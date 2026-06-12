---
title: "Dual Boot Problem (ntoskrnl.exe)"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by chamby on 2007-05-01
Ok so i tried installing Ubuntu on a seperate HD from my existing windows install..

Ubuntu boots fine, and is what i am using right now, but windows will not load due to the "ntoskrnl.exe" 

This is my first experience with linux, so please be descriptive with answers :)

If there is something obvious here that i am missing, let me know please. i dont know what most of the following means. :(

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       19456    53882010    f  W95 Ext'd (LBA)
/dev/sda5           12749       19456    53881978+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19266   154754113+  83  Linux
/dev/sdb2           19267       20023     6080602+   5  Extended
/dev/sdb5           19267       20023     6080571   82  Linux swap / Solaris

```

Thanks in advance to anyone who can help

---

### Post by chamby on 2007-05-01
bump! :[

---

### Post by psusi on 2007-05-01
Could you be more specific about the error message that windows gives?

---

### Post by chamby on 2007-05-01
ok, well i tried to boot windows to check the error message again, and it started to boot, but i had done a windows repair so that finished, then it booted into windows. since then i have booted into windows about 5 times in a row so i think windows repair fixed the problem. noooow i have another problem :(. ubuntu will not boot. for the whole time i've had ubuntu i have had a problem with "piix"? and have had to type "modprobe piix" and then "exit" at the (initramfs) prompt. each time i have done this it has made ubuntu load, but now when i do it, the ubuntu load bar sits at the beginning for about 5 minutes and brings me back to the prompt. :/

---

