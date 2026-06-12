---
title: "Explain Installing for a windows User"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Alexdelpiero1974 on 2010-04-29
Hello , How are you ?
I'm a Windows user and i would like to install Ubuntu and try it 
i have all the requirements for it ,

but i want to ask about How to make Partition for Ubuntu 
i'm currently have 80 GB hard disk 
and i'm willing to give Ubuntu 7 or 10 GB 
first of all i want to know how to make  a 7 or 10 GB for Ubuntu 
without affect my over data or damage it 

i just want to know how to cut or give ubuntu those 7 or 10 GB only 
without ruin my data or my harddisk 

please explain this point to me with a ll methods or alternatives 

i want the safest way to do it

---

### Post by Megaptera on 2010-04-29
As a start, you could look at Wubi which install Ubuntu like a Windows prog but no partitioning etc reqd.
Choose between Ubuntu or Windows at boot.

[http://wubi-installer.org/](http://wubi-installer.org/)

Or if you want to dual boot, good clear guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Talks abou XP, but works for Vista too.

Whatever you decide backup first!

Hope these help?

---

### Post by Ms_Angel_D on 2010-04-29
> **Megaptera said:**
> As a start, you could look at Wubi which install Ubuntu like a Windows prog but no partitioning etc reqd.
Choose between Ubuntu or Windows at boot.

[http://wubi-installer.org/](http://wubi-installer.org/)

Or if you want to dual boot, good clear guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Talks abou XP, but works for Vista too.

Whatever you decide backup first!

Hope these help?

They have a guide for vista as well [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by mattlopezdias on 2010-04-29
firstly backup everything you'd not want to lose. people always say this and people always ignore it, including myself, but you should if you don't wanna risk losing it all.

then boot from the latest full release ubuntu cd and it will guide you, it has it's own partition software that does it all for you. you will then have a choice at boot time to boot into windows or ubuntu. just be sure and read the screen clearly to ensure you are installing alongside windows and not instead of it.

anything above 5gb is plenty to try ubuntu properly.

---

### Post by Mark Phelps on 2010-04-29
> **Alexdelpiero1974 said:**
>  ... i want the safest way to do it

The "safest way" (if you're running Vista or Win7) is to NOT let the Ubuntu installer shrink your MS Windows OS partition; instead, use the Vista/Win7 Disk Management utility to shrink the OS partition and leave the new space as unallocated.  Then, boot into Vista/Win7 to ensure that it still boots OK before you continue.

If you're running Win7, it's also a good idea to use the Backup feature to create & burn a Win7 Repair CD.  That will come in handy later if you need to repair the Win7 boot loader.

If you're running XP, you should be OK letting the Ubuntu installer do the partition shrinkage.

---

