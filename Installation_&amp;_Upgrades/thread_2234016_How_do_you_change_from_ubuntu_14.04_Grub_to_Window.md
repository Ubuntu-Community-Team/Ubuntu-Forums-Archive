---
title: "How do you change from ubuntu 14.04 Grub to Windows 7 boot loader in dual booted PC?"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by William_Nyffenegge on 2014-07-12
Recently I installed ubuntu onto a computer that already had windows 7 on it. The computer now dual boots through the grub boot loader. Everything works fine, but from past experiences with linux partitions (grub was damaged and I had to reinstall windows), I would like to be able to boot using the windows boot loader and am wondering how to safely switch to that boot loader. I've heard that boot repair is risky and that easybcd can have errors.

So this is the question: what (safe) methods are there to switch to the windows boot loader from grub, and how should I go about doing those methods?

---

### Post by veddox on 2014-07-12
I don't know if you can use the Windows boot loader when dual-booting, since Windows doesn't recognizse ext3/4 partitions (assuming you have Ubuntu installed on one of those). So you might have to no choice but to stick with GRUB, if you want to keep you Linux system.

However, if I am mistaken, or you want to experiment about a bit, you can reinstall the Windows boot loader from the Windows repair DVD.

---

### Post by LastDino on 2014-07-12
You may able to do that using Easy BCD. I can not assure you about its safety though as I've better luck with grub and I actually like it. 

Btw, if ever grub is broken, it takes less than 2 min to actually boot into live DVD/USB and fix/reinstall it and everything is back to normal. And it is highly customizable, I'm not sure why you would want to go back to Windows bootloader. Nonetheless, I would wait for someone who has actually tried EasyBCD/ something else to go back to windows bootloader (which is highly unlikely, but oh well)

Also, I don't think  Windows repair will be safe method as it will probably screw your Ubuntu side.

---

### Post by oldfred on 2014-07-12
I do not recommend EasyBCD, but some that are primarily Windows users have used it. Most use grub2 and do not have issues or easily fix them on the occasion something happens.

EasyBCD uses a very old version of grub4dos to chainload to an install of grub2's boot loader to the partition boot sector or PBR. But grub2 does not correctly fit into the PBR, so it has to convert to blocklists or hard coded addresses. If a grub update or fsck moves any of the grub files on the drive the address is wrong and grub breaks. You then have to use Live installer to fix it. So if using EasyBCD you need current version of Ubuntu as live installer handy.

But you always should have a current repairCD or flash drive for every installed system anyway.

You will probably get this:
>  Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 



       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Bashing-om on 2014-07-12
William_Nyffenegge; In addition
To all the above:

If it is your desire to have the safest dual booting method for both Windows and ubuntu, then we are looking at dual booting from two distinct physical hard dives ! Windows installed onto the 1st hard drive (sda) with it's own boot code; ubuntu installed onto the 2nd physical hard drive (sdb) with ubuntu's grub2 Boot Manager and with grub, chainload Windows boot code onto grub's boot menu. One must set the boot priority to this 2nd hard drive to boot either OS, in the event of failure of grub ( and it only takes 2 minutes to re-install grub ), to boot up Windows just reset the boot priority to the 1st hard drive.

[INDENT][INDENT]best of all worlds, true dual boot
[/INDENT][/INDENT]

---

### Post by William_Nyffenegge on 2014-07-12
Thanks guys that helps. It sounds like I should just stick with grub and be ready to repair it if necessary. Don't have another hard drive to play with unfortunately, otherwise I would.

---

