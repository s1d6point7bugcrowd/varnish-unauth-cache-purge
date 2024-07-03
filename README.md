# Varnish Unauthenticated Cache Purge Vulnerability Check

## Description

This .yaml checks if a Varnish Cache server is vulnerable to unauthenticated cache purge attacks. Varnish Cache is a web application accelerator that caches HTTP requests to improve performance. If the PURGE method is not properly authenticated, it can allow attackers to clear the cache without any authentication, leading to potential performance degradation and information disclosure risks.

## Vulnerability Details

- **ID**: varnish-unauth-cache-purge
- **Name**: Varnish Unauthenticated Cache Purge
- **Severity**: High
- **Description**: Checks if it is possible to purge Varnish cache without authentication.


Key Components:

    Request Method: PURGE - This is the HTTP method used to purge the cache.
    Path: {{BaseURL}} - The target URL where the cache purge request is sent.
    Headers:
        Accept: / - Accepts any type of content.
        Accept-Language: en - Specifies the preferred language as English.
        User-Agent - Simulates a request from a specific browser.

Matchers:

    Condition: and - All matchers must be satisfied.
    Matchers:
        Word Matcher: Checks if the response body contains "status": "ok".
        Regex Matcher: Verifies if the response body contains an ID in the format of a UUID.
        Status Matcher: Ensures the HTTP status code is 200
