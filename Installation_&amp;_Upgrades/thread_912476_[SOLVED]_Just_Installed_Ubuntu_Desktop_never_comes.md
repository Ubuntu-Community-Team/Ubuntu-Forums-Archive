---
title: "[SOLVED] Just Installed Ubuntu Desktop never comes up"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by bbrunning on 2008-09-06
I just installed Ubuntu on a multiboot system. I used my 1TB HD and set aside 100GB for linux. I installed Ubuntu manually using 96GB for the root and 4GB for the Swap. After installation my system reboots and I set it to go to linux. Ubuntu brings up the logon screen, I log in and a small box comes up which stays blank the whole time. Nothing else happens. I've reinstalled ubuntu 4 times and the same thing happens.

Any Ideas?

---

### Post by BenAshton24 on 2008-09-06
hmm, make sure that your using the latest version of ubuntu, 8.04, you could try pressing escape when your computer says loading grub boot or whatever and choose Ubuntu safemode or one of the others then see if that works

Hope this helps :D

---

### Post by bbrunning on 2008-09-07
I am using the latest version. I downloaded it tonight. I logged into ubuntu recovery mode (Or whatever the other mode is on the grub boot menu) and it went in just fine and brought up the desktop. I did get an error:
Last error msg was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message based security policy blocked the reply, reply timed out or expired, network connection was broken.

I have installed ubuntu about 15 times on other systems with no problem (intel based). The only difference is this system is using an AMD processor. I don't know if that makes anything different but thought it may be handy to know in diagnosing the problem. As for any other info that may help.

---

### Post by bbrunning on 2008-09-07
Alright I got it working. Once I was in recovery mode I checked my devices and found that the nvidia card wasn't using the drivers. Once I enabled it and rebooted everything worked.

Thanks for pointing me in the right direction!

---

### Post by Sef on 2008-09-07
> Alright I got it working. Once I was in recovery mode I checked my devices and found that the nvidia card wasn't using the drivers. Once I enabled it and rebooted everything worked.

Thank you for posting how you were able to resolve your problem.

---

