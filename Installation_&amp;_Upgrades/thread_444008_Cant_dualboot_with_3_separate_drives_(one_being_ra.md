---
title: "Cant dualboot with 3 separate drives (one being raid 0)"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by dvazriel on 2007-05-14
Okay i have tried the whole weekend and still cant get it to work.

I have a 2 drives doing raid 0 (jmicron driver). I am dualbooting Vista and XP, using Vistas bootloader. Everything works great. I installed ubuntu on a 3rd single sata hardrive. Everything works installs great, its installed in /dev/sdc1. ( since ubuntu sees it as the 3rd drive ).


I install grub in the root partition

root(hd2,0)
setup(hd2,0)

then extract the bootsector with sudo udo dd if=/dev/sdc1 of=mbr.backup bs=512 count=1
and then copy it over to the Ntfs partition ( im pretty familiar doing this, been doing it since my Redhat days )

The problem is, it doenst work. I use easybcd and add the Linux entry, replacing the default one with the one i extract. When i chose the entry, it get a blank screen, then kicks me out back to the boot menu.

Some things i found out.

Windows see the single drive as drive 0, and the Raided drives as drive 1. Linux sees the Raid drives first, then the single one. 

Windows see two drives ( raid 0 and single ) while Linux sees 3 drives. I never got dmraid to work.

I installed ubuntu and Vista in the single sata drive, follwed the exact procedure and it worked flawlessly. So booting ubuntu from the SAME drive works fine.


I dont think grub loader will work here, since im assuming grub doenst have support for fakeraid builtin, so im assuming grub wont be able to boot windows since they are both in the raid drive.

Im using 7.04

Any more ideas?

---

### Post by Computer Guru on 2007-05-15
What happens if you *don't* replace the default nst_grub.mbr with your dd'd one?

---

### Post by dvazriel on 2007-05-15
Same thing.

I ended up "fixing" it, although its more of a rig.

Scenarios: 
Since i know grub will not be able to boot my raid0, the only bootloader that i can use was the Vista loader. 

Vista loader, when installed in the MBR of my raid drive, fails to boot ubuntu.

I can only boot ubuntu and Vista if BOTH were installed in the same single SATA drive.

WIth this in mind i installed ubuntu again in the SATA drive, then left space in there to install a "dummy" Vista.  I then proceed to setup dualbooting using the Vista loader (the dummy vista ) and using easybcd to add Linux. I also changed the BiOS so that the SATA drive is my primary boot harddrive.

Now that this works, i just added my entries for the "good" Vista and XP, both from my RAID drive ( although i can still boot from this drive if i choose to in the bios )


So basically the bootloader is installed in the MBR of the SATA drive, not the RAID drives.

---

### Post by Computer Guru on 2007-05-16
Glad you got it to work, just a quick question:

So you're saying that the Vista bootloader *can't* by on a RAID if you want to dual-boot Linux - and that Ubuntu (or at the very least the /boot partition) has to be on a non-RAID partition as well?

---

