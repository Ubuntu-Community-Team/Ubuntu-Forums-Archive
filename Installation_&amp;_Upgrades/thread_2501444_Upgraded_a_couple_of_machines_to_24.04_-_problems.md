---
title: "Upgraded a couple of machines to 24.04 - problems"
date: 2024-10-07
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-10-07
I have been trying to install 24.04 into two machines.  I am now setting them up but there are problems.  This is about that.

I have functional other machines and I am trying to set up the two I just upgraded.  One thing that I am doing is copying stuff from one that is functional to include in the two I just did.  I am copying this stuff on a memory stick (31gb) and then putting that stick into the new ones to copy what I put on the memory stick.  My problem is that, when I put the stick into the other machine, even when Discs sees the stick and logs it in properly, etc. I cannot get to the stick as files doesn't recognize it which means I can't do what I wanted to do and something is wrong.  My files file, for instance, is a bit strange.  It has, for instance, "desktop" with nothing in it.  It has several other things which also have nothing in them and some do not exist.  I have no idea what is going on.

Thoughts?

---

### Post by ubfan1 on 2024-10-07
What filesystem is on the USB (are drivers for that fs available on both machines?)? How did you do the copy?  Any error messages (like maybe complaints of a read-only filesystem)?

---

### Post by grahammechanical on 2024-10-07
> My files file, for instance, is a bit strange.  It has, for instance,  "desktop" with nothing in it.  It has several other things which also  have nothing in them and some do not exist.  I have no idea what is  going on.

I am on Ubuntu 24.04 and Files>Documents is empty. As is Music & Pictures & Videos. This is because I have not put any files into those folders. I have a partition for storing those kind of files.

The Desktop folder has a file in it. That is because I have installed a Windows program under WINE that puts an icon on the desktop. Otherwise, Files>Desktop would be emplty also.

As for accessing a USB memory stick it should appear in the left hand column of Files. Another place to look is + Other Locations. The memory stick that I am using has a Ubuntu ISO image on it. So, Files does not have any problem seeing the USB stick. 

The suggestion of @ubfan1 may have the solution.

Regards

---

### Post by jgw on 2024-10-08
Thank you for the reply.  

There is a lot of stuff that just makes no sense on this machine.  I am considering simply re-installing and my only question is "with what?"  Anyway, here are some problems.  I did check on the file system.  It had a problem.  I fixed it, Changed nothing.  I restarted and did that again, It had a problem. I fixed it.  Changed nothing again.  When I started the machine.  When it starts it says that failed to open /efi/ ubuntu not found (efi is the first partition on the sdd which is the sole disc on the system.  Will not restart and it will not power down.  It is no longer booting, ubuntu comes up but it eventually gets to a black screen - forever.  The is more stuff but I think its really time to re-install.

---

### Post by jgw on 2024-10-10
its just too easy!  I have NOT payed attention (yet again).  The trick was to get to the boot of the bootable and then tell the computer what boot file to use.  I had two machines to deal with.  One was an intel machine and the other was an HP machine.  The HP machine was actually harder as it was faster and was difficult to get to the place but the Intel was a bit slower and I was able to press the f2 key which took me to the list of boots and I choose my bootable and that did the trick.  

The real trick is the actually read, carefully, when you are being told how to do what you are trying to do.  I am only 89.  Just to damned young to pay attention!!

---

