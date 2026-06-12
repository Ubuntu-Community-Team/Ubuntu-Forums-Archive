---
title: "Problem with USB stick install"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by Photobug on 2013-12-23
I have a thumb drive I used to install a working version of Ubuntu 12.04.  I also use it to trouble shoot and run Ubuntu on my laptop.  I want to now use it to install a version of 12.04 on another drive, but I am not having a number of problems with it.  The problems are as follow:

[LIST]
[*]Cant update software because not enough space
[*]Can't run GParted because it won't find devices
[*]All commands besides "suspend" are missing.
[/LIST]

I have searched and tried to fix these but no success.  I found the first issue was a result of left over kernels in other peoples threads but since I have no previous OSs installed it is not my issue.  I did a search for restart and shutdown in the dash and could not find either.  Neither command is availiable from the upper right hand shutdown symbol.  I am not so concerned about these issues right now but am wondering if I should trust this Live USB drive to install a new OS on a hard drive, or should I try another one?

---

### Post by e-San on 2013-12-23
I'm not sure WHEN those problem occur. 

While making new thumb, while installing, while running live-usb?

Try to remake thumb, then install. Check if You use correct device. Try *fdisk /dev/sda* or so.

---

### Post by Photobug on 2013-12-23
> **e-San said:**
> I'm not sure WHEN those problem occur. 



All of the issues happen when the live Ubuntu is up and running from the thumb drive.  It starts up fine and runs fine.  It did have a problem installing Ubuntu on the hard drive.  So I am running Unetbootin now to create another thumb drive to try installation again from a fresh thumb drive.

---

