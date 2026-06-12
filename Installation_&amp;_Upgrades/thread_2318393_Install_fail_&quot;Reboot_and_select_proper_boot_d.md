---
title: "Install fail &quot;Reboot and select proper boot device&quot; (Toshiba Satellite)"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by randomuser12 on 2016-03-25
I decided to install Lubuntu 14.04 LTS on a Toshiba Satellite laptop  with DVD-RW (image: lubuntu-14.04.4-desktop-amd64.iso). Install went OK,  but when I restarted the computer, it ended up in black screen saying:  "Reboot and select proper boot device". I couldn't do anything.

I changed the boot order that HDD is first, but it didn't help. After  that I decided to reinstall Lubuntu, but that didn't have any effect  either. In BIOS there's UEFI/CSM options, and UEFI has been on. Secure  Boot has been all the time disabled.


Here's the info from boot-info: [https://paste.ubuntu.com/15501481/](https://paste.ubuntu.com/15501481/)
 

Any ideas how to proceed? I really would like to make this laptop working.

---

### Post by randomuser12 on 2016-03-26
I got this fixed. I disabled UEFI and put CSM on. Then I re-installed Lubuntu from USB stick. System is now working.

However, system won't shutdown or restart. I freezes to blue Lubuntu screen and when all five dots are blue, it simply freezes.

---

### Post by mörgæs on 2016-03-26
Does it shutdown if you press enter while it's frozen?

---

### Post by randomuser12 on 2016-03-26
No.

More details here: [http://ubuntuforums.org/showthread.php?t=2318439&p=13460775#post13460775](http://ubuntuforums.org/showthread.php?t=2318439&p=13460775#post13460775)

---

