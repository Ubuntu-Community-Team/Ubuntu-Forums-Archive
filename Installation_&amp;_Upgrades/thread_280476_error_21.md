---
title: "error 21"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by zoomwest on 2006-10-19
After installing Ubuntu on my secondary Hard drive (XP Pro on primary) I get an "Error 21" message right after the Grub Loading, please wait notice.  How do I get back to be able to boot XP, and then how do I get Ubuntu to run off the second drive?

It is NOT a bios issue.  Turns out after some research this is a very common problem, and the link provided in the first response to my post has good advice which I will try, but for now XP is back.

Thanks to all.

---

### Post by gn2 on 2006-10-19
You could re-install Grub using Super Grub Disc and see if that cures it.
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Or you could run fixmbr from the recovery options after re-booting the Windows install CD.

This thread may interest you: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by bulldog on 2006-10-19
Error 21 means:

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Can you put the output of ```
sudo fdisk -l
``` l as in like.

---

### Post by az on 2006-10-19
> **bulldog said:**
> or not recognized by the BIOS in the system.
.
If this is on an older computer, it is likely that the motherboard bios cannot see the second hard drive (or it can't see all of it).  Grub does not run in linux, it does not benefit from the ability the linux kernel has to access the hardware.

Your bios is pretty primitive in this regard.  On some older machines, for example, the bios cannot see more than the first few gigs of a hard drive  (that does not prevent the linux kernel from seeing it, though).  The solution is to install grub to a portion of the hard drive that can be seen by the bios.  Ususlly, you create a small boot partition at the beginning of the drive and mount your /boot directory there.

Grub and the linux images can be found there.

---

### Post by bulldog on 2006-10-19
Well I use this site to look up errors and don't know them by myself.

So if this is not correct,it's a pity :D 

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

---

### Post by h4rdwire on 2006-10-19
Did you check in bios if it isn't even recognized?, if you have another harddrive try if that one works....or with your IDE just swap the setup just to do some harmless tests.

-Check bios if its even detected
-Try plugging in the 2ndary harddrive as the primary on the IDE ribbon and see if it works alone...

and if you have an IDE drive, master/cs/slave jumppers?

update us on progess...!

---

