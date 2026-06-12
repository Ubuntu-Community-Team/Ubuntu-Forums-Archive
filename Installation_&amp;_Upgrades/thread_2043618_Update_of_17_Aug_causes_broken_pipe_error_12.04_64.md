---
title: "Update of 17 Aug causes broken pipe error 12.04 64-bit"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2012-08-16
Just ran update that came out this evening (New York time).  Got broken pipe error.  Had great running system and upgrade ruined it.  Another error when I was trying load in failsafe mode said something about difference between update and nVidia driver (173 driver).

How am I supposed to fix this error?

John

---

### Post by bogan on 2012-08-17
Hi!, **cigtoxdoc**,

What was the actual 'broken pipe' error message?

If it was: 'Could not write bytes: Broken Pipe', I have been getting that for months; Posted about it but got no response. Does not seem to affect anything noticeably.

It just appears at every log-in & log-out.

Please post:```
 lspci -nnk | grep -iA3 VGA
sudo apt-cache policy nvidia-current
```The 173 driver should only be needed for nvidia cards of 5xxx series and before. It has recently been much changed to operate with the latest Xserver - previous versions did not - and is currently at 173.14.35. There is a 64bit version.

If you actually need it, you may benefit by updating the driver.

Chao!,** bogan.**

---

### Post by cigtoxdoc on 2012-08-18
Thank you, bogan.  Information you requested is shown below.

John

john@john-N68S3B:~$ lspci -nnk | grep -iA3 VGA 
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] [10de:03d6] (rev a2) 
	Subsystem: Biostar Microtech Int'l Corp Device [1565:1405] 
	Kernel driver in use: nvidia 
	Kernel modules: nvidia_current_updates, nvidia_173, nouveau, nvidiafb 
john@john-N68S3B:~$ sudo apt-cache policy nvidia-current 
[sudo] password for john:  
nvidia-current: 
  Installed: 304.37-0ubuntu1~precise~xup1 
  Candidate: 304.37-0ubuntu1~precise~xup1 
  Version table: 
 *** 304.37-0ubuntu1~precise~xup1 0 
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main amd64 Packages 
        100 /var/lib/dpkg/status 
     295.40-0ubuntu1.1 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted amd64 Packages 
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted amd64 Packages 
     295.40-0ubuntu1 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages 
john@john-N68S3B:~$

---

### Post by bogan on 2012-08-19
Hi!, **cigtoxdo**c,

 I do not know what to advise you, as Nvidia.com/Drivers is very ambiguous re your graphics. Hopefully, someone with experience of your Graphics will come on line.

What is certain, is that you do not want both the 173 and the 304 drivers installed at once.

Looking up your card, on Nvidai.com>Drivers, as: "GeForce  7025", gives the 304.37 driver as recommended, but when looked up as: "nForce 630a/GeForce 7025"it  gives no Linux driver at all, only Windows, even under 'Beta & Legacy drivers'.

You Posted:> Had great running system and upgrade ruined it. But apart from the 'broken pipe' messages, you do not say what the 'ruin' consists of.

So, on the whole, in your position-  as far as I know it -  I would use Synaptic to un-install the nvidia-173 entries, - probably four of them - and reboot.

If that did not work, then I would use sudo apt-get remove --purge to clear out all the nvidia stuff and start again, first with the default Nouveau driver, and then with 3.04.37 nvidia-current.

Chao!, **bogan.**

---

### Post by cigtoxdoc on 2012-08-19
Hello bogan:

Your are definitely the expert.  Correct driver is at

[http://www.nvidia.com/object/linux-display-amd64-304.37-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.37-driver.html)  This driver has 13 AUG 2012 date on it.

I got rid of all others showing on Synaptic except for 302.17 nvidia settings.  Now PC boots correctly.

Correct booting is very important as PC in question is used by my secretary -- only employee at my very small scientific consulting business.

John

---

