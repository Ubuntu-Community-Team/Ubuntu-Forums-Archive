---
title: "grub a disk read error occurred on windows after installing 12.10"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by dadoeyad on 2012-10-21
Hi I just installed ubuntu 12.10 and when I choose windows from the boot menu it's giving me
```
a disk read error occurred
```Any help?

---

### Post by kc1di on 2012-10-21
> **dadoeyad said:**
> Hi I just installed ubuntu 12.10 and when I choose windows from the boot menu it's giving me
```
a disk read error occurred
```Any help?

Can you give us a little more information?
Is this a UEFI boot or regular? Windows 7 or xp ?

If it's regular then the fix is to use the windows CD and do a fixMBR or fixboot.  then you will have to reinstall grub to the MBR.

you can do the grub fix by downloading boot-repair from [here.]("https://help.ubuntu.com/community/Boot-Repair")

(Follow the instructions on the page)
you can find the instruction to restore the windows boot for windows 7 on [this page ]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

---

### Post by dadoeyad on 2012-10-21
I restored MBR using boot-repair. it worked.
Thanks

---

### Post by kc1di on 2012-10-21
> **dadoeyad said:**
> I restored MBR using boot-repair. it worked.
Thanks

your welcome have fun :)

---

