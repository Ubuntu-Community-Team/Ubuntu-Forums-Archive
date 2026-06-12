---
title: "Dell D420 upgrade to 10.10, no network connectivity"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Matt007 on 2010-10-14
I have a Dell D420 that I successfully upgraded to Ubuntu 10.10. Everything looks fine except there is no LAN or wireless working. I upgraded the BIOS to the latest version (A06) and there are no proprietary drivers listed under System/Administration/Additional drivers.
 
when I plug the LAN cable into the 420, the indicator cycles for a long time but eventually displays the red exclamation mark.
 
Any ideas?

---

### Post by pjvolkma on 2010-10-22
I found something similar when I tried 10.10 this morning on my Dell D420.  The wired network worked OK but I was unable to get wireless going.  I tried loading the proprietary driver but got an error message and no wireless.  Previous releases work fine.

As my environment is usually wireless only these days, having only a wired connection won't work for me.

---

### Post by ajm661023 on 2010-10-25
Replace the standard NetworkManager with WICD as written on this thread:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1598673](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1598673)


sudo apt-get install wicd
sudo apt-get remove --purge network-manager network-manager-gnome

---

