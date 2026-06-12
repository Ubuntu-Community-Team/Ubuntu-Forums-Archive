---
title: "Grub menu showing even though I only have 1 OS"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by juanfernandes on 2013-09-26
I think that some updates have cause my ubuntu 13.04 to start showing the grub menu when booting up.

Yes I don't have any other OSs installed on that hard drive. 

Any idea why this has started happening? 

I have the modified version of Ubuntu - the one that enables it to work with secure boot. 

Thanks in advance

---

### Post by ibjsb4 on 2013-09-26
Go to System Settings>User Accounts

Are you still set for auto login?

Or you can do it manually.

[http://www.liberiangeek.net/2012/03/automatically-login-to-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/automatically-login-to-ubuntu-12-04-precise-pangolin/)

---

### Post by grahammechanical on 2013-09-26
You also say this

> [COLOR=#000000]Yes I don't have any other OSs installed on that hard drive. [/COLOR]

Does that mean that you have at least one other drive and there is at least one other OS on this other drive? That would be the reason. You may not have had this other drive connected when you installed Ubuntu but a recent update may have brought in a newer Linux kernel which, in turn, prompted a reconfiguration of the Grub configuration files during which that other OS was detected.

All versions of Ubuntu since 12.10 onwards work with secure boot and now included in this are latest images of 12.04, such as 12.04.2 and 12.04.3. There cannot be any connection with this issue.

Regards.

---

### Post by juanfernandes on 2013-10-14
This seems to have fixed itself. But it had nothing to do with the suggestions above, but thanks for the replies.

---

