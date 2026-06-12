---
title: "Reinstalling Ubuntu caused Windows letter change"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by ragingmen on 2008-06-08
I've recently reinstalled 7.10 on a machine with windows xp. After installation I could not boot into XP with the system citing a boot directory error. So I used booted off of the windows setup cd and discovered that the C and D drives have been flipped, and I assume windows is attempting to boot from the current C drive which does not have the Windows files.

Any help would be appreciated!

fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13867   111386646    f  W95 Ext'd (LBA)
/dev/sda2   *       13868       14593     5831595    b  W95 FAT32
/dev/sda5               1       11986    96276351+   7  HPFS/NTFS
/dev/sda6           11987       13810    14651248+  83  Linux
/dev/sda7           13811       13867      457821   82  Linux swap / Solaris

menu.lst:
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a28250ac-c28f-4c76-ad09-2f6bc6328549 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a28250ac-c28f-4c76-ad09-2f6bc6328549 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by zvacet on 2008-06-09
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Edit your grub with 

```
gksudo gedit /boot/grub/menu.lst
```

and replace windows entries with 

title              Microsoft Windows XP Professional
rootnoverify       (hd0,1)
makeactive
chainloader +1

---

### Post by logos34 on 2008-06-09
> **ragingmen said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13867   111386646    f  W95 Ext'd (LBA)
[B]/dev/sda2   *       13868       14593     5831595    b  W95 FAT32
/dev/sda5               1       11986    96276351+   7  HPFS/NTFS[/B]
/dev/sda6           11987       13810    14651248+  83  Linux
/dev/sda7           13811       13867      457821   82  Linux swap / Solaris

...

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,**4**)
savedefault
makeactive
chainloader	+1

try booting from sda5 (hd0,4)...The fact that they have changed seems to make sense because you normally install the C: system drive on NTFS, and put documents (shared partition) on fat32.

If the 'makeactive' option doesn't enable boot of sda5, you'll need to switch the boot flag (*) with 

sudo cfdisk 

or 

gparted>right-click sda5>check boot
(also, remove other flag from sda2)

---

### Post by meierfra. on 2008-06-09
> try booting from sda5 (hd0,4)...

Windows never puts the boot information on a logical partition.
So this would only work if  you moved XP from a primary to logical partition. (A logcial partition is any partition numbered higher than 4. So /dev/sda5 is the first logical partition) But  you might as well try it. 

> If the 'makeactive' option doesn't 

Do NOT use "makeactive"   together with "(hd0,4)".  Grub is unable to apply "makeactive" to a logical partition. "root (hd0,4),  makeactive"  will produce   Error 12.


So try zvacet's suggestion and

title Microsoft Windows XP Professional
rootnoverify (hd0,4)
chainloader +1 

Did Windows use to be the only partition you had?  Or was it the first partition on your hard drive.
In either case  you need to edit "boot.ini":  Change "partition(1)" to "partition(2)"
See  [http//support.microsoft.com/kb/289022]("http://support.microsoft.com/kb/289022") for detailed instruction.

If none of this helped:

> After installation I could not boot into XP with the system citing a boot directory error. 

Could you post the exact error message?
Did you delete any partition when you re-installed Ubuntu?

---

