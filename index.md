---
title: What's this?
nav_order: 0

---

# What's this?

A summary on HTTP statuses.

{: .notice }
> 🚧 Under construction
>
> Currently, the content is being categorized over based on [a section on HTTP statuses in RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html#section-15). Eventually, we aim to put the important summary on top of every section which are practical for most developers.
>
> If you would like to contribute, [please start with an issue discussing your proposal before sending pull requests](https://github.com/wilsonehusin/httpstatus-dev/issues).

# What's HTTP status?

The status code of a response is a three-digit integer code that describes the result of the request and the semantics of the response, including whether the request was successful and what content is enclosed (if any). All valid status codes are within the range of 100 to 599, inclusive.

The first digit of the status code defines the class of response. The last two digits do not have any categorization role. There are five values for the first digit:

- [1xx (Informational)](/1xx): The request was received, continuing process
- [2xx (Successful)](/2xx): The request was successfully received, understood, and accepted
- [3xx (Redirection)](/3xx): Further action needs to be taken in order to complete the request
- [4xx (Client Error)](/4xx): The request contains bad syntax or cannot be fulfilled
- [5xx (Server Error)](/5xx): The server failed to fulfill an apparently valid request

HTTP status codes are extensible. A client is not required to understand the meaning of all registered status codes, though such understanding is obviously desirable. However, a client MUST understand the class of any status code, as indicated by the first digit, and treat an unrecognized status code as being equivalent to the x00 status code of that class.

For example, if a client receives an unrecognized status code of 471, it can see from the first digit that there was something wrong with its request and treat the response as if it had received a [400 (Bad Request)](/400) status code. The response message will usually contain a representation that explains the status.

Values outside the range 100..599 are invalid. Implementations often use three-digit integer values outside of that range (i.e., 600..999) for internal communication of non-HTTP status (e.g., library errors). A client that receives a response with an invalid status code SHOULD process the response as if it had a [5xx (Server Error)](/5xx) status code.

A single request can have multiple associated responses: zero or more "interim" (non-final) responses with status codes in the "informational" ([1xx](/1xx)) range, followed by exactly one "final" response with a status code in one of the other ranges.
