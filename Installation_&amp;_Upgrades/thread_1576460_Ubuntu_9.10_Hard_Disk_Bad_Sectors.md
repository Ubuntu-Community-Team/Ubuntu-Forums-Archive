---
title: "Ubuntu 9.10 Hard Disk Bad Sectors"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by itsingleegfang on 2010-09-17
hey,
i have recently installed ubuntu 9.10 on my Windows XP.

On the completing the installation i got a error message 
"a hard disks may be failing one or more hard disk report health problem. click the icon to get more information"
so i clicked ok then clicked on the new hard disk icon on my panel with a "!" inside a yellow triangle, doing so "palimpsest disk utility" application comes up saying
Disk has many bad sectors

and then my pc freezes(hangs) (in just few seconds) hence leaving me with no other option than re-booting

i have searched for solutions relating it..but no success..

Is there any solutions to remove those bad sectors ..and i also heard from some that it is a BUG...


Plz Help!!

or else i have go for ubuntu 10.04..or so

PS: i  have installed ubuntu 9.10 three time(#failure)

---

### Post by Grenage on 2010-09-17
If the computer is actually freezing, it's unlikely a false positive.  Assuming that much, I'd replace the drive.

There's an outside chance that it IS a false positive, and that you have bad RAM (or other hardware) - but it's not likely.

---

### Post by mörgæs on 2010-09-17
Palimpsest used to have errors - I don't know if that is still the case. Anyway, I would rather download some diagnostics tools from the hard disk vendor.

---

### Post by SlugSlug on 2010-09-17
install 10.04

---

### Post by itsingleegfang on 2010-09-17
@Grenage

what do u think i should do??

---

### Post by Grenage on 2010-09-17
> **itsingleegfang said:**
> @Grenage

what do u think i should do??

Hi again.

**mörgæs**'s suggestion of a hard drive test would be a good first move.  You can rule out memory by running the memtest option in Grub; if you don't see Grub when the computer boots, hold down shift.

The problem with hard drives and bad sectors, is that they aren't usually 'one-offs'; you tend to keep getting more and more.  A manufacturer's test program will rule it out, assuming it runs on a boot disk, or Linux.

A _really_ basic test would be to boot with a Live CD and use it for a while, if there are no problems, you can probably rule out memory and most of the hardware.  You can then try writing and copying data on the hard drive, to see if it fails.

---

