---
title: "Dual boot problems"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by fordexplorerdotnet on 2007-08-14
Excuse my lack of proper terminology, I'm a noob.  My original intention was to use my system's boot menu to boot either XP from my primary IDE drive or Ubuntu from the secondary SATA drive.  When I originally installed, I screwed something up and it stuck Ub on the same drive as windows.  I then disconnected the IDE drive and installed again, so then I was running Ubuntu fine on the SATA.  After trying to acquiece a way to just run Win4Lin b/c the wife requires Windows, I decided to reinstall it using my restore discs.
Now when I boot, I can go into Win fine.  However, if I use the boot menu to boot from SATA it gives me a boot error which is escaping me right now, I'll post it in a bit.  Regardless, I can't get to grub.  
I can use the install disc to access my data though, which is an important fact because I need to get to my backed-up data I copied to the SATA before wiping and install for win on IDE.  As you know, Win isn't going to see the SATA drive.  The install Ubuntu disc won't give me access to the IDE drive.  I *need* that.
Got it all?  Good.  I hope it's as confusing and stupid for all of you as it is for me, that way I'm normal.

---

### Post by logos34 on 2007-08-14
> **fordexplorerdotnet said:**
> Excuse my lack of proper terminology, I'm a noob.  My original intention was to use my system's boot menu to boot either XP from my primary IDE drive or Ubuntu from the secondary SATA drive.  When I originally installed, I screwed something up and it stuck Ub on the same drive as windows.  I then disconnected the IDE drive and installed again, so then I was running Ubuntu fine on the SATA.  After trying to acquiece a way to just run Win4Lin b/c the wife requires Windows, I decided to reinstall it using my restore discs.
Now when I boot, I can go into Win fine.  However, if I use the boot menu to boot from SATA it gives me a boot error which is escaping me right now, I'll post it in a bit.  Regardless, I can't get to grub.  
I can use the install disc to access my data though, which is an important fact because I need to get to my backed-up data I copied to the SATA before wiping and install for win on IDE.  As you know, Win isn't going to see the SATA drive.  The install Ubuntu disc won't give me access to the IDE drive.  I *need* that.
Got it all?  Good.  I hope it's as confusing and stupid for all of you as it is for me, that way I'm normal.

Windows just overwrote Grub boot loader on the IDE drive MBR.  Grub reinstalled there when you put ubuntu on the sata.  

Actually you can access the IDE drive from the cd (even write to it if you dl the drivers) but it's a lot easier to do this:

boot into windows and download [fs-driver]("http://www.fs-driver.org/download.html").  It will allow you read+write access to your ext3 linux partitions on the sata.  Copy over all your backup files.  

Then you have two options: reinstall grub to the MBR of the IDE drive, or put grub on the sata drive and use the Bios to select the OS/disk your want to boot.

---

### Post by fordexplorerdotnet on 2007-08-14
Fs-driver seems to work like a charm, thanks!
I'm not familiar with how to reinstall grub, however.

---

### Post by fordexplorerdotnet on 2007-08-14
And now I've found that too.
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Greatest forums evar :bigthumb:

---

### Post by logos34 on 2007-08-14
> **fordexplorerdotnet said:**
> And now I've found that too.
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

yep, just do:

[B]sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit[/B]

---

