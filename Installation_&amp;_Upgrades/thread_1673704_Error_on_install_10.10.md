---
title: "Error on install 10.10"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Jinx13 on 2011-01-22
Hey guys...! Just wanna  explain i'm a Linux n00b :p
 
I been trying to dual boot Kubuntu x64/Windows Se7en x64.
The install on the 10.10 Desktop disk seems great, but I keep getting an error at 66% :(
 
> Unable to install GRUB in /dev/mmcblk0
Excuting 'grub-install/dev/mmcblk0' failed
This is a fatal error.
 
Hope someone can help,
Thanks in advance,
 
Regards,
 
Jinx13.

---

### Post by Quackers on 2011-01-22
Have you checked the MD5SUM of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out, whilst booting from the cd press the Esc key, enter your language and you should get a screen giving you some options. Choose the one that checks the cd for errors.

---

### Post by Jinx13 on 2011-01-23
Thanks for your reply.
 
I checked the .iso and it said that the MD5 Hash is different. I don't understand why because I downloaded the .torrent :o
 
You think I should download again?
Also on the MD5 page it doesn't give CD/DVD checksums so do you think my checksum could actually be right, as I downloaded the DVD version.
 
I did try to register on Kubuntu forums first but gave up trying lmao.
 
Thanks again,
Regards,
 
Jinx13

---

### Post by Quackers on 2011-01-23
If the md5 sum is different, the download isn't perfect. If you're sure you are comparing the correct version and release number and type (32 bit/64 bit), that is :-)

---

### Post by Rubi1200 on 2011-01-23
Are you also installing with a RAID array?

If yes, see here:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

---

### Post by Jinx13 on 2011-01-23
> **Quackers said:**
> If the md5 sum is different, the download isn't perfect. If you're sure you are comparing the correct version and release number and type (32 bit/64 bit), that is :-)
 
Right :( I started again downloaded etc as the check sums we're different.
I downloaded and checked MD5 - and it was correct :)
I started the disk and then did a disk check - No errors
I started the instalation again and it stuck at the same point with the same error :(
 
 
> **Rubi1200 said:**
> Are you also installing with a RAID array?
 
Nope :)
 
 
 
Thanks,
Regards,
 
Jinx13

---

### Post by presence1960 on 2011-01-23
Boot the Live CD/USB. Choose try ubuntu. When the desktop loads open a terminal and run ```
gksu gparted
```

Look at your hard disk info in gparted. If you have any devices labeled anything other than /dev/sda (b,c,etc) and you have names with a string of letters that means your device has RAID metadata on it. It is easy to remove. Close gparted. In terminal run ```
dmraid -E -r /dev/sda
``` (if other disk has it run sdb, sdc, etc in place of sda in the command)

If you are not comfortable with this post a screenshot of gparted showing the funny named devices.

---

### Post by Jinx13 on 2011-01-24
Hmm thanks for your reply trying to run terminal and entering gksu gparted.
First it asked me to install, so did that.
Then when I try to run, it's asking for password (which it doesn't set up on live cd)
Anyone know default kubuntu live password?
I tried ```
sudo passwd
``` But it won't let me input anything

Regards,

Jinx13

---

