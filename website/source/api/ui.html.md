---
layout: api
page_title: UI
sidebar_current: ui
description: |-
  The /ui namespace is used to access the Nomad web user interface.
---

# Nomad Web UI

Starting in v0.7, the Nomad UI is accessible at `/ui`. It is not namespaced by version. A request to `/`
will also redirect to `/ui`.


## List Jobs

This page lists all known jobs in a paginated, searchable, and sortable table.

| Path       | Produces    |
| ---------- | ----------- |
| `/ui/jobs` | `text/html` |

### Parameters

- `namespace` `(string: "")` - Specifies the namespace all jobs should be a member
  of. This is specified as a querystring parameter. Namespaces are an enterprise feature.

- `sort` `(string: "")` - Specifies the property the list of jobs should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `search` `(string: "")` - Specifies a regular expression uses to filter the list of
  visible jobs. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the jobs list that should be visible. This
  is specified as a querystring parameter.


## Job Detail

This page shows an overview of a specific job. Details include name, status, type,
priority, allocation statuses, and task groups. Additionally, if there is a running
deployment for the job, it will be shown on the overview.

| Path               | Produces    |
| ------------------ | ----------- |
| `/ui/jobs/:job_id` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of task groups should be
  sorted by. This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the task groups list that should be visible. This
  is specified as a querystring parameter.


### Job Definition

This page shows the definition of a job as pretty-printed, syntax-highlighted, JSON.

| Path                          | Produces    |
| ----------------------------- | ----------- |
| `/ui/jobs/:job_id/definition` | `text/html` |


### Job Versions

This page lists all available versions for a job in a timeline view. Each version in
the timeline can be expanded to show a pretty-printed, syntax-highlighted diff between
job versions.

| Path                          | Produces    |
| ----------------------------- | ----------- |
| `/ui/jobs/:job_id/versions`   | `text/html` |


### Job Deployments

This page lists all available deployments for a job when the job has deployments. The
deployments are listed in a timeline view. Each deployment shows pertinent information
such as deployment ID, status, associated version, and submit time. Each deployment can
also be expanded to show detail information regarding canary placements, allocation
placements, healthy and unhealthy allocations, as well the current description for the
status. A table of task groups is also present in the detail view, which shows allocation
metrics by task group. Lastly, each expanded deployment lists all associated allocations
in a table to drill into for task events.

| Path                             | Produces    |
| -------------------------------- | ----------- |
| `/ui/jobs/:job_id/deployments`   | `text/html` |


## Task Group Detail

This page shows an overview of a specific task group. Details include the number of tasks, the aggregated amount of reserved CPU, memory, and disk, all associated allocations broken
down by status, and a list of allocations. The list of allocations include details such as
status, the node the allocation was placed on, and the current CPU and Memory usage of the
allocations.

| Path                                | Produces    |
| ----------------------------------- | ----------- |
| `/ui/jobs/:job_id/:task_group_name` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of allocations should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `search` `(string: "")` - Specifies a regular expression uses to filter the list of
  visible allocations. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the allocations list that should be visible. This
  is specified as a querystring parameter.


## Allocation Detail

This page shows details and events for an allocation. Details include the job the allocation
belongs to, the node the allocation is placed on, a list of all tasks, and lists of task
events per task. Each task in the task list includes the task name, state, last event, time,
and addresses. Each task event in a task history list includes the time, type, and
description of the event.

| Path                        | Produces    |
| --------------------------- | ----------- |
| `/ui/allocations/:alloc_id` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of tasks should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.


## Nodes List

This page lists all nodes in the Nomad cluster in a sortable, searchable, paginated
table.

| Path        | Produces    |
| ----------- | ----------- |
| `/ui/nodes` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of client nodes should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `search` `(string: "")` - Specifies a regular expression uses to filter the list of
  visible client nodes. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the client nodes list that should be visible. This
  is specified as a querystring parameter.


## Node Detail

This page shows the details of a node, including the node name, status, full ID,
address, port, datacenter, allocations, and attributes.

| Path                 | Produces    |
| -------------------- | ----------- |
| `/ui/nodes/:node_id` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of allocations should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `search` `(string: "")` - Specifies a regular expression uses to filter the list of
  visible allocations. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the allocations list that should be visible. This
  is specified as a querystring parameter.


## Servers List

This page lists all servers in the Nomad cluster in a sortable table. Details for each
server include the server status, address, port, datacenter, and whether or not it is
the leader.

| Path          | Produces    |
| ------------- | ----------- |
| `/ui/servers` | `text/html` |

### Parameters

- `sort` `(string: "")` - Specifies the property the list of server agents should be sorted by.
  This is specified as a querystring parameter.

- `desc` `(boolean: false)` - Specifies whether or not the sort direction is descending
  or ascending. This is specified as a querystring parameter.

- `page` `(int: 0)` - Specifies the page in the server agents list that should be visible. This
  is specified as a querystring parameter.


## Server Detail

This page lists all tags associated with a server.

| Path                     | Produces    |
| ------------------------ | ----------- |
| `/ui/servers/:server_id` | `text/html` |


## ACL Tokens

This page lets you enter an ACL token (both accessor ID and secret ID) to use with the UI.
If the cluster does not have ACLs enabled, this page is unnecessary. If the cluster has an
anonymous policy that grants cluster-wide read access, this page is unnecessary. If the
anonymous policy only grants partial read access, then providing an ACL Token will
authenticate all future requests to allow read access to additional resources.

| Path                  | Produces    |
| --------------------- | ----------- |
| `/ui/settings/tokens` | `text/html` |
