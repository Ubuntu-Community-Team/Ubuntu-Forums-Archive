---
title: "Grub Error 22"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by keshek on 2007-01-02
I am trying to install Ubuntu 6.10 and I am having a problem booting after the install. I get a Grub error 22 when it tries to boot. This is what I get from fdisk -l 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15681   125957601    7  HPFS/NTFS
/dev/sda2   *       15682       19299    29061585   83  Linux
/dev/sda3           19300       19457     1269135    5  Extended
/dev/sda5           19300       19457     1269103+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
236 heads, 43 sectors/track, 15402 cylinders
Units = cylinders of 10148 * 512 = 5195776 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15402    78146560    7  HPFS/NTFS

```

This is a dual boot system with both WinXp and Ubuntu being installed to my first Serial ATA hd. I let the installer partition the free space for Ubuntu and accepted the default install location for grub which was hd0. I have installed ubuntu in the past without any problems using the exact same setup. But I always used the text based installers. Just to check I pulled out my 6.06 dvd and ran the text installer and used the same partition setup (it doesnt ask where to install grub) and the installer froze at installing grub. Could anyone tell me what I should enter for grub location to get this install to work. Thanks.

---

### Post by goodfella on 2007-01-02
I was getting the same error.  It was because during the install the menu.lst file was setup incorrectly.  If you could post the contents of your menu.lst file and your device.map file I might be able to help you.  Even though I had that problem I was able to boot ubuntu by using the live cd and selecting the last option which if I remember says "Boot from First Hard Drive" or something like that.  If you post those files I should be able to help you.  Like I said I had the same problem.

---

### Post by keshek on 2007-01-03
I still wasnt able to boot using the live cd, I dont know much about mounting drives, if you someones tells me how i will use the live cd and dig up the menu.lst that way.

---

### Post by falsedust on 2007-01-04
Depending on which partition has your linux (sda2 ?) you can mount it using the terminal in the live cd -
sudo mount /dev/sda2 /mnt     <- note there is a space between ..sda2 and /mnt

Then -
sudo gedit /mnt/boot/grub/menu.lst

---

### Post by Jose Catre-Vandis on 2007-01-04
I posted a tip about this Error 22, but it has not cleared the mods yet. My clean install of any Ubuntu gave error 22 with three HDs and a CD rom. I removed the IDE1 connector which was carrying two of the HDs and the thing then booted. On reconnecting the IDE1 the thing booted OK. Don't know why this should be, but try reducing hardware/drives and see if this helps. It was definitely not a software config problem

---

