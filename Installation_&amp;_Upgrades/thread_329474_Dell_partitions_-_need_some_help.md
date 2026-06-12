---
title: "Dell partitions - need some help"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-01-01
Have run across several threads recently where people were having trouble with partitions.  Dell seems to be the root of the problems.  Apparently Dells come with at least 3 partitions, a utility partition (function unknown to me), Windows, and the recovery partition.

-Where are these partitions located physically and how are they formatted? (primary, extended, etc.)

-If you have a Recovery Disc, can you vaporize the recovery partition?

-What about the "Dell utility" partition?  Can it be removed?  

-What would happen if you wiped a HDD entirely, then set up a primary NTFS partition for Windows, two primaries for Linux, and an extended for swap, FAT32, whatever.  Can you then use the Dell recovery CD and install all of it to the one NTFS partition?  Wouldn't it try to build more partitions within that partition, making a mess of things?

Any help would be much appreciated!

---

### Post by adaptr on 2007-01-01
> **Bartender said:**
> Have run across several threads recently where people were having trouble with partitions.  Dell seems to be the root of the problems.  Apparently Dells come with at least 3 partitions, a utility partition (function unknown to me), Windows, and the recovery partition.

-Where are these partitions located physically and how are they formatted? (primary, extended, etc.)
That is not very important; the important factoid is whether the recovery partition is located **before** or **after** the Windows partition.
If it is located after the Windows partition, your chances of successfully resizing Windows may shrink to 0 (zero).

> -If you have a Recovery Disc, can you vaporize the recovery partition?
Certainly - they contain the exact same data.
A few upgrades may have been applied to your on-disk image, as that tends to be newer than the CD, which is not upgraded every time they install a new Windows image.
But the differences will be small - mostly drivers you can get from the Dell site with minimal trouble.

> -What about the "Dell utility" partition?  Can it be removed?  
Usually not without losing the ability to boot Windows - at all.
The "utility" partition is a small DOS partition used to store BIOS setup programs and RAID setup software and the like.
It does double duty as your actual C: drive, so this is where Windows boots from - it is where the boot loader lives.

> -What would happen if you wiped a HDD entirely, then set up a primary NTFS partition for Windows, two primaries for Linux, and an extended for swap, FAT32, whatever.  Can you then use the Dell recovery CD and install all of it to the one NTFS partition? 
No, you can't.
The Recovery option (whether from CD or from disk) completely wipes the HD and re-installs what you had when you bought it.
All your personal data, e-mail, Ubuntu, whatever - **gone**.

>  Wouldn't it try to build more partitions within that partition, making a mess of things?
Not really - you'll end up with a very clean, completely Ubuntu-free Windows installation :)

The very first thing I'd do with a new, Windows-infested laptop would be exactly what you describe.
Install Windows on max. half the hard drive, choosing the partition size during installation.
Then install Ubuntu after Windows, using as many partitions as you need.
One root, one home, some swap, and a small FAT32 transfer should be enough - you'll need logical partitions for this, but that's hardly a problem these days.
I'd install Windows in Primary partition 1, some swap right after that, and make the rest an extended partition with whatever partitions you want for Ubuntu.

---

### Post by HarrisonHopkins on 2007-01-01
This is exactly how they are set up on my Inspiron E1505 with MediaDirect. I'm looking at them through GParter

50MB FAT16 partition at the very beginning - Utilities
Windows Partition NTFS
2GB Extended Partition containing a FAT32 partition - MediaDirect, I'm guessing
5GB FAT32 Partition - System Recovery more than likely.

---

### Post by Bartender on 2007-01-01
Thanks, guys -
That helps me get a picture of what's going on under the hood.  I don't have a Dell, and don't want one after reading about this nonsense.

EDIT:  So, Harrison, have you installed Linux?  If so, where did it go, and how'd you do it?

---

### Post by HarrisonHopkins on 2007-01-03
Yes, I have Kubuntu installed. Using a Gparted Live CD, I shrank my Windows partition from 105GB to 80GB, leaving me with exactly 25GB free, unpartitioned space to put Kubuntu on. I started up the live CD, went through the install directions, and installed it to the largest contiguous free space.

The 25GB went into the extended partition.

---

### Post by Bartender on 2007-01-03
So the installer was smart enuf to 

1) Figure out you had no more primary partitions to spare
2) Create extended space instead and set up Ubuntu completely inside of that?

Don't know about you guys, but I think that's pretty amazing.  The default Ubuntu install is / in a primary and swap inside extended.  

