---
title: Log Explorer
kind: documentation
description: 'Search through all of your logs and perform Log Analytics'
aliases:
    - /logs/explore
further_reading:
    - link: 'logs/explorer/analytics'
      tag: 'Documentation'
      text: 'Perform Log Analytics'
    - link: 'logs/processing'
      tag: 'Documentation'
      text: 'Learn how to process your logs'
    - link: 'logs/explorer/saved_views'
      tag: Documentation
      text: 'Automatically configure your Log Explorer'
    - link: 'logs/explorer/patterns'
      tag: Documentation
      text: 'Detect patterns inside your logs'
---

## Overview

The Logs Explorer is your home base for troubleshooting and exploration:

{{< img src="logs/explorer/log_explorer_walkthrough.gif" alt="Explore view with comments" style="width:80%;" >}}

Different views offer different types of insights from your log data, matching a [search query][1].

### Live Tail

The Live Tail displays logs as they flow into Datadog. Live Tail logs do not persist, but the view provides visibility on **all** logs, whether they are indexed or not. Find out more in the [Log Live Tail section][2].

{{< img src="logs/explorer/log_explorer_walkthrough_livetail.gif" alt="Log Livetail" style="width:60%;" >}}

### Log Lists

The Log List displays indexed logs and offers privileged tools to navigate **individual results**. Find out more in the [Log List section][3].

{{< img src="logs/explorer/log_explorer_walkthrough_list.png" alt="Log List" style="width:60%;" >}}

### Log Patterns

The Log Patterns automatically aggregate indexed logs into a **handful of groups** with similar structures. Find out more in the [Log Patterns section][4].

{{< img src="logs/explorer/log_explorer_walkthrough_patterns.png" alt="Log Patterns" style="width:60%;" >}}

### Log Analytics

The Log Analytics **graph** log queries and see maximums, averages, percentiles, unique counts, and more. Follow the [log graphing guide][5] to learn more about all the graphing options.

{{< img src="logs/explorer/log_explorer_walkthrough_analytics.png" alt="Log Analytics" style="width:60%;" >}}

## The Log Side Panel

Datadog displays individual logs following this general side-panel layout:

{{< img src="logs/explorer/log_side_panel.png" alt="Log Side Panel"  style="width:60%;">}}

### Log structured information

- The upper part of the panel displays general **context** information.
- The lower part of the panel displays the actual **content** of the log.

**Context** refers to the infrastructure and application context in which the log has been generated. Information is gathered from tags—whether automatically attached (host name, container name, log file name, serverless function name, etc.)—or added through custom tags (team in charge, environment, application version, etc.) on the log by the Datadog Agent or Log Forwarder.

**Content** refers to the log itself. This includes the log message, as well as all structured information extracted and enriched from the logs through [Log Pipelines][6]. For logs generated by common components of a technical stack, parsing and enriching comes out-of-the-box:

- For file log collection, make sure you properly set up the source field, which triggers file log collection. See Datadog's [100+ Log Integrations][7] for reference.
- For container log collection, use [Autodiscovery][8].

Some standard fields—for instance, `error.stack`, `http.method`, or `duration`—have specific enhanced displays in the Log Panel for better readability. Make sure you extract corresponding information from your logs and remap your attributes with [standard attribute remappers][9].

### A hub to other data sources

Interact with the upper reserved attributes section:

- with the **Host** section, to access the related [host dashboard][10] or [network page][11].
- with the **Service** section, to see the [trace in APM][12] (both require a `trace_id` attribute in the log: refer to [trace injection in logs][13]) or the [service page][14].
- Enhance your experience further with [Unified Service Tagging][15] to navigate to and from logs with `env`, `service`, and `version`.

The **View in context** button updates the search request in order to show you the log lines dated just before and after a selected log—even if they don't match your filter. This context is different according to the situation, as Datadog uses the `Hostname`, `Service`, `filename`, and `container_id` attributes, along with tags, in order find the appropriate context for your logs.

{{< img src="logs/explorer/side_panel_hub.gif" alt="Side Panel Hub" style="width:60%;">}}

### Configure your troubleshooting context

Interact with the attributes names and values in the lower JSON section to:

- Add or remove a column from the logs table.
- Append the search request with specific values (include or exclude)

{{< img src="logs/explorer/side_panel_context.gif" alt="Side Panel context"  style="width:60%;">}}

- Build or edit a facet or measure from an attribute. See [Log Facets][16].

{{< img src="logs/explorer/side_panel_facets.gif" alt="Side Panel Facets"  style="width:60%;">}}

### Share a log

Use the **Share** button to share the log opened in side panel to other contexts.

- **Copy to clipboard** or `Ctrl+C` / `Cmd+C` copies the log JSON to your clipboard.
- **Share Event** shares the log (along with the underlying view) with teammates through email, Slack, and more. See all [Datadog notification integrations][17] available.

{{< img src="logs/explorer/upper_log_panel.png" alt="Upper Log Panel"  style="width:50%;">}}

## Troubleshooting Context

### Search Filter

Build up a context to explore your logs in your log explorer view. First, select the proper time range. Then, use the search bar to filter your Logstream and Log Analytics.

**Time Range**

The time range feature allows you to display logs in the Logstream or Log Analytics within a given time period.
It appears directly under the search bar as a timeline. The timeline can be displayed or wrapped up with the **Show timeline** check box in the Logstream option panel.

Quickly change the time range by selecting a preset range from the dropdown:

{{< img src="logs/explorer/timerange.png" style="width:50%;" alt="Timerange"  >}}

**Search**

Use facets, measures, tags, or even [free text search][1] to filter your Logstream and Log Analytics with dedicated context. The search bar and URL automatically reflect your selections.

Follow the [guide to search your logs][1] for a detailed explanation of all the Log Explorer search features, including use of wildcards and queries of numerical values.

### Saved views

Use saved views to automatically configure your log explorer with a preselected set of facets, measures, searches, time ranges, and visualizations. Check the dedicated [saved views documentation][18] to learn more.

## Further Reading

{{< partial name="whats-next/whats-next.html" >}}

[1]: /logs/search-syntax/
[2]: /logs/explorer/live_tail/
[3]: /logs/explorer/list/
[4]: /logs/explorer/patterns/
[5]: /logs/explorer/analytics/
[6]: /logs/processing/pipelines/
[7]: /integrations/#cat-log-collection
[8]: /agent/autodiscovery/integrations/?tab=kubernetes
[9]: /logs/processing/attributes_naming_convention/
[10]: /dashboards/#preset-lists
[11]: /network_performance_monitoring/network_page/
[12]: /tracing/app_analytics/search/#displaying-a-full-trace
[13]: /tracing/connect_logs_and_traces/
[14]: /tracing/visualization/service/#overview
[15]: /getting_started/tagging/unified_service_tagging
[16]: /logs/explorer/facets/#overview
[17]: /logs/processing/
[18]: /logs/explorer/saved_views/
