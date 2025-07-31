# rzap-ng

This library provides an interface to control shocker devices via [OpenShock](http://openshock.org)'s API

> [!NOTE]
> This is an un-official API interface, and a (hopefully temporary) fork of
> [`LostQuasar/rzap`].

[`LostQuasar/rzap`]: https://github.com/LostQuasar/rzap

## Example

A simple request to retrieve the API key user's id

```rs
    dotenv().ok();
    let openshock_token = dotenv::var("OPENSHOCK_TOKEN").expect("missing OPENSHOCK_TOKEN");
    let app_name = env!("CARGO_PKG_NAME");
    let app_version = env!("CARGO_PKG_VERSION");

    assert_ne!(openshock_token, "");

    openshock_api = OpenShockAPIBuilder::new()
        .with_app(app_name.to_string(), Some(app_version.to_string()))
        .with_default_api_token(openshock_token)
        .build()
        .unwrap();

    println!(openshock_api.get_user_info(None).await.unwrap().id);
```

