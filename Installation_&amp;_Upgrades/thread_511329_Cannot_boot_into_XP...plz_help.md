---
title: "Cannot boot into XP...plz help"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by permak on 2007-07-27
Hi guys, I really hope you can help me with this. Long story short, I got a new hard-drive, formatted it into two ntfs partitions. 20 and 60 gigs respectively. Then I installed windows on the 60 gigs partition. Today I wiped the 20 gigs with the Ubuntu install disc and created a swap and a ext3 for ubuntu out of the created free space. Now Grub doesnt even give me an option to boot into Windows. I tried editing the grub list and still nothing. 

Here's my info - 

menu.lst contents 

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80ce9771-1e6f-494a-8cea-e98fdb4de2bd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80ce9771-1e6f-494a-8cea-e98fdb4de2bd ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title Windows Xp
root (hd0,4)
chainloader +1

AND fdisk -l contents

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63        9729    77650177+   f  W95 Ext'd (LBA)
/dev/sda5            2550        9729    57667648+   7  HPFS/NTFS
/dev/sda6              63        2549    19976764+  83  Linux

Any ideas???

---

### Post by merlinus on 2007-07-27
You might try changing your windows entry in /boot/grub/menu.lst to:

title       Windows XP
root        (hd0,4)
savedefault
makeactive
chainloader    +1

Also, for future reference, it is always better to have windows on the first partition.

-merlin

---

### Post by permak on 2007-07-27
Thanks tried that, no go.

---

### Post by Pumalite on 2007-07-27
Windblows likes sda1

---

### Post by MrHippocampus on 2007-07-27
Try this one:

```
title Windows XP
rootnoverify (hd0,4)
makeactive
chainloader +1
```

note that the spaces in the commands are important and must be kept the same as ive typed

---

### Post by permak on 2007-07-27
thanks for the advice, I have tried using rootnoverify didn;t work before. Ill give it another whirl. Anyone know how to map it so it thinks its sda1? I tried mapping myself but I am not sure im doing it right.

---

### Post by MrHippocampus on 2007-07-27
You should only need to map the drive if the mbr is not on the same drive as windows in, i.e. BIOS is booting from drive 1 but windows is on drive 2.

If this is the case then this should do the trick, if not then you shouldnt need it:

```

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,4)
makeactive
chainloader +1

```

---

### Post by merlinus on 2007-07-27
The easiest solution is to start over.  Install windows first, and then install ubuntu.

You can backup needed data using ubuntu beforehand.

-merlin

---

