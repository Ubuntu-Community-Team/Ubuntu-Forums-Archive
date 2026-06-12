---
title: "Grub geom error when HDD order changed"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by stevesutt89 on 2011-11-16
Hi guys, 
So I have a netbook which I'm trying to get 11.10 on, I installed using the alternative installer running from an SD card. 

To boot from the SD card (or USB disk) I have to go into BIOS and make it the first HDD. The install went fine, so I rebooted, changed the first HDD back to my actual HDD in the BIOS. 

Now when I boot it, I just get:

> Geom Error

Reboot abd Select Proper device...

I assume that swapping the order of the "HDD"s has caused this error. 

Thus is there anyway that I can setup grub so that it expects the hard drive to be the first hard drive (even though its currently the second, according to the BIOS)?

---

### Post by efflandt on 2011-11-16
Which drive(s) did you actually install Linux on and did you specifically make sure that you put grub on that device as a manual partitioning option?  What does **sudo fdisk -l** (small L) show?

You also may want to post the output of the bootinfo script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) wrapped in code tags by highlighting that output and clicking the **#** symbol in Message window.  That should show if you accidentally put grub on your internal hd.  There are ways to restore a Windows MBR from Ubuntu CD or bootable USB (or other working installed system).

---

