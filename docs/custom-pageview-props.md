---
title: Tracking custom pageview properties
---

import useBaseUrl from '@docusaurus/useBaseUrl';

With Plausible, you can track pageviews with custom properties. If you're familiar with Google Analytics, custom properties are basically like custom dimensions in GA. For example, say you want to track your blog posts by `author` - every time a visitor lands on one of your blog posts, a pageview will be sent with property `author=...`, and you can later filter by a specific author to quickly see all their blog posts.

In order to use the feature you have to start sending custom properties from your website. The easiest option to get started is to use the `script.pageview-props.js` script extension. 

## 1. Change the Plausible snippet on your site

Please change the file name in the `src` attribute of your Plausible snippet from `script.js` to `script.pageview-props.js`. It should look like this:

```html
<script defer data-domain="<yourdomain.com>" src="https://plausible.io/js/script.pageview-props.js"></script>
```

Or if you're using [a proxy](/proxy/introduction.md):

```html
<script defer data-domain="<yourdomain.com>" src="https://yourproxy.com/script.pageview-props.js"></script>
```

:::note
If you're using any of our other script extensions, you can [combine them](script-extensions.md#you-can-combine-extensions-according-to-your-needs) by changing the `src` attribute in the snippet. If you want to track pageview props and outbound link clicks simultaneously, change the script name to `script.pageview-props.outbound-links.hash.js`.
:::

## 2. Add your custom properties to your Plausible snippet

You should now add the custom properties as HTML attributes to your Plausible snippet (the `<script>` element). The attributes must follow the format `event-<property>="<value>"`. For example, if you want to track the `author` property with a value of `John Doe`, you should do that as follows:

```html
<script defer event-author="John Doe" data-domain="<yourdomain.com>" src="https://plausible.io/script.pageview-props.js"></script>
```

That's it - you're now tracking custom pageview properties!

## 3. Filtering by custom properties

As soon as you have at least one pageview sent with a custom property, you should be able to see an option to filter by that property in your dashboard. To do that, open up the filter dropdown menu and select "Property".

<img alt="Custom Property Filter" src={useBaseUrl('img/custom-property-filter.png')} />

In that view you can interact with the dropdown fields, where Plausible will automatically provide filtering suggestions based on the data that your dashboard has received. The suggestions also take into account the selected time period and other filters already applied.

:::note
Currently clients are limited to filtering by just one custom property at a time.
:::