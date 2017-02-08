# ezgist

## Github API OAuth flow(Temp note):

#### 1. GET https://github.com/login/oauth/authorize?client_id=18a799f4b218bafe39de&redirect_uri=https%3A%2F%2Fwonderbeyond.github.io%2Fezgist%2F%23%2Foauth-callback&scope=user+gist

#### 2. GitHub redirects back to: https://wonderbeyond.github.io/ezgist/?code=<code>#/oauth-callback

#### 3. Exchange code for an access token(via XMLHttpRequest):

Take jQuery.ajax for example:

```
$.ajax({
    url: 'https://github.com/login/oauth/access_token?client_id=18a799f4b218bafe39de&client_secret=7d6a559a42641169b81f9fd3221710e3db312802&code=d724fc5fccff76cb1032',
    type: 'POST',
    dataType: 'json',
})
.done(function() {
    console.log("success");
})
.fail(function() {
    console.log("error");
})
.always(function() {
    console.log("complete");
});

```

Got: cc423681a042ca502fde37da44f49835b20c6543

#### 4. get resource

```
http get 'https://api.github.com/gists/starred' 'Authorization:token cc423681a042ca502fde37da44f49835b20c6543'
```
