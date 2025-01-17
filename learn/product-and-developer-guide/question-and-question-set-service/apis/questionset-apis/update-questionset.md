---
description: >-
  This API is used to update an existing question set on the Sunbird-inQuiry
  Platform.
---

# Update QuestionSet

{% swagger method="patch" path="/questionset/v1/update" baseUrl="" summary="This API is used to update an existing question set on the Sunbird-inQuiry Platform." expanded="true" %}
{% swagger-description %}
• 

<mark style="color:orange;">

/Update/

</mark>

 endpoint executes the "Update QuestionSet" request based on parameters provided as metadata in the request body.

\


• It points to inquiry-api-service (assessment service) - 

<mark style="color:orange;">

/questionset/v4/update

</mark>

\


<mark style="color:orange;">



</mark>

• It is mandatory to provide values for parameters marked with 

<mark style="color:red;">

\*

</mark>

. 

\


• Mandatory fields cannot be null or empty.
{% endswagger-description %}

{% swagger-parameter in="path" name="QuestionSet_Id" type="String" required="true" %}
Append a valid QuestionSet ID to the requested URL
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
The Content-Type entity is the media type of the resource. Possible media types can be:-

<mark style="color:green;">

Application/json

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
All question APIs require authorization for use. Specify the authorization key received from the administrator when placing the request for use of the API.

\


Set 

<mark style="color:green;">

Bearer {{api_key}}

</mark>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="request" type="Object" required="true" %}
It contains metadata about the questionset to be updated.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-channel-id" type="String" %}
Unique identification number associated with a root organization.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The Update Question Set operation was successfuly executed." %}
```javascript
{
  "id": "api.questionset.update",
  "ver": "3.0",
  "ts": "2021-02-02T19:55:07ZZ",
  "params": {
    "resmsgid": "9d9d4824-cc40-4ac7-a3d6-6da61c0240e9",
    "msgid": null,
    "err": null,
    "status": "successful",
    "errmsg": null
  },
  "responseCode": "OK",
  "result": {
    "identifier": "do_113207924037746688110",
    "versionKey": "1612295707004"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The 'Update QuestionSet' operation failed ! The possible reason for failure is that you may have missed providing input for a mandatory parameter." %}
```javascript
{
  "id": "api.questionset.update",
  "ver": "3.0",
  "ts": "2021-02-02T19:56:20ZZ",
  "params": {
    "resmsgid": "fcfcf6d6-84f1-43f5-b573-c3b6cf69ef53",
    "msgid": null,
    "err": "CLIENT_ERROR",
    "status": "failed",
    "errmsg": "Invalid version Key"
  },
  "responseCode": "CLIENT_ERROR",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The Update Question Set operation failed !The possible reason for failure is that you may have provided wrong question ID." %}
```javascript
{
  "id": "api.questionset.update",
  "ver": "3.0",
  "ts": "2021-02-02T19:57:35ZZ",
  "params": {
    "resmsgid": "2b139ee9-f091-4cca-b466-32af45f49a65",
    "msgid": null,
    "err": "NOT_FOUND",
    "status": "failed",
    "errmsg": "Error! Node(s) does not exist. | [Invalid Node Id.]: do_1132079240377466881101"
  },
  "responseCode": "RESOURCE_NOT_FOUND",
  "result": {
    "messages": null
  }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Looks like something went wrong! These errors are tracked automatically" %}
```javascript
{
  "result": {},
  "id": "string",
  "ver": "string",
  "ts": "string",
  "params": {
    "resmsgid": "string",
    "msgid": "string",
    "err": "string",
    "status": "string",
    "errmsg": "string"
  },
  "responseCode": "string"
}
```
{% endswagger-response %}
{% endswagger %}

#### Sample Request

```json
{
  "request": {
    "questionset": {
      "description": "Updated description",
      "versionKey": "1612295414767"
    }
  }
}
```

#### Request schema

| Attribute   | Type   | Description                                                      | Required |
| ----------- | ------ | ---------------------------------------------------------------- | -------- |
| versionKey  | String | Represents the transaction update version key of the Questionset | Yes      |
| description | String | Represents the description of the Questionset                    | No       |

#### Success result schema

| Attribute  | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| identidier | String | Unique Question identifier      |
| versionKey | String | Unique version key for question |

####

#### cURL

```shell
curl --location -g --request PATCH '{{host}}/questionset/v1/update/{{questionSet_id}}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{api_key}}' \
--data-raw '{
  "request": {
      "questionset":{
        "versionKey": {{versionKey}},
        "description": "Updated description"
      }
  }
}'
```

