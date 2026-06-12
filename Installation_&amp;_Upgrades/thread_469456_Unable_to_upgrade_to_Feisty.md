---
title: "Unable to upgrade to Feisty"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by OzRob on 2007-06-09
I am a happy Edgy user but want to upgrade to Feisty.
I have made one modification to my installation and that was to blacklist ipv6, which enabled Firefox browser access, which I didn't have before the blacklisting.
When I use update manager I am told that I am "Your system is up to date" and when I select 'Check' It starts "Downloading package information".
I get a status of Failed for each of the nine files that it attempts to download.

---

### Post by OzRob on 2007-06-09
And.... when it finishes checking for downloads I get a message "Could not download all repository boxes" with each file having the message "..... connection timed out"

---

### Post by OzRob on 2007-06-12
Must have everyone stumped. I have burn't a Feisty live CD and that has no problems with getting updates. The problem I have is that I can't even seem to update from the CD. Alternatively, I would be happy to do a clean install of Feisty but how do I get it to use the Edgy partition?

---

### Post by zvacet on 2007-06-12
You can not do upgrade with live CD.Be sure that you have separate home partition before you go and install Feisty instead of Edgy.If you don´t have one make it.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

In the partition step you will select Edgy root patition and delete it and on it´s place you will install Feisty root partition.**Do not reformat home partition.**

---

### Post by OzRob on 2007-06-17
Thanks for the suggestion but what I did was download and update files bring me up to date on 6.10. Once I had done that I could then download Feisty. I suspect that it may have been apt related in that I had .45 rather than .45.2.

---

