---
title: "Neither usb hd nor internal drive boot after installing 10.10 to external drive"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by Rantsville on 2010-10-30
Have been using 8.04 for some time and wanted to try 10.10 before upgrading the 8.04 installation.  So burned a live CD and installed to my USB drive (250gb Seagate free agent go).  The USB will not boot on any of the computers in the house and the computer used to install 10.10 to the USB drive will not boot either.  Really don't want to lose the emails and bookmarks in the 8.04 installation but have been completely unable to install a functional GRUB.  Keep getting the "Minimal Bash" note and and "no loaded kernel" after typing "boot".

I'm more novice than anything but have been using ubuntu since Kubuntu 6.06 so this problem has really surprised me.

Insights will truly be appreciated.

---

### Post by mikewhatever on 2010-10-30
Two questions:
can your computers boot from USB, and if so, have you changed the boot order?
where is grub installed?

---

### Post by Rantsville on 2010-10-30
> **mikewhatever said:**
> Two questions:
can your computers boot from USB, and if so, have you changed the boot order?
where is grub installed?

Yes, they should be able to boot from USB.  Yes, I have changed the boot order a number of times since installing to the external drive.  Both of them I've tried to boot from are IBM T42 laptops.  Where's grub installed?  Not trying to be a wise cracker but I'm afraid saying sda1 makes it seem that way.

---

### Post by efflandt on 2010-10-30
Even when I wanted to put grub somewhere else (on sda4 instead of mbr) the setting for that did not jump out at me the first time I installed 10.10 release.  Although, in beta when I put root (/) on a usb drive, it defaulted to putting grub there.

But that may have changed in the release and if you did not intentionally put grub on the usb drive in the manual partitioning screen, it might be on the internal drive of the computer you used to install it to usb.

One problem I have had with grub2 even on usb is that with some computers it cannot boot beyond a certain point on a usb drive, but I have not determined what that point is.  For example even my new desktop PC cannot boot usb if grub is in the mbr and the Linux partition is at the far end of a 500 GB drive (which boots fine on 2 older laptops from 2006).  But it boots fine from the far end of a 160 GB usb drive or if the Linux partition is near the beginning of a 500 GB usb drive.  Even stranger is that the PC that cannot boot Linux at the far end of a usb drive is able to boot Linux at the far end of its 1 TB internal drive.

Another potential issue is that some computers cannot cope with partitions aligned to MB boundaries (default since 10.04) instead of cylinder boundaries.  I have an older desktop PC from 2004 with Asus motherboard with that issue.  But **partman/alignment=cylinder** kernel boot parameter (and/or making sure that you align partitions to cylinders) during install can get around that.

So those are some things that could trip you up.

---

### Post by presence1960 on 2010-10-30
Let's not use speculation here. We need to see exactly what you have on that machine & the USB disk. Plug the USB to the computer then do the following:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Rantsville on 2010-10-30
Yes, presence1960, someone that can look at the stuff and see what's what is exactly the ticket.  Only thing is it's nearly 11PM and at least two extra Newcastles more under the belt than advisable for tackling operating system issues or for that matter driving a vehicle.  So I'll refrain from both until morning when chances of screwing things up will be much lower.

---

