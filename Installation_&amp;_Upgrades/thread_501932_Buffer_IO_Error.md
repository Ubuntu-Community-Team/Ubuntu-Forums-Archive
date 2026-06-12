---
title: "Buffer I/O Error?"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by dodgerwv on 2007-07-15
I can't get Feisty Fawn to load onto a new computer. The live CD takes forever to load. It finally loads with this error message: 242.3295 Buffer I/O error on device fd0 logical block 0

The installation seemingly went well, but the computer goes to a blank screen after loading Grub. It's a new Dell Optiplex 320 with a Pentium 4 processor if that helps.

Thanks in advance for any help. I've loaded 7.04 on three other computers and the office and it works fine. My wife who would be using this computer doesn't want to have go back to using Windows if I can't get a fix!

---

### Post by dodgerwv on 2007-07-16
Tried to reinstall.  Didn't get the error message, but still cannot boot from the harddrive.  The GRUB loads and then I get a black screen with a flashing cursor up top.  Nothing happens from that point.  The live CD works fine and XP is still fine, but I can't get past the blank screen with a cursor when I try to boot Feisty from the harddrive.

I'm open to any worthwhile suggestions.  Thanks in advance for help.

---

### Post by dodgerwv on 2007-07-16
Had same problem with trying to load Kubuntu.  It's fine on the CD, but will not do anything after it starts loading GRUB.  I get the feeling that I'm missing some sort of relatively simple fix, but am lost right now.  Thanks in advance for any help.

---

### Post by confused57 on 2007-07-16
Here's a bug report for this problem, with a possible solution:
[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

You should be able to mount your root partition with the live cd & make the changes mentioned in the report:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

