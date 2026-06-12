---
title: "Ubuntu menu option does not show up in Grub"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by dominiquec on 2010-06-10
I've had two students report a problem whereby Ubuntu does not show up as a menu option in Grub.  Both systems used Wubi installations of Ubuntu 10.04 Desktop for x86 on Windows XP.

Can anyone recommend a fix?

In both cases, Ubuntu completed the installation process.  Upon reboot, we have the options to choose between Windows XP and Ubuntu.  However, once we enter into Grub, only the Windows XP option shows.

I tried searching for answers but somehow I can't think of search terms that would bring back specific results.

---

### Post by darkod on 2010-06-10
It's a bit confusing to talk about grub when using wubi because it doesn't actually use grub, not in the way a full dual boot install does. Some people even mistakenly call the windows bootloader grub.

With wubi install you are still using windows bootloader from your MBR of the disk, just it has added entry for ubuntu/wubi.

After you select wubi, it shows grub but not from your MBR. If that makes sense. :)

So, in windows bootloader you do have entried for XP and wubi, right? And after selecting wubi in the second boot menu (grub from wubi), it shows only XP? Does that mean you can't boot wubi/ubuntu at all?

---

### Post by dominiquec on 2010-06-10
Okay, thanks for that correction.  I'll have to review my terms.

Setting the terminology aside, then, this is the problem:

At bootup, the selection menu shows "Windows XP" and "Ubuntu".

After selecting "Ubuntu", it just shows "Windows XP."  It does not show the Ubuntu options (with corresponding kernel choices) at all.  It does not even show the Memtest options.  Just "Windows XP."

Selecting "Windows XP" brings me right back up to the first menu.

---

### Post by darkod on 2010-06-10
Very strange. Haven't heard of that before. And since this is a wubi install, it doesn't have its own partition, I don't even know where to start. Wubi works from an image file on the disk and everything is inside. Which makes it possible to look inside, but not in a real easy and straightforward way. :(

And I don't use it so know very little about it.

---

### Post by oldfred on 2010-06-11
I do not know anymore than Darko on wubi. One of the problems is that those volunteering to help are not wubi users. Wubi is for those windows users that want a longer test than using the liveCD. It is a full install but in a file on the windows NTFS partition. Makes it easy to uninstall.

Even the creator assumes you will convert to a full partition within 6 months.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

You can run the boot info script as it does try to parse data inside the wubi install.  This may tell us something similar to a normal install, but I am not sure we know how to fix it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by dominiquec on 2010-06-11
While I suppose any response is better than dead silence, I was hoping for something more than what amounts to "use something else."

Just so you understand my situation: I teach in a university with an IT staff that's hostile to Linux.  I cannot install Ubuntu in a dedicated partition.  Wubi gives me a way to work around that.

So far I have introduced over 250 students to Linux in a semestral course that works with Ubuntu as the main platform.  We have problems, yes, but we work around them.  I would say 95% of the time, wubi works for our purpose.  In fact, wubi was generally  all right up until 9.10 when we had problems introduced through updates; and now this.

It's not even an issue with all the other installs, just with a couple.  I'm curious to know why, and if anyone else has run into the same thing.

(I will try the bootinfoscript, though.)

---

### Post by oldfred on 2010-06-11
Flash drives are relatively cheap now and you can do a full install in 8 or 16GB USB flash drive. If you computer will boot USB it is a way to use Ubuntu without changing the windows install at all.

---

### Post by darkod on 2010-06-11
> **oldfred said:**
> Flash drives are relatively cheap now and you can do a full install in 8 or 16GB USB flash drive. If you computer will boot USB it is a way to use Ubuntu without changing the windows install at all.

+1

Just make sure you clicked on Advanced in the last installer screen and select grub2 to be installed on the usb stick. Otherwise it can usually go to your int hdd MBR and the computer can't boot anything without the stick plugged in.

Sorry about the lack of knowledge/support for wubi. Not having ubuntu in grub2 sounds like no kernels are present maybe, but I have no idea how to look into the root.disk image file or install kernels inside it.
You can mount it like loop device (or called similar, not sure), but I don't know the exact procedure. If you feel like it, maybe google can help to check how to mount wubi image disk.

---

### Post by oldfred on 2010-06-11
I have saved some info on wubi just because the issue keeps coming up, but most is with 9.10 and from meierfra who was testing his script with wubi and found some errors in 9.10


[Script] Mount Wubi Disk from Linux 
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

The script will possibly tell us more.

---

