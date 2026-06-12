---
title: "Plaese help me"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by chidi on 2011-03-20
Hello everyone,
Am new to linux and recently deleted my window xp for linus due to the small capacity of my hard disk which is 12GB. 
When now trying to install the ubuntu desktop 10.10 it was going smoothly until it got to the piont of scanning the CD rom even though i am using a flash/removable disk...then a message appears
                   apt configuration problem...An attempt to configure apt to install additional    packages from CD failed...

Please what do i do next

---

### Post by Quackers on 2011-03-20
Welcome to UF :-)
Did you check the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the md5sum is wrong then the iso should be downloaded again.
If the md5sum checks out ok, when booting from the usb, at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language and on the next screen choose the option to check the cd for errors (it doesn't matter that you are using a usb, it's the same).
If that finds any errors at all the image is no good. If the md5sum checks ok, you will need to burn the image to usb again.

---

