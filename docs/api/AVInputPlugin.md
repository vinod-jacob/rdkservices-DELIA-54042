<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.AVInput_Plugin"></a>
# AVInput Plugin

**Version: 1.0**

**Status: :black_circle::black_circle::black_circle:**

A org.rdk.AVInput plugin for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Description](#head.Description)
- [Configuration](#head.Configuration)
- [Methods](#head.Methods)
- [Notifications](#head.Notifications)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the org.rdk.AVInput plugin. It includes detailed specification about its configuration, methods provided and notifications sent.

<a name="head.Case_Sensitivity"></a>
## Case Sensitivity

All identifiers of the interfaces described in this document are case-sensitive. Thus, unless stated otherwise, all keywords, entities, properties, relations and actions should be treated as such.

<a name="head.Acronyms,_Abbreviations_and_Terms"></a>
## Acronyms, Abbreviations and Terms

The table below provides and overview of acronyms used in this document and their definitions.

| Acronym | Description |
| :-------- | :-------- |
| <a name="acronym.API">API</a> | Application Programming Interface |
| <a name="acronym.HTTP">HTTP</a> | Hypertext Transfer Protocol |
| <a name="acronym.JSON">JSON</a> | JavaScript Object Notation; a data interchange format |
| <a name="acronym.JSON-RPC">JSON-RPC</a> | A remote procedure call protocol encoded in JSON |

The table below provides and overview of terms and abbreviations used in this document and their definitions.

| Term | Description |
| :-------- | :-------- |
| <a name="term.callsign">callsign</a> | The name given to an instance of a plugin. One plugin can be instantiated multiple times, but each instance the instance name, callsign, must be unique. |

<a name="head.References"></a>
## References

| Ref ID | Description |
| :-------- | :-------- |
| <a name="ref.HTTP">[HTTP](http://www.w3.org/Protocols)</a> | HTTP specification |
| <a name="ref.JSON-RPC">[JSON-RPC](https://www.jsonrpc.org/specification)</a> | JSON-RPC 2.0 specification |
| <a name="ref.JSON">[JSON](http://www.json.org/)</a> | JSON specification |
| <a name="ref.Thunder">[Thunder](https://github.com/WebPlatformForEmbedded/Thunder/blob/master/doc/WPE%20-%20API%20-%20WPEFramework.docx)</a> | Thunder API Reference |

<a name="head.Description"></a>
# Description

The `AVInput` plugin facilitates interactions with the Parker STB HDMI input. The HDMI input is presented by using a `VideoResource` whose URL starts with `avin:`. For example: `avin://input1`.

The plugin is designed to be loaded and executed within the Thunder framework. For more information about the framework refer to [[Thunder](#ref.Thunder)].

<a name="head.Configuration"></a>
# Configuration

The table below lists configuration options of the plugin.

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| callsign | string | Plugin instance name (default: *org.rdk.AVInput*) |
| classname | string | Class name: *org.rdk.AVInput* |
| locator | string | Library name: *libWPEFrameworkAVInput.so* |
| autostart | boolean | Determines if the plugin shall be started automatically along with the framework |

<a name="head.Methods"></a>
# Methods

The following methods are provided by the org.rdk.AVInput plugin:

AVInput interface methods:

| Method | Description |
| :-------- | :-------- |
| [contentProtected](#method.contentProtected) | Returns `true` if the content coming in the HDMI input is protected; otherwise, it returns `false` |
| [currentVideoMode](#method.currentVideoMode) | Returns a string encoding the video mode being supplied by the device currently attached to the HDMI input |
| [numberOfInputs](#method.numberOfInputs) | Returns an integer that specifies the number of available inputs |


<a name="method.contentProtected"></a>
## *contentProtected [<sup>method</sup>](#head.Methods)*

Returns `true` if the content coming in the HDMI input is protected; otherwise, it returns `false`. If the content is protected, then it is only presented if the component and composite outputs of the box are disabled.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object | An empty parameter object |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result.isContentProtected | boolean | Whether the HDMI input is protected |
| result.success | boolean | Whether the request succeeded |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "org.rdk.AVInput.1.contentProtected",
    "params": {}
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": {
        "isContentProtected": true,
        "success": true
    }
}
```

<a name="method.currentVideoMode"></a>
## *currentVideoMode [<sup>method</sup>](#head.Methods)*

Returns a string encoding the video mode being supplied by the device currently attached to the HDMI input. The format of the string is the same format used for the `resolutionName` parameter of the XRE `setResolution` messages. HDMI input is presentable if its resolution is less than or equal to the current Parker display resolution. 
 
### Events
 
 No Events.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object | An empty parameter object |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result.currentVideoMode | string | The current video mode |
| result.message | string | `Success` if plugin is activated successfully and gets the current Videomode. `org.rdk.HdmiInput plugin is not ready` if plugin is not activated or activation failed |
| result.success | boolean | Whether the request succeeded |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "org.rdk.AVInput.1.currentVideoMode",
    "params": {}
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": {
        "currentVideoMode": "Unknown",
        "message": "Success",
        "success": true
    }
}
```

<a name="method.numberOfInputs"></a>
## *numberOfInputs [<sup>method</sup>](#head.Methods)*

Returns an integer that specifies the number of available inputs. For example, a value of `2` indicates that there are two available inputs that can be selected using `avin://input0` and `avin://input1`. 
 
### Events
 
 No Events.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object | An empty parameter object |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result.numberOfInputs | number | The number of inputs that are available for selection |
| result.message | string | `Success` if plugin is activated successfully and gets the current Videomode. `org.rdk.HdmiInput plugin is not ready` if plugin is not activated or activation failed |
| result.success | boolean | Whether the request succeeded |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "org.rdk.AVInput.1.numberOfInputs",
    "params": {}
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": {
        "numberOfInputs": 1,
        "message": "Success",
        "success": true
    }
}
```

<a name="head.Notifications"></a>
# Notifications

Notifications are autonomous events, triggered by the internals of the implementation, and broadcasted via JSON-RPC to all registered observers. Refer to [[Thunder](#ref.Thunder)] for information on how to register for a notification.

The following events are provided by the org.rdk.AVInput plugin:

AVInput interface events:

| Event | Description |
| :-------- | :-------- |
| [onAVInputActive](#event.onAVInputActive) | Triggered when an active device is connected to an AVInput port |
| [onAVInputInActive](#event.onAVInputInActive) | Triggered when an active device is disconnected from an AVInput port or when the device becomes inactive |


<a name="event.onAVInputActive"></a>
## *onAVInputActive [<sup>event</sup>](#head.Notifications)*

Triggered when an active device is connected to an AVInput port.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.url | string | The URL of the port with an active device |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onAVInputActive",
    "params": {
        "url": "avin://input0"
    }
}
```

<a name="event.onAVInputInActive"></a>
## *onAVInputInActive [<sup>event</sup>](#head.Notifications)*

Triggered when an active device is disconnected from an AVInput port or when the device becomes inactive.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.url | string | The URL of the port with an inactive device |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onAVInputInActive",
    "params": {
        "url": "avin://input0"
    }
}
```

