---
title: "Ubuntu 10.10 Wont open the Installer on Live CD?"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by justinram22 on 2011-04-25
Hello! I seem to be having an odd problem.  Everything works fine on the live CD, I can open programs and do everything else, but when I try to click on the "Install Ubuntu 10.10", I see a flash of "Starting Admin.." on the bottom of the screen (on the minimize programs bar) and it doesn't open.  Anyone have any ideas on how I could get it to open, or an alternative way to install Ubuntu.  I got this computer from a friend and was going to turn it into a home server computer!

Thanks guys!! Any help is greatly appreciated!

---

### Post by Dutch70 on 2011-04-25
Please post the output of the following command...
```
sudo fdisk -l
```
That's a lower case L

---

### Post by Quackers on 2011-04-25
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's ok, check the cd for errors. Press any key at the first purple screen, choose language then use the check for errors menu item.

---

