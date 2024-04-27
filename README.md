[//]: # ( )
[//]: # (This file is automatically generated by a `metapak`)
[//]: # (module. Do not change it  except between the)
[//]: # (`content:start/end` flags, your changes would)
[//]: # (be overridden.)
[//]: # ( )
# @zibuthe7j11/maxime-incidunt-quos
> Out of the box application environment and configuration service.

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/zibuthe7j11/maxime-incidunt-quos/blob/main/LICENSE)
[![Coverage Status](https://coveralls.io/repos/github/nfroidure/@zibuthe7j11/maxime-incidunt-quos/badge.svg?branch=main)](https://coveralls.io/github/nfroidure/@zibuthe7j11/maxime-incidunt-quos?branch=main)


[//]: # (::contents:start)

Need to manage several environment and configurations for your
[`knifecycle`](https://github.com/nfroidure/knifecycle) based app? This module
is all what your need.

## Features

Out of the box, standard compliant, application environment:

- accepting only
  [standard](https://koistya.medium.com/demystifying-node-env-var-b25ed43c9af)
  `NODE_ENV` values: `test`, `development`, `production`,
- managing application environment in a clean and separate `APP_ENV` environment
  variable,
- leverage `dotenv` to read environment variables,
- manage separate and type checked applications configurations for each
  deployment environments and allows loading it automatically (in the
  `./configs/${APP_ENV}/index` file).

It requires `log` and `importer` services to be passed in, you can find
implementations in the
[`common-services`](https://github.com/nfroidure/common-services) project.

It also relies on constant services you will have to provide: `APP_ENV`,
`NODE_ENV` and the `MAIN_FILE_URL` (directory where actual code is).

[//]: # (::contents:end)

# API
## Constants

<dl>
<dt><a href="#PROCESS_ENV
Provides the PROCESS_ENV service">PROCESS_ENV
Provides the PROCESS_ENV service</a> : <code>Object</code></dt>
<dd></dd>
</dl>

## Functions

<dl>
<dt><a href="#extractAppEnv">extractAppEnv(appEnv, availableAppEnvs)</a> ⇒</dt>
<dd><p>Cast any string into an application environment</p>
</dd>
<dt><a href="#initAppConfig">initAppConfig(services)</a> ⇒ <code>Promise.&lt;Object&gt;</code></dt>
<dd><p>Initialize the APP_CONFIG service according to the APP_ENV</p>
</dd>
<dt><a href="#initENV">initENV(services)</a> ⇒ <code>Promise.&lt;Object&gt;</code></dt>
<dd><p>Initialize the ENV service using process env plus dotenv files
 loaded in <code>.env.node.${ENV.NODE_ENV}</code> and <code>.env.app.${APP_ENV}</code>.</p>
</dd>
<dt><a href="#initProcess">initProcess(services)</a> ⇒ <code>Promise.&lt;Object&gt;</code></dt>
<dd><p>Instantiate the process service</p>
</dd>
<dt><a href="#initProjectDirectory">initProjectDirectory(services)</a> ⇒ <code>Promise.&lt;Object&gt;</code></dt>
<dd><p>Initialize the PROJECT_DIR service</p>
</dd>
</dl>

<a name="PROCESS_ENV
Provides the PROCESS_ENV service"></a>

## PROCESS\_ENV
Provides the PROCESS\_ENV service : <code>Object</code>
**Kind**: global constant  
<a name="extractAppEnv"></a>

## extractAppEnv(appEnv, availableAppEnvs) ⇒
Cast any string into an application environment

**Kind**: global function  
**Returns**: string  

| Param | Description |
| --- | --- |
| appEnv | string |
| availableAppEnvs | string[] |

<a name="initAppConfig"></a>

## initAppConfig(services) ⇒ <code>Promise.&lt;Object&gt;</code>
Initialize the APP_CONFIG service according to the APP_ENV

**Kind**: global function  
**Returns**: <code>Promise.&lt;Object&gt;</code> - A promise of a an object the actual configuration properties.  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| services | <code>Object</code> |  | The services `APP_CONFIG` depends on |
| services.APP_ENV | <code>Object</code> |  | The injected `APP_ENV` value |
| services.MAIN_FILE_URL | <code>String</code> |  | An URL pointing to the main file run |
| services.importer | <code>Object</code> |  | A service allowing to dynamically import ES modules |
| [services.log] | <code>Object</code> | <code>noop</code> | An optional logging service |

<a name="initENV"></a>

## initENV(services) ⇒ <code>Promise.&lt;Object&gt;</code>
Initialize the ENV service using process env plus dotenv files
 loaded in `.env.node.${ENV.NODE_ENV}` and `.env.app.${APP_ENV}`.

**Kind**: global function  
**Returns**: <code>Promise.&lt;Object&gt;</code> - A promise of an object containing the actual env vars.  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| services | <code>Object</code> |  | The services `ENV` depends on |
| [services.BASE_ENV] | <code>Object</code> |  | Base env vars that will be added to the environment |
| services.APP_ENV | <code>Object</code> |  | The injected `APP_ENV` value |
| services.PROCESS_ENV | <code>Object</code> |  | The injected `process.env` value |
| services.PROJECT_DIR | <code>Object</code> |  | The NodeJS project directory |
| [services.log] | <code>Object</code> | <code>noop</code> | An optional logging service |

<a name="initProcess"></a>

## initProcess(services) ⇒ <code>Promise.&lt;Object&gt;</code>
Instantiate the process service

**Kind**: global function  
**Returns**: <code>Promise.&lt;Object&gt;</code> - A promise of the process object  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| services | <code>Object</code> |  | The services `process` depends on |
| services.APP_ENV | <code>Object</code> |  | The injected `APP_ENV` value |
| [services.PROCESS_NAME] | <code>Object</code> |  | The process name to display |
| [services.SIGNALS] | <code>Object</code> |  | The process signals that interrupt the process |
| [services.exit] | <code>Object</code> |  | A `process.exit` like function |
| services.$instance | <code>Object</code> |  | The Knifecycle instance |
| services.$fatalError | <code>Object</code> |  | The Knifecycle fatal error manager |
| [services.log] | <code>Object</code> | <code>noop</code> | An optional logging service |

<a name="initProjectDirectory"></a>

## initProjectDirectory(services) ⇒ <code>Promise.&lt;Object&gt;</code>
Initialize the PROJECT_DIR service

**Kind**: global function  
**Returns**: <code>Promise.&lt;Object&gt;</code> - A promise of a an object the actual configuration properties.  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| services | <code>Object</code> |  | The services PROJECT_DIR depends on |
| [services.log] | <code>Object</code> | <code>noop</code> | An optional logging service |


# Authors
- [Nicolas Froidure](http://insertafter.com/en/index.html)

# License
[MIT](https://github.com/zibuthe7j11/maxime-incidunt-quos/blob/main/LICENSE)
