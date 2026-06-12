---
title: "Remove ubuntu (temporarily!!)"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by MG&amp;TL on 2011-07-11
Recently I wanted to remove Ubuntu from a dual boot with Windows7. Don't panic, Ubuntu-ers, it was just a temporary measure, I wanted to try kubuntu (live cd is VERY slow) and it didn't seem to have an option to install over ubuntu.

Anyway, the only way I could think of was to make the partition 'free space' in the windows disk management bit. Unfortunately, doing this or making it unallocated space causes a problem.

On reboot, laptop hums for a bit and then gives me:
error:no such partition
grub rescue>
(command line)

I didn't know enough about command lines, BIOS, and all that to recover anything, so I re-installed Ubuntu via cd, selected 'alongside windows' and ran the installer. Now worked fine, windows booted, ubuntu booted, happy days. :D

BUT- three questions:

-Why does it do that? I'm assuming grub stays behind and then can't find the partition? How do I avoid doing it again? (Scary, new laptop!)

-How DO I remove 'buntu?

-Could I save myself the hassle, is there an option to install over ubuntu in the kubuntu menu?

---

### Post by Lars Noodén on 2011-07-11
You can install over the old Ubuntu installation without disturbing anything else.  In the section where you are partitioning the drive, choose manual and then point the installation at the old Ubuntu installation.  That will write over the old installation.

---

### Post by MG&amp;TL on 2011-07-11
There was nothing in 'manual install' as in, it returned a blank white, framed, nicely done kubuntu screen. But still no install option. And I checked the disk and it returned no errors. I just assumed manual was a command-line, and you needed to know some shortcuts to get it to work.

Thanks for input, I shall re-load cd and see if it's there. :D

---

### Post by Mark Phelps on 2011-07-11
Yes, GRUB stays behind -- in the MBR.

If you ever want to restore the original Win7 MBR, you should go into Win7 (while it still works), and use the Backup feature to create and burn a Win7 Repair CD.  That can be used later to restore the original MBR.

---

### Post by Lars Noodén on 2011-07-11
It'll be there in the partitioning menu, when you get to that.

---

### Post by MG&amp;TL on 2011-07-11
Oh, thanks people, I'll get around to burning the cd sometime when I'm actually using Windows.:D

---

### Post by Lars Noodén on 2011-07-12
> **MG&TL said:**
> Oh, thanks people, I'll get around to burning the cd sometime when I'm actually using Windows.:D

You can burn CDs in Ubuntu with K3B or Brasero.

---

### Post by MG&amp;TL on 2011-07-12
I meant the Windows recovery cd. I imagine it's possible to burn a windows recovery cd in ubuntu, I just won't remember while using ubuntu. :)

---

