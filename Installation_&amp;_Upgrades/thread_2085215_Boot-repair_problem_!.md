---
title: "Boot-repair problem !"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by JohnTube on 2012-11-17
I encountered a problem with my ubuntu 12.04, I used a live usb ubuntu 12.10 to install boot-repair : first message : mdadm something, next thing is /boot to tell me to check it in the advanced config... 
After doing the Recommended repair and reboot my laptop does not reconginze any OS on my drive any more  

this is the link from boot-repair : [http://paste.ubuntu.com/1365240](http://paste.ubuntu.com/1365240)

---

### Post by YannBuntu on 2012-11-17
Hello
> **JohnTube said:**
> this is the link from boot-repair : [http://paste.ubuntu.com/1365240](http://paste.ubuntu.com/1365240)

You have installed Ubuntu on LVM, and it is not detected by os-prober.
Another problem is that your /usr partition seems to be broken: Boot-Repair can't detect any apt nor grub executable in it.
Only solution i know in this case is to fix system packages this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

