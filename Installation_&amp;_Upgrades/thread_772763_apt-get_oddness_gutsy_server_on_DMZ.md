---
title: "apt-get oddness gutsy server on DMZ"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by eyeroll on 2008-04-28
Howdy,

I am having issues with running apt-get update - and all other apt functions for that matter.  I have a recently installed Gutsy server that I am building and placed it in a DMZ.

When I run apt-get update all of my sources are "111 connection refused".  I can ping internet based hosts - yahoo.com for exampple, and I have access in to the server via ssh. 

I then put the server on my LN temporarily and apt-get update worked...

Any ideas why when the server is located on a DMZ subnet - going through the same firewall as the ALN - apt-get update fails ?

I am really confused by tis.

Thanks,

eyeroll

---

