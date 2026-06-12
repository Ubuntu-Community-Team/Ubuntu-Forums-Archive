---
title: "Installation with existing Grub"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by KnevetS on 2006-11-14
I have an existing SUSE installation on my desktop set up with Grub so that I can switch between windows and SUSE on boot.

I never use my SUSE installation because I ran into extreme difficulty getting my dual monitor setup to work.

I have tried the LiveCD, and from what I read I see promise that I could get my ATI 9500 up and running properly with ubuntu.

I want to overwrite my SUSE installation with ubuntu, but I am afraid that I will end up killing grub and rendering Windows difficult to find.  Although I would love to just never use Windows anymore, I know I'm going to still need access to it.

Are my fears without foundation?  Or is there any way that I can ensure that this won't happen during installation?

Or is my best bet to go in to SUSE, back up /boot and just edit some files after the fact?

---

### Post by davec64 on 2006-11-14
Hi,
Whilst I'm no expert! i've sucessfully done what you require!

From within Windows I deleted the Linux Partitions using Partition Magic (any partition manager will do). This isn't actually necessary as during the installation of Ubuntu you can use GPARTED to sort out you partitions (or even from the Live CD). This created free space on the disk.
Secondly I used a windows 98 boot disk and ran FIXMBR which removed GRUB. I later found out that this isn't strictly necessary as the new Ubuntu installation would have reinstalled GRUB.
I then proceeded to install Ubuntu which subsequently installed GRUB and picked up the Windows installation.

Hope this helps! 

All the best

---

### Post by KnevetS on 2006-11-14
And whadya know!  I used GParted to erase/recreate my SUSE partitions during the installation and everything went smooth - although my system did lock up once during the install which freaked me out since it was after I deleted the partitions but before the new ones were created!  I simply let it boot with the liveCD and everything went great the second time around.  No SUSE on the grub menu (which was desired), and it found my Windows installation no problem.

I didn't have to resort to FIXMBR or anything like that, although I did prepare myself just in case.

Funny how easy this is compared to a Windows OS install.  Took about 10 or 15 minutes and I was up on the web downloading display drivers.  The funny thing is that I started up a game of nibbles to occupy my time during the install.

---

### Post by davec64 on 2006-11-15
Glad all went OK!

I've got to admit my approach was real 'belt and braces' job!

The install is unbelievable compared to windows!

---

