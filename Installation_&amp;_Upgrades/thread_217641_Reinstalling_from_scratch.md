---
title: "Reinstalling from scratch"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Zooropa on 2006-07-17
Hi folks,

I have a dual boot with Xp through grub, it's running from one physical drive with a few partitions.

After upgrading from Breezy I've had a few issues, so i just want to install Dapper from a fresh .iso.

What's the best way to totally remove what I have just now for Ubuntu, but leave Grub unharmed?

---

### Post by x64Jimbo on 2006-07-17
You're going to need to re-do your Grub when you re-install anyway. Grub boots Linux by calling your kernel version specifically, and if you're still running Breezy, you're probably not running the latest kernel, which would be included in Dapper when you download it. I'd recommend just letting Dapper re-write your Grub configuration when you re-install. Just re-format the partition that Breezy resides on currently when you re-install, and you should get a fresh and clean system.

---

### Post by Zooropa on 2006-07-17
Excellent, so essentially when i fire in this new CD I just install as I did initially and it'll take care of it?

Nice one, fingers crossed!

---

### Post by x64Jimbo on 2006-07-17
Well, you'll still need to re-format the partition to make sure that none of the old files are hanging around on the disk, but other than that, it should be just like the first time you installed.

---

### Post by Zooropa on 2006-07-17
Got it installed, but when it boots up I don't get the login screen...it all goes black.

There's an issue somewhere, but I'll see if it's been posted before

---

### Post by x64Jimbo on 2006-07-17
It's likely that something went haywire with your video card stuff. Poke around in xorg.conf and see if anything looks funky or different from the last one. Installing from the LiveDVD should make all that stuff work since it works on the live portion. One solution is to boot LiveDVD and save ITS xorg.conf file somewhere and then use it to replace the one on your hard disk.

---

