+++
date = ""
draft = true
title = "API Post and OPTIONS"

+++
I've been having trouble with using axios to call a POST request. I was trying to pass the data via the body. Axios tries to pass these datas as OPTIONS but the API doesn't accept OPTIONS. To fix this, we can use qs, or query string

    npm i qs

Then import it in react app

    import qs from 'querystring'

In axios, when passing the body, use `qs.stringify()`

    const url = 'https://www.virustotal.com/vtapi/v2/file/scan'
        const config = {
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
          },
          params: {
            apikey: process.env.REACT_APP_API_KEY
          }
        }
        const body = {
          file: file
        }
        const res = await axios.post(url, qs.stringify(body), config)

Now the body will be passed as a string rather than an object OPTIONS