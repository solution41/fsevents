Older versions of "fsevents" Node.js library are vulnerable to code injection because they download additional binaries from dynamically generated URLs.

I discovered that versions up to 1.x.x of fsevents library download binaries from a S3 bucket URL https://fsevents-binaries.s3-us-west-2.amazonaws.com, but the bucket fsevents-binaries did not exist. This can made it possible for an attacker to claim this S3 bucket and upload arbitrary code in there. Because this bucket had expired an if a attacker take this addres he/she can upload malicious binary and this will end up with getting remote access on the endpoint which use this insecure and deprecated version of fsevents Node.js library.

It is important to highlight that all of the vulnerable versions are 4+  years old and have been marked as deprecated by the maintainer in NPM.  There is also a note from the maintainer that the versions could use insecure binaries.
https://www.npmjs.com/package/fsevents/v/1.1.2
https://www.npmjs.com/package/fsevents/v/1.2.2
https://www.npmjs.com/package/fsevents/v/1.2.8
https://www.npmjs.com/package/fsevents/v/<1.X.X>

The v1 package contains DANGEROUS / INSECURE binaries. Upgrade to safe fsevents v2
