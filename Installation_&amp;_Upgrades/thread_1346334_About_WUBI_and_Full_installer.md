---
title: "About WUBI and Full installer"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by desaturated on 2009-12-04
Im using WUBI this time, 
all i want to know is.. the diffferent when using WUBI and FULL installer..
focusing in performance and compability..

is it true that WUBI using NTFS?

---

### Post by MelDJ on 2009-12-05
wubi does not install ubuntu on its on partition. but it installs ubuntu as a program under windows. so if you want to uninstall ubuntu, you will have to remove through windows's add/remove.
the full installer installs ubuntu on its own partition
the full installer is preferred as it allows ubuntu to be independent of windows. so if windows crashes, ubuntu will still work. and maybe there will be a performance boost as ubuntu will use the ext filesystem

---

### Post by misterbk on 2009-12-05
> **desaturated said:**
> Im using WUBI this time, 
all i want to know is.. the diffferent when using WUBI and FULL installer..
focusing in performance and compability..

is it true that WUBI using NTFS?

From what I can gather, the Wubi installer installs Linux to an .ISO image within your Windows filesystem, and adds an option inside the Windows bootloader to boot that .ISO image as if it were a hard drive.

This means that internally, Linux is translating block device requests through a software layer, into NTFS-3G (probably), and directing it to an image file on your NTFS partition.

Seems whether it works well depends who you ask.  One person made a good point, saying that he didn't recommend Wubi because few people use it, so your resources for support are more limited.

---

### Post by misterbk on 2009-12-05
> **MelDJ said:**
> wubi does not install ubuntu on its on partition. but it installs ubuntu as a program under windows.
It may appear in the Add/Remove Programs dialog, but that alone doesn't make it a "windows program".  Everything I see points to the Wubi install being a "boot from image file" scenario similar to Windows 7's VHD support.

> 
the full installer is preferred as it allows ubuntu to be independent of windows. so if windows crashes, ubuntu will still work. and maybe there will be a performance boost as ubuntu will use the ext filesystem

Performance boost should be true.  Since the Ubuntu "partition" is just an image file on the Windows filesystem, seems like the only Windows issue that could kill Ubuntu would be a full filesystem collapse, right?  If Windows stops booting properly, but the filesystem still works, Ubuntu should still load, right?

---

### Post by wilee-nilee on 2009-12-05
> **misterbk said:**
> It may appear in the Add/Remove Programs dialog, but that alone doesn't make it a "windows program".  Everything I see points to the Wubi install being a "boot from image file" scenario similar to Windows 7's VHD support.



Performance boost should be true.  Since the Ubuntu "partition" is just an image file on the Windows filesystem, seems like the only Windows issue that could kill Ubuntu would be a full filesystem collapse, right?  If Windows stops booting properly, but the filesystem still works, Ubuntu should still load, right?

No the windows bootlaoder is part of windows if it crashes you may not get to the bootloader. 

Ubuntu also runs slower in wubi.

Wubi is a good way of trying out Ubuntu though without having to repartition and reinstall the windows bootloader to the MBR if you want to remove it.

---

### Post by desaturated on 2009-12-05
im using WUBI because i have bad experience when using 2 boot @ my system..
i lost my boot on windows. and have to re install it.. but the linux partition still there...but i cannot using it.. so i have to format the hardrive remove all partition and al partitioning stuff it make me go nuts.

but still, im dont have any problem using WUBI. KOALA work smooth. im upgrading, installing, everything works fine.. but slight HD performance didnt much give any different
but also i did save my file on windows partitions...

so my experience proof. WUBI is not for trial... u can use it full of used of ubuntu.

---

### Post by darkod on 2009-12-05
> **desaturated said:**
> im using WUBI because i have bad experience when using 2 boot @ my system..
i lost my boot on windows. and have to re install it.. but the linux partition still there...but i cannot using it.. so i have to format the hardrive remove all partition and al partitioning stuff it make me go nuts.


You are of course right to use whatever works for you. But lots of people install wubi because they think it's the same as side-by-side dual boot and that's wrong, it should be pointed out that it isn't. I have no problem people saying wubi is working, but they should not try telling people who are first trying linux that it's the same as dual boot install.
As for what you wrote above, restoring any bootloader, windows or grub, is quote simple unless there are other more complex problems and definitely doesn't involve total reinstall of both OSs. That is the last resort. Again, people can use this procedure if they want and if it's easier for them, but don't complain because you didn't run two commands to restore grub. Reformatting is not the default solution.

---

