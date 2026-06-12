---
title: "Installing Ubuntu with a Flash Drive"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by tylermenz on 2010-06-25
I am trying to install Ubuntu on an old computer that has really been giving me nothing but problems. The CD Drive does not work, so I decided to install through USB. After everything was good here on my Laptop, I put it in the old computer but it would just try to boot windows (which fails for some reason) even though I have it set to boot from USB First.

I went back in the BIOS and saw that the Flash drive was reading as a HD, and it was third on the list of boot options (below my primary HD and the one that came with the computer). It also wouldnt let me change the order that they booted in.

So I unattached both the HD's and booted again. Finally I got to the Desktop and started installing Ubuntu. Everything was going pretty good until I got to Step 4 of 8 on the installer: Preparing Partitions. Nothing shows up in the partitions box, and even after I hook up the other HD's its still blank.

The computer is an old Everex and it doesnt boot up at all anymore, regardless which HD I put in it. Has anyone else had this problem? I would like to just completely reformat since there was nothing important on the HD anyway.

The Error that it is giving me is:

X  No Root File System
   No Root file system is defined
   Please correct this on the Partitioning Menu 

unfortunately the "New Partition Table", "Add...", "Change" "Delete" and "Revert" buttons are all greyed out and unusable.

---

### Post by C.S.Cameron on 2010-06-25
I think the HD needs to be plugged in before booting the USB.
One of my computers is difficult for making the flash drive the first hard drive, over on the side on the BIOS screen it says I need to press enter then use the plus minus keys, on some computers it is the page up and page down keys and on others it is the up and down arrows.

---

### Post by oldfred on 2010-06-25
Have you run chkdsk on the windows partition?

I could not get gparted to open my sda drive with windows, even though I knew windows worked. It turned out there were a lot of errors and after I ran chkdsk in windows gparted would open it immediately.

---

### Post by tylermenz on 2010-06-26
I finally got it to work. I did have to have the drive plugged in and just had to use the other +/- keys on the keyboard in order to change the boot order.

Know I just need to figure out how to Plug in one of my other HD's and duel boot the computer. 

Thanks Guys

---

