---
title: "Curl, Twitter.php"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by drhiii on 2010-03-10
I am trying to run an app, twitter.php, under Joomla, running on Ubuntu (version info below).  Have gone through a myriad of upgrades, updates, curl is installed, and so on...but the app does not 'fire' and send the anticipated 'tweet' to Twitter.  

Anyone suggest how to test this app, how to test that curl is indeed being called by twitter.php, and so on?  Am at a bit of a loss.  Help?

(pardon if this is not the right forum to post in... please repost if there is a better choice)

Info:

Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
Apache version  2.2.9

PHP 5.2.6-2ubuntu4.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Aug 21 2009 20:36:27)

Curl is installed.

---

### Post by rubo77 on 2010-09-04
i tried this:
[http://www.commandlinefu.com/commands/view/176/update-twitter-via-curl](http://www.commandlinefu.com/commands/view/176/update-twitter-via-curl)
```

curl -u user:pass -d status="Tweeting from the shell" http://twitter.com/statuses/update.xml
```

but i get an error:
[HTML]<?xml version="1.0" encoding="UTF-8"?>
<errors>
  <error code="53">Basic authentication is not supported</error>
</errors>
[/HTML]

---

### Post by darshan.maiya on 2010-11-02
hi i am getting the same above error..
isn't there any solution for this?

---

