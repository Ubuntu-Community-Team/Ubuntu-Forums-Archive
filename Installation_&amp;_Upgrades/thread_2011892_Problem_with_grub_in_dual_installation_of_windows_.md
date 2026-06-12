---
title: "Problem with grub in dual installation of windows and linux"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by msandeep273 on 2012-06-28
Hi,

I had installed ubuntu within windows. But it got corrupted two times, and i had to just format the partition where it was installed. But, the Grub still lists the two corrupted ubuntus.

I have again installed ubuntu, and now, there are 2 grubs - one with 

[I]1. Windows
2. Ubuntu /*corrupted
3. Ubuntu /*corrupted
4. Ubuntu /*working[/I]

The second grub shows me the updates of kernels of ubuntu 10.10 presently installed.

I tried startup manager, but it only modifies the second grub, whereas the first one remains.

Can someone help me as to how to clean this mess up, and have only one grub, with ubuntu as my default OS.

Thanks and regards,
Sandeep.

---

### Post by bcbc on 2012-06-28
Use bcdedit as per [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") 
> To use bcdedit, run cmd.exe as an administrator, then enter bcdedit to show all boot entries, note the {GUID} specified for the Ubuntu entry, and then remove it: bcdedit /delete {GUID}

Here's an example: [http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

---

### Post by msandeep273 on 2012-06-28
Thank you.

It worked.

---

