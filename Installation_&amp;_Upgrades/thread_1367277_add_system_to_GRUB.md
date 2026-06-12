---
title: "add system to GRUB"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by sebek60 on 2009-12-29
hello everyone!
How add windows Xp to GRUB?
When I edit file "menu.lst" on:
```

title Windows XP
rootnoverify (hd0,2)
chainloader +1

```
and start, system display error:
"Don't found file NTLDR
Press key ctrl+alt+del"
I read about this problem but I don't solved them.
I hope You understand me because my English is terrible.

---

### Post by oldfred on 2009-12-29
Your entry should work if windows is on sda3 and you are using grub legacy(0.97).
to see your partitions:

sudo fdisk -l (el not 1 or i)

---

### Post by raymondh on 2009-12-29
title        Windows XP
root        (hdX,Y)
savedefault
makeactive
chainloader    +1

X & Y are the HD and partition, starting from 0

If you have more that 1 HD's, you may have to re-map as well ... to fool XP into thinking it's "first" on HD.  Assuming XP is on the 2nd HD:

title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

EDIT : +1 on Oldfred ... let's see the fdisk -l output.

Regards,

---

### Post by sebek60 on 2009-12-29
fdisk -l:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94a494a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
/dev/sda2           19457       19705     2000092+  82  Linux swap / Solaris
/dev/sda3           19706       29990    82614262+   7  HPFS/NTFS
/dev/sda4           29991       38913    71673997+  83  Linux


```

---

### Post by oldfred on 2009-12-29
Do you have two different copies of windows as you have two NTFS partitions. The boot flag (*) is on sda1, so makeactive is not required.

title        Windows XP
root        (hd0,0)
savedefault
chainloader    +1

If it is sda3 you either need to move the boot flag using gparted or  the makeactive should temporarily add the boot flag so windows thinks it can boot.

title        Windows XP
root        (hd0,2)
savedefault
makeactive
chainloader    +1

---

### Post by sebek60 on 2009-12-29
Thanks for answers but my situation is changed. 
fdisk -l out now:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94a494a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
/dev/sda2           19457       19705     2000092+  82  Linux swap / Solaris
/dev/sda3           19706       27428    62034997+   7  HPFS/NTFS
/dev/sda4           27429       38913    92253262+   5  Extended
/dev/sda5           29991       38913    71673966   83  Linux
/dev/sda6           27429       29878    19679562   83  Linux
/dev/sda7           29879       29990      899608+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
I installed GRUB 2. I want boot windows from disk sda3, how can I do that?
And I want add windows to GRUB 2. Previously when I installed linux, GRUB automatic search every systems.

---

### Post by oldfred on 2009-12-29
use gparted to move the boot flag from sda1 to sda3 assuming you have a bootable windows in sda3.

In Ubuntu this will find windows installs (if they are bootable)
sudo update-grub

you can also do this to set boot flags windows will only recogize one flag per drive or else not work.

    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

---

### Post by v1nsai on 2010-01-24
I've been trying to figure out how to use parttool to 'makeactive' my windows partition but I can't figure out where to put it.  grub.cfg isn't supposed to be directly editable, so do I put the parttool command in the os_prober file or what?

---

### Post by presence1960 on 2010-01-24
wrong thread

---

### Post by oldfred on 2010-01-24
Parttool is a command line to allow editing of the partition table in the MBR. 

I just found you can do this also from a command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

sfdisk is very powerful so be sure to copy command or make sure you have typed it correctly.

---

