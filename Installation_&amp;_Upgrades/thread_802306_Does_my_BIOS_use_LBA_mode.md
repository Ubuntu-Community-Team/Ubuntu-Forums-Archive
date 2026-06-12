---
title: "Does my BIOS use LBA mode?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Crossroads on 2008-05-21
I hope someone can sort me out.

I have read that some older BIOSes can only access the first part of a hard disk. So when the /boot partition (or / (root) partition if there is no /boot) is installed it must be in the first 8GB (approx) of the disk. Elsewhere I recall reading that the whole partition must lie within this 8GB.

This is because the older BIOS uses CHS (Cylinder, Head, Sector) addressing to access the bootable partition. More recent BIOSes uses LBA (Logical Block Addressing?) to access the complete disk (up to 128GB anyway I think) and so avoid this problem.

It is not really practical for me to create space for /boot in the first 8 GB on my Windows XP PC so I would lke to ask: 
a) how can I check whether my BIOS has this constraint?
b) it looks like the GRUB installation Stage 2 error #18 reports this problem; are any irreversible disk changes done by this point or does GRUB reverse out all the changes? 
c) I would think that a Wubi Install bypasses this problem completely as the Windows boot loader ntldr is used and boot.ini is modified); is that correct? 

I've tried a few forum searches but have not been able to pick the right words to get relevant threads.

---

### Post by logos34 on 2008-05-21
> **Crossroads said:**
> 
a) how can I check whether my BIOS has this constraint?
check your pc/motherboard manufacturer web site (driver downloads/bios updates page).   Generally the 1024 cylinder limit is something that is found on older boards, ca.1999 or earlier

> 
b) it looks like the GRUB installation Stage 2 error #18 reports this problem; are any irreversible disk changes done by this point or does GRUB reverse out all the changes? 

You can simply overwrite the MBR by restoring the windows bootloader if need be. 

> c) I would think that a Wubi Install bypasses this problem completely as the Windows boot loader ntldr is used and boot.ini is modified); is that correct? 


I believe that's correct.

Alternatively, you might try using windows bootloader to boot ubuntu with [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html").

---

### Post by Crossroads on 2008-05-22
Thanks for your reply.

The Mobo is ASUS A7N8X Deluxe, the BIOS Phoenix Award v6.00PG 03/19 and the hard disk is a Maxtor 120GB (from early 2003, I reckon). The disk  is IDe and the mode in the BIOS is "Auto".

I've searched the AUSU and Phoenix sites but have not found the required details.

So GRUB will have overwritten the MBR before detecting any CHS/LBA problem. Ah well. I don't have an Xp installation idsk but the OEM supplied a Recovery/Support disk and there is a Recovery partition on the hard drive. [I explored that a bit from an Ubuntu Live CD boot.]

I'll take another look at Wubi too.

---

### Post by logos34 on 2008-05-22
> **Crossroads said:**
> Thanks for your reply.

The Mobo is ASUS A7N8X Deluxe, the BIOS Phoenix Award v6.00PG 03/19 and the hard disk is a Maxtor 120GB (from early 2003, I reckon). The disk  is IDe and the mode in the BIOS is "Auto".

I've searched the AUSU and Phoenix sites but have not found the required details.

So GRUB will have overwritten the MBR before detecting any CHS/LBA problem. Ah well. I don't have an Xp installation idsk but the OEM supplied a Recovery/Support disk and there is a Recovery partition on the hard drive. [I explored that a bit from an Ubuntu Live CD boot.]

I'll take another look at Wubi too.

I took a look at your board specs and I don't think it's a bios limitation issue.  Error 18 can occur for other reasons.

Try the suggestions [here]("http://users.bigpond.net.au/hermanzone/p15.htm#18"). (check cables, set Bios explicitly for LBA mode instead of Auto, etc.)

You can also reinstall windows bootloader with [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

You may have missed the last line in my post above.  Try Wingrub.

If it turns out that you do in fact need to use a separate /boot at the frn tof the hard disk, you can shrink the windows partition using Gparted (which hopefully won't screw up XP boot)

---

### Post by Crossroads on 2008-05-24
Thank you.

I had a bit of a look around the BIOS. When I changed the IDE mode away from "Auto" the cylinder and head values that it displayed changed. But the values shown for "CHS" mode were the same as shown for "Auto" mode. So it looks like I do have the 8GB constraint here. [I don't fancy a BIOS update.]

I'll look at shrinking C:\ but there may be too much already in there. [I just checked: excluding Docs & Settings, there is 6.5GB used, and there is a hidden Recovery partition of 2.5GB in front of it - so no go :(] 

Alternatively, there is alwys Wubi or, my preference for the long term, WinGrub.

---

