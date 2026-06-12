---
title: "Flash Installation Fail for Chromium"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by eric75 on 2015-07-10
Running ubuntu 14.04 LTS for about a month or so. I am trying to install Adobe Flash in Chromium.
 
At [https://get.adobe.com/flashplayer/?no_redirect](https://get.adobe.com/flashplayer/?no_redirect), there are 4 versions:

YUM, .tar.gz, .rpm, APT for Ubuntu 10.04+

I tried a few, including the apt one, not working. (apt one just sits there)


Then I tried [https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash), and on step 3, type: EN: Install "adobe-flash-plugin"

I get "No Items Match "adobe-flash-plugin"."

Anyone know how to get it to install or do I need to use an alternate?

---

### Post by deadflowr on 2015-07-10
You need to use an alternative.
Chrome and chromium don't use the normally installed flash but instead use a special plugin called pepperflash.
Google Chrome, the googlized version of chromium comes with this built in.
chromium however does not.
But it is possible to get it for chromium.
You need to look for a package called "pepperflashplugin-nonfree"
It is in the multiverse repository, so you might want to make sure that it is enabled."(it should be, but you never know)

---

### Post by eric75 on 2015-07-14
Got it. Thanks.

---

