---
title: "Grub problem after windows 10 update"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by choinul on 2015-08-08
Hi everyone,

I just updated windows8 to windows 10 on a system with windows8 and Ubuntu and I obtain a grub rescue terminal :
Error: unknown filesystem.
grub rescue>

I succeeded to access the grub menu by typing
set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
insmod normal
normal

Then I launch ubuntu in order to correct the grub problem.
I used boot-repair in order to fix it. But I still have the issue when I reboot my system.

Then I made a boot-info from boot repair and here is the link :
[http://paste.ubuntu.com/12034669/](http://paste.ubuntu.com/12034669/)

Any ideas of what I can try to fix that?

Many thanks,

---

### Post by oldfred on 2015-08-09
Did you let Boot-Repair run its suggested fixes?

How did you configure your HP to boot Ubuntu in first place?
Every HP we have seen has needed a work around.
Boot-Repair used to copy grub into Windows efi folder &  rename as the Windows efi boot file. That is not now recommended as Windows updates overwrite that. 
And now Boot-Repair suggests adding an entry to Windows BCD.

But most HP users have copied grub or shim efi files into /EFI/Boot and renamed to bootx64.efi. Then the hard drive boot entry will work if you already have one, or you can create one that will work. But then you have copied grub & a major update of grub may get versions out of sync & need recopying again.

---

