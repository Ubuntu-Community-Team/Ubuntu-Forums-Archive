---
title: "Problems to login after 14.04 installation"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by Marcos_Quintana on 2014-08-26
I installed Ubuntu 14.04 from Ubuntu 12.04

It seems that the installation was successful, but in the login screen, after introducing my password I am returned to the same screen.

I am positive that my password is right. In fact, testing with a different one shows "Invalid password, please try again"

I can't spot anything strange in the grub file for "Ubuntu". Please see attachment.

Any ideas about how to login successfully?

---

### Post by Marcos_Quintana on 2014-08-26
I have been trying to follow the help from thread 

[http://ubuntuforums.org/showthread.php?t=2234623](http://ubuntuforums.org/showthread.php?t=2234623)

When I run

tail ~/.xsession-errors

I get

XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
        after 20 requests with 0 events remaining.

---

