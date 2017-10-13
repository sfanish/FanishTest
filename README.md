
- [Table of contents](#table-of-contents)
- [Schema for Device Information table](#schema-for-device-information-table)
- [CURL samples](#curl-samples)
	- [UserProfile Create](#userprofile-create)
	- [UserProfile Get](#userprofile-get)
	- [UserProfile PUT](#userprofile-put)
	- [UserProfile Delete](#userprofile-delete)
	- [UserProfile Query](#userprofile-query)
- [Activity Diagrams](#activity-diagrams)
	- [UserProfile Create](#userprofile-create-1)
	- [UserProfile Get](#userprofile-get-1)
	- [UserProfile PUT](#userprofile-put-1)
	- [UserProfile Delete](#userprofile-delete-1)
	- [UserProfile Query](#userprofile-query-1)
- [Code Samples for C Sharp](#code-samples-for-c-sharp)
	- [UserProfile Create](#userprofile-create-2)
	- [UserProfile Get](#userprofile-get-2)
	- [UserProfile PUT](#userprofile-put-2)
	- [UserProfile Delete](#userprofile-delete-2)
	- [UserProfile Query](#userprofile-query-2)
- [Code Samples for Node JS](#code-samples-for-node-js)
	- [UserProfile Create](#userprofile-create-3)
	- [UserProfile Get](#userprofile-get-3)
	- [UserProfile PUT](#userprofile-put-3)
	- [UserProfile Delete](#userprofile-delete-3)
	- [UserProfile Query](#userprofile-query-3)
- [Code Samples for JavaScript](#code-samples-for-javascript)
	- [UserProfile Create](#userprofile-create-4)
	- [UserProfile Get](#userprofile-get-4)
	- [UserProfile PUT](#userprofile-put-4)
	- [UserProfile Delete](#userprofile-delete-4)
	- [UserProfile Query](#userprofile-query-4)

Schema for Device Information table
--------------

|       id       |    {GUID}     |
| :------------: | :-----------: |
|  ActiveDirID   |      111      |
|     CardID     |    AWS123     |
|     Domain     |    domain     |
|     Email      | test@test.com |
| LastDeviceUsed | str(datetime) |
|   LastLogin    | str(datetime) |
|      Name      |     Name      |
|     O365ID     |      xyx      |
|   O365Token    |    abcxyx     |

CURL samples
--------------
UserProfile Create
--------------
```curl
curl -X "POST" "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile?one=1&two=2" \
     -H "x-api-key: XXXXXXXXXXXXXXXXXXXX" \
     -H "Content-Type: application/json" \
     -d $'{
  "CardID": "1239",
  "Domain": "SSDI",
  "O365ID": "kravikiran@onmicrosoft.com",
  "O365Token": "ABCDEFGHh",
  "Name": "Ravikian",
  "Email": "kravikiran@ssdi.sharp.co.in",
  "ActiveDirID": "ssdiblr"
}'

```

UserProfile Get
--------------
```curl
curl "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2" \
     -H "x-api-key: XXXXXXXXXXXXXXXXXXXX" \
     -H "Content-Type: application/json" \
     -d $'{}'
```

UserProfile PUT
--------------
```curl
curl -X "PUT" "https://64bg0rty5h.execute-api.us-east-1.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D" \
     -H "x-api-key: NmvoWKXKzn70sOpQhqRPo58sR9fAedyD5RpjBJeX" \
     -H "Content-Type: application/json" \
     -d $'{
  "O365ID": "Ravi",
  "O365Token": "RaviTokeb"
}'

```
UserProfile Delete
--------------
```curl
curl -X "DELETE" "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2" \
     -H "x-api-key: XXXXXXXXXXXXXXXXXXXX" \
     -H "Content-Type: application/json" \
     -d $'{}'
```
UserProfile Query
--------------
```curl
curl -X "POST" "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/query" \
     -H "x-api-key: XXXXXXXXXXXXXXXXXXXX" \
     -H "Content-Type: application/json" \
     -d $'{
  "id": "CardID",
  "value": "12391"
}'
```
Activity Diagrams
--------------
UserProfile Create
--------------
![UserProfile Create](Image/Register_Device.png)

UserProfile Get
--------------
![UserProfile Get](Image/Get_Device.png)

UserProfile PUT
--------------
![UserProfile PUT](Image/Update_Device.png)

UserProfile Delete
--------------
![UserProfile Delete](Image/Delete_device.png)

UserProfile Query
--------------
![UserProfile Query](Image/Device_Query.png)





Code Samples for C Sharp
--------------
UserProfile Create
--------------
```C#
using System;
using System.Threading.Tasks;
using System.Net;
using System.IO;
using System.Text;

namespace MyNamespace {
	public class MyActivity {
		
		private async Task<bool> UserProfileCreate () {

			string url = "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile?one=1&two=2";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create (new Uri(url));
			request.ContentType = "application/json";
			request.Headers.Add("x-api-key", "XXXXXXXXXXXXXXXXXXXX");
			
			request.Method = "POST";
			
			string postData = "{\"Name\":\"Ravikian\",\"CardID\":\"1239\",\"Domain\":\"SSDI\",\"ActiveDirID\":\"ssdiblr\",\"Email\":\"kravikiran@ssdi.sharp.co.in\",\"O365ID\":\"kravikiran@onmicrosoft.com\",\"O365Token\":\"ABCDEFGHh\"}";
			ASCIIEncoding encoding = new ASCIIEncoding ();
			byte[] byte1 = encoding.GetBytes (postData);
			request.ContentLength = byte1.Length;
			Stream newStream = request.GetRequestStream ();
			newStream.Write (byte1, 0, byte1.Length);
			newStream.Close ();
			
			using (WebResponse response = await request.GetResponseAsync ()) {
				using (Stream stream = response.GetResponseStream ()) {
					return true;
					//process the response
				}
			}
		}
	}
}

```
UserProfile Get
--------------

```C#
using System;
using System.Threading.Tasks;
using System.Net;
using System.IO;
using System.Text;

namespace MyNamespace {
	public class MyActivity {
		
		private async Task<bool> UserProfileGet () {

			string url = "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create (new Uri(url));
			request.ContentType = "application/json";
			request.Headers.Add("x-api-key", "XXXXXXXXXXXXXXXXXXXX");
			
			request.Method = "GET";
			
			string postData = "{}";
			ASCIIEncoding encoding = new ASCIIEncoding ();
			byte[] byte1 = encoding.GetBytes (postData);
			request.ContentLength = byte1.Length;
			Stream newStream = request.GetRequestStream ();
			newStream.Write (byte1, 0, byte1.Length);
			newStream.Close ();
			
			using (WebResponse response = await request.GetResponseAsync ()) {
				using (Stream stream = response.GetResponseStream ()) {
					return true;
					//process the response
				}
			}
		}
	}
}

```
UserProfile PUT
--------------

```C#
using System;
using System.Threading.Tasks;
using System.Net;
using System.IO;
using System.Text;

namespace MyNamespace {
	public class MyActivity {
		
		private async Task<bool> UserProfilePUT () {

			string url = "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create (new Uri(url));
			request.ContentType = "application/json";
			request.Headers.Add("x-api-key", "XXXXXXXXXXXXXXXXXXXX");
			
			request.Method = "PUT";
			
			string postData = "{\"O365ID\":\"Ravi\",\"O365Token\":\"RaviTokeb\"}";
			ASCIIEncoding encoding = new ASCIIEncoding ();
			byte[] byte1 = encoding.GetBytes (postData);
			request.ContentLength = byte1.Length;
			Stream newStream = request.GetRequestStream ();
			newStream.Write (byte1, 0, byte1.Length);
			newStream.Close ();
			
			using (WebResponse response = await request.GetResponseAsync ()) {
				using (Stream stream = response.GetResponseStream ()) {
					return true;
					//process the response
				}
			}
		}
	}
}

```

UserProfile Delete
--------------

```C#
using System;
using System.Threading.Tasks;
using System.Net;
using System.IO;
using System.Text;

namespace MyNamespace {
	public class MyActivity {
		
		private async Task<bool> UserProfileDelete () {

			string url = "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create (new Uri(url));
			request.ContentType = "application/json";
			request.Headers.Add("x-api-key", "XXXXXXXXXXXXXXXXXXXX");
			
			request.Method = "DELETE";
			
			string postData = "{}";
			ASCIIEncoding encoding = new ASCIIEncoding ();
			byte[] byte1 = encoding.GetBytes (postData);
			request.ContentLength = byte1.Length;
			Stream newStream = request.GetRequestStream ();
			newStream.Write (byte1, 0, byte1.Length);
			newStream.Close ();
			
			using (WebResponse response = await request.GetResponseAsync ()) {
				using (Stream stream = response.GetResponseStream ()) {
					return true;
					//process the response
				}
			}
		}
	}
}

```

UserProfile Query
--------------

```C#
using System;
using System.Threading.Tasks;
using System.Net;
using System.IO;
using System.Text;

namespace MyNamespace {
	public class MyActivity {
		
		private async Task<bool> UserProfileQuery () {

			string url = "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/query";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create (new Uri(url));
			request.ContentType = "application/json";
			request.Headers.Add("x-api-key", "XXXXXXXXXXXXXXXXXXXX");
			
			request.Method = "POST";
			
			string postData = "{\"id\":\"CardID\",\"value\":\"12391\"}";
			ASCIIEncoding encoding = new ASCIIEncoding ();
			byte[] byte1 = encoding.GetBytes (postData);
			request.ContentLength = byte1.Length;
			Stream newStream = request.GetRequestStream ();
			newStream.Write (byte1, 0, byte1.Length);
			newStream.Close ();
			
			using (WebResponse response = await request.GetResponseAsync ()) {
				using (Stream stream = response.GetResponseStream ()) {
					return true;
					//process the response
				}
			}
		}
	}
}
	
```

Code Samples for Node JS
--------------
UserProfile Create
--------------
```javascript
// request UserProfile Create 
(function(callback) {
    'use strict';
        
    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'XXXXXXXXXXXXXXXXXXXX.amazonaws.com',
        port: '443',
        path: '/qa/api/v1/userprofile?one=1&two=2',
        method: 'POST',
        headers: {"x-api-key":"XXXXXXXXXXXXXXXXXXXX","Content-Type":"application/json"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;
 
    // Paw Store Cookies option is not supported

    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';
        
        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;            
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ? 
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;
            
            callback(null, res.statusCode, res.headers, responseStr);
        });
        
    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{\"Name\":\"Ravikian\",\"CardID\":\"1239\",\"Domain\":\"SSDI\",\"ActiveDirID\":\"ssdiblr\",\"Email\":\"kravikiran@ssdi.sharp.co.in\",\"O365ID\":\"kravikiran@onmicrosoft.com\",\"O365Token\":\"ABCDEFGHh\"}")
    request.end();
    

})((error, statusCode, headers, body) => {
    console.log('ERROR:', error); 
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});


```

UserProfile Get
--------------
```javascript
// request UserProfile Get 
(function(callback) {
    'use strict';
        
    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'XXXXXXXXXXXXXXXXXXXX.amazonaws.com',
        port: '443',
        path: '/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2',
        method: 'GET',
        headers: {"x-api-key":"XXXXXXXXXXXXXXXXXXXX","Content-Type":"application/json"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;
 
    // Paw Store Cookies option is not supported

    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';
        
        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;            
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ? 
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;
            
            callback(null, res.statusCode, res.headers, responseStr);
        });
        
    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{}")
    request.end();
    

})((error, statusCode, headers, body) => {
    console.log('ERROR:', error); 
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

```

UserProfile PUT
--------------
```javascript
// request UserProfile PUT 
(function(callback) {
    'use strict';
        
    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'XXXXXXXXXXXXXXXXXXXX.amazonaws.com',
        port: '443',
        path: '/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2',
        method: 'PUT',
        headers: {"x-api-key":"XXXXXXXXXXXXXXXXXXXX","Content-Type":"application/json"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;
 
    // Paw Store Cookies option is not supported

    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';
        
        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;            
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ? 
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;
            
            callback(null, res.statusCode, res.headers, responseStr);
        });
        
    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{\"O365ID\":\"Ravi\",\"O365Token\":\"RaviTokeb\"}")
    request.end();
    

})((error, statusCode, headers, body) => {
    console.log('ERROR:', error); 
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

```

UserProfile Delete
--------------
```javascript
// request UserProfile Delete 
(function(callback) {
    'use strict';
        
    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'XXXXXXXXXXXXXXXXXXXX.amazonaws.com',
        port: '443',
        path: '/qa/api/v1/userprofile/%7Bid%7D?one=1&two=2',
        method: 'DELETE',
        headers: {"x-api-key":"XXXXXXXXXXXXXXXXXXXX","Content-Type":"application/json"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;
 
    // Paw Store Cookies option is not supported

    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';
        
        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;            
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ? 
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;
            
            callback(null, res.statusCode, res.headers, responseStr);
        });
        
    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{}")
    request.end();
    

})((error, statusCode, headers, body) => {
    console.log('ERROR:', error); 
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

```

UserProfile Query
--------------
```javascript
// request UserProfile Query 
(function(callback) {
    'use strict';
        
    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'XXXXXXXXXXXXXXXXXXXX.amazonaws.com',
        port: '443',
        path: '/qa/api/v1/userprofile/query',
        method: 'POST',
        headers: {"x-api-key":"XXXXXXXXXXXXXXXXXXXX","Content-Type":"application/json"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;
 
    // Paw Store Cookies option is not supported

    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';
        
        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;            
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ? 
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;
            
            callback(null, res.statusCode, res.headers, responseStr);
        });
        
    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{\"id\":\"CardID\",\"value\":\"12391\"}")
    request.end();
    

})((error, statusCode, headers, body) => {
    console.log('ERROR:', error); 
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

```


Code Samples for JavaScript
--------------
UserProfile Create
--------------
```javascript
// UserProfile Create (POST https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile)

jQuery.ajax({
    url: "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile?" + jQuery.param({
        "one": "1",
        "two": "2",
    }),
    type: "POST",
    headers: {
        "x-api-key": "XXXXXXXXXXXXXXXXXXXX",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "CardID": "1239",
        "Domain": "SSDI",
        "O365ID": "kravikiran@onmicrosoft.com",
        "O365Token": "ABCDEFGHh",
        "Name": "Ravikian",
        "Email": "kravikiran@ssdi.sharp.co.in",
        "ActiveDirID": "ssdiblr"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```

UserProfile Get
--------------
```javascript
// UserProfile Get (GET https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D)

jQuery.ajax({
    url: "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D",
    type: "GET",
    data: {
        "one": "1",
        "two": "2",
    },
    headers: {
        "x-api-key": "XXXXXXXXXXXXXXXXXXXX",
        "Content-Type": "application/json",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```

UserProfile PUT
--------------
```javascript
// UserProfile PUT (PUT https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D)

jQuery.ajax({
    url: "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?" + jQuery.param({
        "one": "1",
        "two": "2",
    }),
    type: "PUT",
    headers: {
        "x-api-key": "XXXXXXXXXXXXXXXXXXXX",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "O365ID": "Ravi",
        "O365Token": "RaviTokeb"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});



```

UserProfile Delete
--------------
```javascript
// UserProfile Delete (DELETE https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D)

jQuery.ajax({
    url: "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/%7Bid%7D?" + jQuery.param({
        "one": "1",
        "two": "2",
    }),
    type: "DELETE",
    headers: {
        "x-api-key": "XXXXXXXXXXXXXXXXXXXX",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({

    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```

UserProfile Query
--------------
```javascript
// UserProfile Query (POST https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/query)

jQuery.ajax({
    url: "https://XXXXXXXXXXXXXXXXXXXX.amazonaws.com/qa/api/v1/userprofile/query",
    type: "POST",
    headers: {
        "x-api-key": "XXXXXXXXXXXXXXXXXXXX",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "id": "CardID",
        "value": "12391"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```
