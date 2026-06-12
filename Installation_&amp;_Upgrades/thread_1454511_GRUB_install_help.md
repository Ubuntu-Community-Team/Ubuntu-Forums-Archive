---
title: "GRUB install help"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by tim.is.awesome on 2010-04-14
first off, im a noob and i apologize if this question has been answered many many times, and for wasting your time if it has been.

guys i need some assistance. i was installed ubuntu 9.10 and i installed the boot loader to /dev/sda and now i cant start up windows or ubuntu for that matter. 

i installed ubuntu to my external HDD. and windows is on my internal HDD. i was trying to have it so when i had my external HDD plugged in it started up ubuntu and when it was unplugged it started up windows.

any ideas how i can fix this and accomplish what i was trying to do in the first place?

i thank you before hand.

here is a pic of the possible places for the boot loader (if it helps) [http://twitpic.com/1fmklg/full](http://twitpic.com/1fmklg/full)

---

### Post by 2hot6ft2 on 2010-04-14
You should have installed it to the usb drive (/dev/sdb) instead you installed it to the internal hard drive (/dev/sda). See this guide section 16 for fixing the internal drives boot and it will tell you how to install grub2 to the usb drive as well in section 13.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by tim.is.awesome on 2010-04-14
> **2hot6ft2 said:**
> You should have installed it to the usb drive (/dev/sdb) instead you installed it to the internal hard drive (/dev/sda). See this guide section 16 for fixing the internal drives boot and it will tell you how to install grub2 to the usb drive as well.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

thank you. so i now when i install it i should put the boot loader in /dev/sdb?

---

### Post by 2hot6ft2 on 2010-04-14
You're welcome and thanks for saying I'm awesome.:-\" All those things you have open having to do with the grub menu.lst don't apply to grub2 it's a lot different and doesn't have a menu.lst. You'll see in the guide.

---

### Post by presence1960 on 2010-04-14
You are still going to need to fix the MBR of the internal disk. You can do that from the ubuntu Live CD or from an installation of ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```Your internal disk will now have an MBR that will boot right to windows when the external is unplugged.

---

