# Google Tag Manager Tracking for SearchStax Studio

Google Tag Manager can be used to capture keyword search trends and click through data from your SearchStax Studio search result page. This repo contains the Google Tag Manager configuration file. [Read More](https://www.searchstax.com/blog/how-to-set-up-google-analytics-4-with-searchstax-studio/) about setting up and configuring Google Analytics 4 and Google Tag Manager.

# Setting Up a SearchStax Studio App

[SearchStax Studio](https://www.searchstax.com/searchstudio/) is a quick and easy way to add site search to your website. SearchStax Studio features a prebuilt search result page that you can add to any website as well as in-depth search analytics including keyword search trends, click through data, latency, and more.

[SearchStax Studio Analytics](https://www.searchstax.com/search-analytics/) can be paired with Google Analytics 4 to provide complete visibility on how your site visitors search and interact with content on your website.

# Configuring Google Analytics 4 (GA4)

If you haven't already - create a new Google Analytics 4 property for your website. You'll need to get the measurement ID from the Data Streams panel in the Admin section so you can add it to Google Tag Manager.

Once your GA4 account is set up you'll need to define some custom dimensions and events to track SearchStax Studio engagement.

## Google Analytics 4 Custom Dimensions

1. Add `searchstax_query` dimension for SearchStax Studio site queries
2. Add `searchstax_destination_page` dimension to capture click through data
3. Add `searchstax_facets` dimension to capture facet selections
4. Add `searchstax_order` dimension to capture search result sorting

## Google Analytics 4 Custom Events

You'll also need to create some custom events to track searches and clicks from search results.

1. Add `searchstax_search` event that includes `searchstax_query` and `searchstax_destination_page` parameters
2. Add `searchstax_click` event that includes `searchstax_query`, `searchstax_page`, `searchstax_facet`, `searchstax_sort`, and `page_location` parameters

# Configuring Google Tag Manager (GTM)

If you haven't already - create a new Google Tag Manager container and add it to your website.

Once GTM is live on your site you can import the SearchStax Studio config file. This contains the variables, triggers, and tags that will send site search analytics data to GA4.

## Import Configuration

1. Download the `GTM-SearchStax-Studio-Tracking.json` configuration file
2. In the Admin section select 'Import Container' and select the configuration file
3. If you already have a workspace you can add the SearchStax Studio config or create a new workspace with just the SearchStax Studio config
4. Overwrite or merge changes with your existing tags
5. Confirm and import

## Update Google Analytics 4 IDs

The SearchStax Studio config file includes a basic Google Analytics 4 configuration tag with a blank measurement ID - you can either update the measurement ID or use another Google Analytics 4 configuration tag. If you've already set up another configuration tag you'll need to update the `SearchStax Result Click` and `SearchStax Search Update` tags to use that configuration tag.

## Testing

Once you've got Google Tag Manager configured you can preview your configuration on your live site to ensure dimensions and events are properly tracked and sent to Google Analytics 4.

1. In your Google Tag Manager workspace click 'Preview'
2. Enter the URL for your website's search page (this page must contain the GTM container code)
3. Search and click on a search result
4. Verify events and dimensions are properly sent in the Tag Assistant window

If everything looks good you can submit your Google Tag Manager changes to start capturing reporting data. You can see recent events in Google Analytics 4 Realtime Reports. After 24 hours your new events and dimensions will be available in Google Analytics 4 Explore reporting and Looker Studio.