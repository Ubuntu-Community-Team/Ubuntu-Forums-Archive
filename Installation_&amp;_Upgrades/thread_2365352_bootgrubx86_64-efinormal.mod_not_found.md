---
title: "/boot/grub/x86_64-efi/normal.mod not found"
date: 2017-07-05
forum: Installation &amp; Upgrades
---

### Post by legion-l on 2017-07-05
I understand what the problem is and how I got here, but I do not know how to fix it.

Some history:

I had Ubuntu 12.04 LTS factory-installed on my laptop.  I recently noticed that I hadn't gotten any updates in awhile.  I visited ubuntu.com and saw that 12.04 had reached end of lifecycle.  It recommended installing 16.04 LTS.  I downloaded the dvd image and attempted an install.  The install failed.

I rebooted into 12.04 LTS and did some further investigation.  I found that I can't upgrade directly to 16.04.  I also found that I had the option in the upgrade manager to notify of new versions of ubuntu turned off (I suspect from the factory).  I turned on the option and started the upgrade to 14.04 LTS.

When my laptop rebooted, I got the message: "error: unknown filesystem".  I did my research and figured out how to use grub.

I executed the following commands:
[INDENT]set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
insmod normal
[/INDENT]

I got this response:
[INDENT]error: file '/boot/grub/x86_64-efi/normal.mod' not found.
[/INDENT]

When I execute this command:
[INDENT]ls (hd0,6)/boot/grub

[/INDENT]
I get this:
[INDENT]./ ../ gfxblacklist.txt i386-pc/ locale/ fonts/ grubenv grub.cfg
[/INDENT]

So, I think what happened is that I tried to install the 64 bit version of 16.04 LTS, and now it is trying to boot into that, but can't find it.  I need to tell it to boot to (hd0,6)/boot/grub/i386-pc/, not (hd0,6)/boot/grub/x86_64-efi/.  I'm not sure how to correct this.  I've tried a few searches and haven't uncovered anything that worked.  Any advice would be much appreciated.

---

### Post by oldfred on 2017-07-05
Probably best to review report before trying any repairs. With multiple installs you have to use the advanced mode, not the auto fix in most cases.

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by legion-l on 2017-09-24
Life has gotten in the way of working on this.  I'm now getting back to it and I'm no further along.

I cannot get this computer to boot into anything.  I cannot run anything that is not available in grub rescue.

I need to make it boot using (hd0,6)/boot/grub/i386-pc/normal.mod instead of (hd0,6)/boot/grub/x86_64-efi/normal.mod (which does not exist).  I assume there is a set command for this?

---

### Post by legion-l on 2017-09-24
I tried: insmod (hdo,6)/boot/grub/i386-pc/normal.mod

And got: error: invalid arch-dependent ELF magic.

---

### Post by oldfred on 2017-09-24
error: invalid arch independent ELF magic 
 Often version of grub in MBR is not same as install. Or booting UEFI install in BIOS mode or vice versa.
Use same version to reinstall or chroot and fully uninstall & reinstall grub. Or use Boot-Repair.
But as posted before better to see summary report from Boot-Repair.

---

