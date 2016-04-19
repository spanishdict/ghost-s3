# Ghost S3 Storage, compatability mode

This module allows you to read and write images from Amazon S3 instead of
storing them locally.

After installing, new images that you save will use an absolute URL to S3. Any
requests to `/content/images/` will be proxied to S3, so that any previous
images in your blog will not be affected.

## Installation

```bash
$ npm install --save ghost-s3-compat
```

## Create a storage module

Create a file `content/storage/ghost-s3/index.js` (manually create those folders
if they do not exist). Put this code inside of it.

```javascript
'use strict';
module.exports = require('ghost-s3-compat');
```

## Configuration

Create new IAM User with permissions to get object from that bucket. Save the
`ACCESS_KEY` and `ACCESS_SECRET_KEY`.

In `config.js`, add a `storage` block for each environment.

    storage: {
        active: 'ghost-s3',
        'ghost-s3': {
            accessKeyId: 'Put_your_access_key_here',
            secretAccessKey: 'Put_your_secret_key_here',
            bucket: 'Put_your_bucket_name_here',
            region: 'Put_your_bucket_region_here'
        }
    },

### Asset host

You can add `assetHost` to your config to specify a virtual host url. For more
information, [read this section](http://docs.aws.amazon.com/AmazonS3/latest/dev/VirtualHosting.html)
in the AWS docs.

## Copyright & License

Copyright (c) 2010-2016 Curiosity Media, Inc.

Released under the [MIT license](https://github.com/muzix/ghost-s3/blob/master/LICENSE).