All Dell has to do is come up with one more stupid partition and Ubuntu will be locked out unless the user is willing to delete something.  Microsoft and Dell are probly working on that already :evil:

---

### Post by HarrisonHopkins on 2007-01-03
I don't really know what it did, but it worked. Perfectly, at that.

---

### Post by themusicwave on 2007-01-03
I have the same laptop and I wiped all the partitions when I did my ubuntu install.

Here is what will happen if you do this:
The Media Direct button will stop functioning - not a huge deal, no idea how to fix it.

Dell diagnostics will no longer work - you can burn an ISO from Dell's website to run the diagnostics so it's ok.

Those are the problems I have noticed so far, not all that big of a deal.  Everything still works just fine for me(except the mdeia direct feature).

---

### Post by Bartender on 2007-01-03
Hey, thanks guys -
harrison, got a favor to ask of you.  Could you please toss an UbuntuLiveCD in, bring up the desktop, plug in a thumbdrive, open Gnome Partitioner, take a screenshot, save it to the thumbdrive (it should show up as one of the devices to save to right after taking the screenshot), go to the USB icon on the desktop, right-click on it and Eject the thumbdrive to make sure it saves the data, then close out of the LiveCD, then attach the screenshot to a reply?

I'd *really* like to see what your partitions look like.  I'm saving this info for future reference when a Dell owner can't figure out what to do with his/her partitions.  A screenshot would be awful handy.

---

### Post by HarrisonHopkins on 2007-01-03
Sure, I'll give it a shot. I'll edit this post once I have it done. About 30 minutes, I'm writing my resume right now.

---

### Post by Bartender on 2007-01-03
Harrison -
Your input may already be helping a guy with an HP.  Similar problem with all those factory-installed partitions
[http://www.ubuntuforums.org/showthread.php?p=1964190#post1964190](http://www.ubuntuforums.org/showthread.php?p=1964190#post1964190)

---

### Post by HarrisonHopkins on 2007-01-03
That's good to know that it might be helping someone.

Anyways, here is the screenshot. The partitions look a bit funky. I just reinstalled Kubuntu for the 3rd time. Grub doesn't like deleted partitions, it seems... I will take another screenshot once I get Kubuntu working like it was again, this time it should be a much better one.

I'm thinking of completely redoing this hard drive... I'm not sure though.

Edit: The continuous option appeared in Kubuntu though. Not sure if Ubuntu uses the same installer.

---

### Post by Bartender on 2007-01-04
Thanks for taking the effort to post the attachment.  I appreciate it.  I'm starting a new folder on my PC for screenshots.  I think they'll come in handy as a reference for myself and for others who post on the forums.

Can you go back and delete the two swaps, then combine them into one?

---

### Post by HarrisonHopkins on 2007-01-04
Ok, I will do that. Is there a partitioner in Kubuntu? It would be easier since I have it installed.

---

### Post by Bartender on 2007-01-04
The Kubuntu install CD will have Gnome Partitioner under System>Administration.  The finished install doesn't have it.  You can't modify a mounted partition so you'd want to do this from a bootable CD anyway.  

So your best bet would be to go back in with the Kubuntu install CD or download GParted LiveCD .iso and make a bootable CD.

I tried this at home the other day; you can go all the way to the partitioner, then just abort the install, so don't worry about getting too far in with the install CD.

GParted LiveCD is a better option if you can download it.

EDIT:  I don't know if you found this out already.  If you click directly on the swap section in the map, it won't do anything.  Try clicking on the text part below.

---

### Post by ndpete on 2007-01-04
I have an E1505 also and all i did was just wipe the entire hard drive. like themusicwave said only lost the media direct function. since i never used it before its not a very big loss. i just wish i could map that key as a shortcut.
I've had no problems with this set up at all. for a while i had it triple booting XP, Vista, and Ubuntu but have since dumped Vista.

---

### Post by HarrisonHopkins on 2007-01-04
Ok, I got the new picture with it correctly done. Went ahead and completely reinstall Kubuntu, but it fixed it.

I hope the Dells I might be getting from my school don't have these extra partitions....

---

### Post by Bartender on 2007-01-04
Thanks, Harrison - 
Saved the new screenshot too.  I think the extra partitions are pretty much standard for Dell at least and some of the other big box manufacturers too.
Sounds like you could dump the recovery partition at least as long as you have a Recovery CD...

---

### Post by HarrisonHopkins on 2007-01-04
You probably could remove it, but then you would just have a 4GB empty space at the end of your drive. The only thing that you could expand to use it would be the Mediadirect partition.

---

