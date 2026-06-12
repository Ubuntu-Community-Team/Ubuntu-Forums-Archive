---
title: "Help: Grub2 Not Detecting Linux Partition After Upgrade"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by ngrieb on 2010-07-12
I have a Toshiba NB305, which I just attempted auto-upgrade from 9.10 to 10.04 LTS. The problem is that after the upgrade grub2 cannot find the correct UUID to boot from. I continually get tossed to the screen that says "Waited for boot...timed out", blah blah. I have already attempted to specify the correct bootable drive by editing the grub menu that appears, but this doesn't seem to change anything. Does any one know another way around this? 
And if not, is there any way to install via flash disk that simply lets you upgrade or repair? If so how do you do this?

---

### Post by kansasnoob on 2010-07-12
Please post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can use a Live CD or Live USB to do so.

---

### Post by ngrieb on 2010-07-12
I'm not quite sure what this is? Linux insists that the drive it is searching for doesn't exists. Right now there is no way for me to do this anyways. It sounds like I need to first find a viable shell in order to do this, which I have not yet been able to obtain. I only have this one computer, and am using my Windows partition to try and find help. If you can further elaborate bow this works it would be of some help.

---

### Post by ngrieb on 2010-07-12
Ok, it actually doe boot into the correct hard drive, just got that to work...the problem is that a message "resuming: libcrypt 1.4.4" comes up and then proceeds to take like 10 minutes to bring up any login screen. This is absolutely crap. Part of the reason I wanted to upgrade was that I heard that 10.04 had a better startup and resume time, so what the heck is going on here?

---

### Post by ngrieb on 2010-07-12
I found the answer on another page. Just went into bios and selected "Compatibility" instead of "ACHI" or whatever that is...

---

