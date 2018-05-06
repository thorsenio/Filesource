filesource.js
============

Forked from https://github.com/thnew/Filesource with minimal changes.
The requested version of its only dependency, **tmp**, has been changed
from 0.0.23 to ^0.0.33.

Install:
npm install @thorsenio/filesource

You can e.g. use it, if you want to offer a function, taking all possible types of data sources.

Here are some simple examples of how to use it:

```javascript
var filesource = require('@thorsenio/filesource');

// Converts web-source to raw data
filesource.getRawData("http://blabla.com/blabla.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Something went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// raw data
});

// Converts filepath to raw data
filesource.getRawData("/files/example.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Something went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// raw data
});

// Converts web-source to readable filepath
filesource.getDataPath("http://blabla.com/blabla.pdf", function(resp){
	if(!resp.success)
	{
		console.log("Something went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// local filepath
	
	resp.clean();
});

// Converts raw data to readable filepath
var rawData = fs.readFileSync("/files/example.pdf");

filesource.getDataPath(rawData, function(resp){
	if(!resp.success)
	{
		console.log("Something went wrong: " + resp.error);
		return;
	}
	
	console.log(resp.data);	// local filepath
	
	resp.clean();
});
```
