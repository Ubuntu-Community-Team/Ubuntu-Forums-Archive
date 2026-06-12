---
title: "Add a second Ubuntu in Grub 1.5"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by Jonnybx on 2012-02-15
Hello,
I installed a second ubuntu (32 bit) on a separate HDD (sdd), how can I add it in Grub?
I already tried different Versions (with mapping, without, ...).

The latest version:
```
title           play SavageXr
root            (hd3,0)
map             (hd3) (hd0)
map             (hd0) (hd3)
makeactive
chainloader     +1
```this always brings up "Error 13 Unsupported or invalid executable format"

What is wrong?

Greetings, jonnybx

---

### Post by darkod on 2012-02-15
What is wrong is that the menu entry you described is for booting windows, not ubuntu/linux.

Also, are you sure you have grub1? Ever since ubuntu 9.10 it comes with grub2 which can update the boot menu automatically with simply running:
sudo update-grub

---

### Post by Jonnybx on 2012-02-15
I've installed grub 1.5 instead of grub 2, it's faster on my computer. 
sudo update-grub doesn't work, it can't find the second ubuntu on another HDD. 
If my try is completly wrong, how can I add an entry for the second ubuntu manually?
( I can't find it in the web)

Greetings, jonnybx

---

### Post by darkod on 2012-02-15
Post the results of:
sudo fdisk -l (small L)

Also, after the results explain a little bit which is the main install (on which disk and partition), and which is the second install.

---

### Post by Jonnybx on 2012-02-15
Ok, here's the output:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026afe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   226054143   113026048   83  Linux
/dev/sda2       226056190   234440703     4192257    5  Extended
/dev/sda5       226056192   234440703     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64  1258307189   629153563    7  HPFS/NTFS/exFAT
/dev/sdb2      1258307190  1953520064   347606437+   5  Extended
/dev/sdb5      1258307253  1953520064   347606406    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7cb92faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   573442047   286720000    7  HPFS/NTFS/exFAT
/dev/sdc2       573442048  1250260991   338409472    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029587

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    69752831    34875392   83  Linux
/dev/sdd2        69754878    78139391     4192257    5  Extended
/dev/sdd5        69754880    78139391     4192256   82  Linux swap / Solaris

```grub is on sda
[LIST]
[*]on sda is the main OS, an ubuntu 11.10 64bit
[*]on sdb are my user-files of Windows and Linux (2 partitions)
[*]on sdc is Windows and it's stuff (2 partitions)
[*]on sdd is another ubuntu, 32 bit (the one I want to add)
[/LIST]


I hope this helps.

---

### Post by darkod on 2012-02-15
Yes, it helps a lot. But since I don't remember the syntax of grub1 exactly, I need one more thing.

Open the /boot/grub/menu.lst file and post the entry for your current 11.10 (only one entry).

The entry is the whole group of lines, 4-5 lines, starting with:
title Ubuntu....etc

and ending with empty line.

You can use the same entry with small modifications but I don't remember them on the top of my head until I see the entry.

---

### Post by Jonnybx on 2012-02-15
Here it is...

```
title           Ubuntu 11.10, kernel 3.0.0-12-generic
uuid            0df253b4-1b20-4dcc-b722-b6f650ce37bd
kernel          /boot/vmlinuz-3.0.0-12-generic root=UUID=0df253b4-1b20-4dcc-b722-b6f650ce37bd ro quiet splash
initrd          /boot/initrd.img-3.0.0-12-generic
quiet

```

---

### Post by darkod on 2012-02-15
> **Jonnybx said:**
> Here it is...

```
title           Ubuntu 11.10, kernel 3.0.0-[COLOR=Red]12[/COLOR]-generic
uuid            [COLOR=Red]0df253b4-1b20-4dcc-b722-b6f650ce37bd[/COLOR]
kernel          /boot/vmlinuz-3.0.0-[COLOR=Red]12[/COLOR]-generic root=UUID=[COLOR=Red]0df253b4-1b20-4dcc-b722-b6f650ce37bd[/COLOR] ro quiet splash
initrd          /boot/initrd.img-3.0.0-[COLOR=Red]12[/COLOR]-generic
quiet

```

OK. Copy this entry below all of the entries that exist right now in menu.lst.

Find out the UUID of /dev/sdd1 with executing the blkid command.
Change the title to Ubuntu 32bit or what ever you want the new title to be.
Change the UUID value with the value you got for /dev/sdd1 in both places.
Change the -12- depending what is the kernel of the 32bit install you want to use.

You can make more than one entry, each for separate kernel changing just the -12- part but there is really no reason to have all kernels in the boot menu.

After you save the changes to menu.lst and reboot it should work if there were no errors in the menu entry.

---

