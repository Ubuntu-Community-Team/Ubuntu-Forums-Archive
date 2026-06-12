---
title: "dual boot problem"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by ggankhuy on 2007-02-18
I had a windows ME on primary and WIN2000 on first logical on extended.
I installed ubuntu on primary trashing the WinME, but now I can't boot to Windows.

I tried this from grub commadn line:

rootnoverify (hd0.4)           //recognize WIN2000 file system as FAT32 
makeactive                        // invalid device requested.
chainloader +1 
boot                                   //invalid system disk.

I thought ubuntu will leave the other boot options not touched. 
Is there anything I can do? Did installing the ubuntu on primary trashed the previous boot loader so that I can't boot to Win2000 on extended partition anymore? Thanks!

---

### Post by willc0de4food on 2007-02-19
is win2k on /dev/hda5 ?
can you post the output of fdisk -l ?
and the contents of /boot/grub/menu.lst

---

### Post by ggankhuy on 2007-02-23
> **willc0de4food said:**
> is win2k on /dev/hda5 ?
can you post the output of fdisk -l ?
and the contents of /boot/grub/menu.lst

Well situation has changed. 
Now i have Ubuntu on  one PHYSICAL drive PriMaster and Win2000 Prof on another PHYSICAL  drive Secondary Master. Both has a MBR and boots fine separetely. Now I tried to boot windows 2000 from Grup. I have tried same thing:

rootnovery (hd1,0)          // since it is sec master.
makeactive              
chainloader +1

But as soon as do 
boot                                // to boot from drive with win2k
it freezes with blank screen.

---

### Post by confused57 on 2007-02-23
> **ggankhuy said:**
> Well situation has changed. 
Now i have Ubuntu on  one PHYSICAL drive PriMaster and Win2000 Prof on another PHYSICAL  drive Secondary Master. Both has a MBR and boots fine separetely. Now I tried to boot windows 2000 from Grup. I have tried same thing:

rootnovery (hd1,0)          // since it is sec master.
makeactive              
chainloader +1

But as soon as do 
boot                                // to boot from drive with win2k
it freezes with blank screen.

Since Windows is on a separate hard drive, you'll need mapping commands, for example:

title              Windows XP
rootnoverify     (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

If rootnoverify (hd1,0) gives you problems, just try root  (hd1,0)...

---

### Post by ggankhuy on 2007-02-23
OKI doki

---

