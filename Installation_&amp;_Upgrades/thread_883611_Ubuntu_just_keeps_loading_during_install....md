---
title: "Ubuntu just keeps loading during install..."
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by jus1haz2 on 2008-08-08
I have tried multiple linux distros and none seem to work on my desktop. I got fedora to work once but then it kernel panicked. 

With ubuntu the problem seems to be with installing, i cannot get anywhere past selecting the installation off the cd, it just keeps loading. A couple of times I see a blinking cursor but most of the time it just gets stuck on the loading screen (the loading bar will change from really slow to normal speed). I have tried both the 32 and 64bit editions and both seem to have the same problem.

My Computer:
AMD 4000+
2GB ram
74GB Raptor + 300GB w/ NCQ
GIGABYTE GA-K8N Ultra-9 Mobo
7800GT 256mb

Windows works fine so I dont think its a hardware issue.

---

### Post by TenPlus1 on 2008-08-08
Very strange indeed...  It may be a conflict with a device, so maybe unplugging all USB devices until installed (except keyboard.mouse of course)...  Other than that, are you using an original Ubuntu install CD ?  If not, did you download, compare checksums and burn at a very low speed ?

I tend to use Deluge to download the .iso file then force a re-check when downloaded to make sure it's all there...

---

### Post by jus1haz2 on 2008-08-08
I have checked the cd and did re-burn one at a lower speed but it didn't help. I also tried installing another gfx card (PCI one) but that didn't help either. I read somewhere (lost the link) that it could be a USB problem, so maybe I will try using a PS2 keyboard.

---

### Post by jus1haz2 on 2008-08-09
Alright it seemed to install properly with a ps2 keyboard but now i am getting error 17 from grub, any ideas?

I have the following drives

74GB Sata -Windows XP 64bit
320GB Sata - Data
80GB Sata - Has linux on the second partition

---

### Post by PmDematagoda on 2008-08-09
Download the Super GRUB Disc from [here]("http://forjamari.linex.org/frs/download.php/1020/super_grub_disk_0.9737.iso") and boot the PC with it, then try and recover GRUB and see if it makes an improvement.

---

### Post by jus1haz2 on 2008-08-09
Alright, I have browsed through some of the support documentation [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems) but am still lost on what exactly I should do once I am in SGD. Most of the options i try, for instance, "Grub => MBR & Linux! (1) Auto ;-)" return errors, "Error 15: File not found".

If I browse to the 'Repair Grub' section it just says "SGD has NOT succeeded :("

:(

---

### Post by PmDematagoda on 2008-08-09
Can you boot the Ubuntu Live CD and post the output of:-
```
sudo fdisk -l
```

---

### Post by jus1haz2 on 2008-08-09
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
16 heads, 63 sectors/track, 155009 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x49f2340b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       94452    47603304    f  W95 Ext'd (LBA)
/dev/sda2   *       94453      155009    30520728   83  Linux
/dev/sda5               2       91756    46244488+   7  HPFS/NTFS
/dev/sda6           91757       94452     1358752+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x060f173b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0000aba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      568168   286356640+   7  HPFS/NTFS

```

and here is my menu.lst

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829ce281-f889-43dc-ab0a-e100ab32ebc7 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829ce281-f889-43dc-ab0a-e100ab32ebc7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by PmDematagoda on 2008-08-09
The output of the commands look fine. Did you try changing the boot device order in the BIOS and seeing if that fixes it?

---

### Post by jus1haz2 on 2008-08-09
Ya I tried all the different devices before posting, the 74gb just boots straight to windows if that's any help.

---

