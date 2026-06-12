---
title: "Need help fixing the Grub Error on my Natty upgrade  please"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by Chancex on 2011-04-11
First off, I'm a complete newb to *nix and from all I've read on the forums since I hit the problem, this is not that unusual. There are just some steps and language that are being thrown around that I do not understand. Thus, I am going to start a new post and hope for the best :).

My current setup was:
4 x 500 gb hard drives in (software / onboard controller) Raid 10 (1 +0) with Windows 7 x64 as the primary OS
1 500 gb hard drive with Ubuntu 10.10 installed

After upgrading to Ubuntu 11.04 Beta, I hit the Grub Error. I have removed the 5th HDD but still getting it on boot into Windows 7. 

I am currently in the process of copying all files from my raid via a 10.10 flash drive boot (fortunately was able to mount my raid's partitions).

From here I am seeing various suggestions on different threads. Just wondering what I should do?

Thanks,
Chance

---

### Post by oldfred on 2011-04-11
Welcome to the forums. I do not know RAID, as that is not standard for most desktops.

In hindsight, if you have a 500GB drive dedicated to Ubuntu, you may have done better to just create a 20GB / (root) partition for Natty. Natty is still beta and often has breakages and may not work well on some systems until released or fixes are figured out.

To see your entire configuration. You need this version of boot script to work with Natty, but like Natty it is being updated:

Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

---

### Post by Chancex on 2011-04-11
Hey oldfred,

Thanks - I regret performing the upgrade and would happily role back if I could.

Just so I do not mess anything up with assumptions, what should I do with this script? Also, how would you recommend running it? (I have a flash drive that I am currently booted ubuntu 10.10 too).

---

### Post by oldfred on 2011-04-11
Just run it from your flash drive. Newer version works on most older systems, but parses Natty MBR and gpt partitioning systems better.

You can run script from any working Ubuntu, liveCD, liveUSB and many other Linux LiveCD systems. If from liveCD you will not save script unless you copy it somewhere else before you reboot.

---

