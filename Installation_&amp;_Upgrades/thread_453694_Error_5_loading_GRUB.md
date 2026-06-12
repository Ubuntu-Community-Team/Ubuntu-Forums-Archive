---
title: "Error 5 loading GRUB"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by djen9999 on 2007-05-24
I was helping a friend install a dual boot with Feisty and XP and everything went fine during the installation.  After the installation we did a reboot and got an error 5 just as the GRUB was loading.  There were no other details and I don't know what an error 5 is so I don't know how to help.  Right now it wont boot anything.  I can't even access BIOS.

Where do we go from here?

---

### Post by merlinus on 2007-05-24
I do not know if this will help, but here is the definition of grub error 5:

5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

-merlin

---

### Post by djen9999 on 2007-05-24
At least I know what it is even if I don't fully understand it.  Does anyone have a solution?

---

### Post by psusi on 2007-05-24
Can you give a complete system description?  What kind of hardware, how do you have the disk(s) partitioned, etc?

---

### Post by djen9999 on 2007-05-24
As I said, it was my friend's system but I'll give you what I know.  It's an older Gateway with bare minimum memory about 256 Meg.  The hard drive was partitioned one for OS  one for programs and one labeled Ghost which I assumed was a recovery.  There was approximately 2 gig free on the OS partition.  I double checked that the OS partition was the one we used.  I'll provide any other information you might need if I don't have the answer, I can get it.

---

### Post by djen9999 on 2007-05-25
I get the impression that this is the fault of an older BIOS and too many partitions.  Does anyone think it would be possible to mount his hard drive in a newer system with an up to date BIOS and at least salvage Windows?

---

### Post by psusi on 2007-05-25
> **merlinus said:**
> I do not know if this will help, but here is the definition of grub error 5:

5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

-merlin

I am not sure where you got this definition from, but the grub documentation defines error 5 as "Partition table invalid or corrupt".  This is not a good sign.  

Can you post the output of sudo fdisk -l from the livecd?

Also, you can try to recover your windows installation by booting from the windows cd and running the fixmbr command in the recovery console.

---

### Post by merlinus on 2007-05-25
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

But perhaps this page is more accurate???

[http://linspirenetwork.gigastrand.com/support/gruberrors.htm](http://linspirenetwork.gigastrand.com/support/gruberrors.htm)

-merlin

---

### Post by psusi on 2007-05-25
Yes, the latter page seems to agree with what the grub documentation in ubuntu and on grub's web site say.

---

### Post by djen9999 on 2007-05-25
We can't boot from the Ubuntu live CD.  BIOS doesn't seem to recognize the CD drive at this point.  It TRIES to boot from the HD but we get the error message before the GRUB loads.  I'm sure we'll be in the same fix with the Windows CD (If he can even find it ;) )

---

