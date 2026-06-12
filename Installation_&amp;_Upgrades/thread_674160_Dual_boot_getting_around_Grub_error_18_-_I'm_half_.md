---
title: "Dual boot getting around Grub error 18 - I'm half way there"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by doksoul on 2008-01-21
I saw in another forum a way around the dreaded bios limitation...error 18.  I'm trying to dual boot PClinuxOS and Ubuntu gutsy.  PClinux works great, I'm still working on Unbuntu.  The idea around the error is to create a folder in my PClinux boot directory for Unbuntu and copy the Kernel and initrd into it.  Set grub to boot from there and direct it to the other files for ubuntu.  Unbuntu root is hda5 and home is hda6.  Using this methodology I can get by the grub error and start booting Ubuntu, I get the splash screen and status loading line ...but eventually I get alot of errors.  Mainly that it cannot find files, so I think i need some help on redirection.  After loading the kernal and initrd, I figure I need to tell ubuntu where everything is...but don't know exactly what I need to edit in grub to make it work.  Can someone help me out here?  This is what I have in grub now.

title		Ubuntu 7.10, kernel 2.6.22-14-generic, Gusty Gibbon
root		(hd0,0)
kernel		/boot/Ubuntu/vmlinuz-2.6.22-14-generic root=UUID=75ab07ef-cc08-4792-ad5c-16b5456d958f ro quiet splash
initrd		/boot/Ubuntu/initrd.img-2.6.22-14-generic
quiet

I tried adding to the root=UUID line a lead in lke root=/dev/hda5=UUID...but just hands at the ubuntu splash.  I don't know what the UUID part is all about.

---

### Post by torgrot on 2008-01-21
It just tells it what partition to boot the image from.  What I would try is changing root (hd0,0) to root (hd0,4) and change root=UUID= to whatever the UUID is of the drive where the image is.

---

### Post by doksoul on 2008-01-22
I SOLVED IT.  Here's my new menu.1st grub file for Ubuntu.

title		Ubuntu 7.10, kernel 2.6.22-14-generic, Gusty Gibbon
root		(hd0,0)
kernel		/boot/Ubuntu/vmlinuz-2.6.22-14-generic root=UUID=b53eb15a-3b11-4c1b-9f06-adf8bdc523ba ro quiet splash 
initrd		/boot/Ubuntu/initrd.img-2.6.22-14-generic
quiet

First, I changed my partitioning to make this easier and reinstalled Ubuntu without boot mgr.  I installed Ubuntu in just one partition instead of my 2 (hda5 /,hda6 home).  I then went into /etc/fstab and viewed the UUID for root.  I then entered it into the listing above and walla...it works.  Couldn't believe it.

So for machines with old bios, mine is dated 2001, where you get the error 18 grub msg...You can put the kernel and intrid in a folder in your first (less than 8gb) partition and be able to boot to a 2nd OS...Dual booting!!!!

P.S. this round about way was necessary.  I had PClinuOS installed first with grub mgr and when I installed Unbunut and boot mgr., thinking it would just update grub and everything would work...it didn't.  I think its the bios limitation.  It buggered my menu.1st so I couldn't even load PCLinuxOS.  Lucky I had saved a menu.bak file.  So I booted with PCLinuxOS livecd and changed menu.bak to menu.1st and was able to boot into PCLinux and then do everything I said above to get it all working.

Now I know how install as many OS's as I want on this machine and make it work.

---

