---
title: "How to upgrade from dard drive"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by shaquille on 2011-04-04
Hi, I am using Ubuntu 10.04 LTS. For some hardware problem I could not upgrade my Ubuntu to 10.10. Now the problem is solved. I have the ISO image file of 10.10 (ubuntu-10.10-desktop-i386.iso). As I live in Bangladesh, there I have to use a slow connection. So, It will take long time if I have to upgrade online. Is there any way for me to upgrade my version of Ubuntu using the ISO image file?

Thanks.

---

### Post by Hedgehog1 on 2011-04-04
For a network free install/upgrade of 10.10, Un-check the two orange update boxes during the install setup:

[IMG]http://img818.imageshack.us/img818/8751/small13preparing.png[/IMG]

After the first reboot following the install, don't let the update manager do updated until you change these settings:

Check the 'install from cdrom' box:

[IMG]http://img845.imageshack.us/img845/316/ppacd.png[/IMG]

And un-check all the network update choices in this panel:

[IMG]http://img146.imageshack.us/img146/3261/ppa2.png[/IMG]


You can also stop the automatic updates in the System >> Preferences >> Startup Applications and un-check the 'update manager'. 


***The Hedge***

:KS

---

