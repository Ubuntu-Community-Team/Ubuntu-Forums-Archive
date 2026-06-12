---
title: "Ubuntu 7.10 doesn't see my partitions"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by ncc50446 on 2008-04-04
Hey
I'm trying to install Ubunto 7.10, and it doesn't seem to be working. I'm using the live cd version. I get to step 4, and there are no partitions listed. I have two, one NTFS, which has Windows XP, and another one that is a fat 32, which has nothing on it. I partitioned my hd with partition magic, and then formated it with windows (Right clicked on G:, click format as fat32), but it doesn't see either one...what could I be doing wrong?
Thank you for any help :) Really want to try Linux again

---

### Post by forestpixie on 2008-04-04
try formatting it to ext3 with parted magic or the partition editor in the livecd

---

### Post by ncc50446 on 2008-04-04
I'll give that a try, thank you :)

---

### Post by amen-ra on 2008-04-04
I have a toshiba Qosmio G25-AV513 and I have the same issue. I used partition magic and formatted with ext3, and it still dows not recongize the SATA hard drives

---

### Post by ncc50446 on 2008-04-04
I changed mine to ext3, and still having problems...

---

### Post by forestpixie on 2008-04-05
HAving trouble with which editor - does the ubuntu livecd have problems with seeing it - system >admin >partition editor.

When you're booted to the livecd open aterminal - apps >Accessories - paste this in and post the output here please

```
sudo fdisk -l
```

---

### Post by Awjvail on 2008-04-05
Same issue for me.

Toshiba Satellite A200-AH7. Won't see my partitions.

I'm trying ext3 or something
I made the partition with Partition Magic

I also can't seem to access my original partition on Ubuntu.. when in the file browser, I can't access Local Disk that has all of my windows xp stuff on it as well as most of my files. "Cannot Mount Volume"...

Luckily I have some of it on backup but I'd really rather not have to use it.

I'm guessing this isn't an isolated incident.

---

### Post by forestpixie on 2008-04-05
Awjvail - can you do the sudo fdisk -l command

---

### Post by MolsonH on 2008-04-05
I have the same problem. had it in 7.10, have it in 8.04 as well
when I do the sudo fdisk -l it doesn`t return anything. I have tried scripts to mount my partitions and they don`t find anything. I try running pysdm and it crashes when it starts. 
I tried installing with Wubi and I get a busy box command prompt.
I have an Abit IP35 Mobo with the intel chipset

---

### Post by Awjvail on 2008-04-05
> **forestpixie said:**
> Awjvail - can you do the sudo fdisk -l command

Here are the results:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd47f74b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15846   127282963+   7  HPFS/NTFS
/dev/sda2           15847       16242     3180870   1c  Hidden W95 FAT32 (LBA)
/dev/sda3           16243       19457    25824487+   f  W95 Ext'd (LBA)
/dev/sda5           16243       19457    25824456    7  HPFS/NTFS

I'm trying to install on sda5 I believe.

Also, I tried formating the partition as ext3 or something and the install seemed to work fine.. and then it said something about Grub and how it was a fatal error.. and then installation died on me.

I'm  trying to install 7.10. On my other partition, Windows XP Pro is installed.

I checked the MD5's and everything worked fine. The Live CD works fine too.

---

### Post by MolsonH on 2008-04-05
I changed my SATA settings in my BIOS to AHCI instead of IDE and Ubuntu now recognises my drive, but Windows doesn't.

---

### Post by Awjvail on 2008-04-05
Also another error:

When I try to use the partition resize in the installer, it says "An error occured while writing the changes to the storage devices. The resize operation is aborted." :\

---

### Post by forestpixie on 2008-04-05
Awjvail - you need to format the partition to ext3 - it won't install to ntfs

Molson - I have no idea what AHCI is - I suggest you try searching the forums - or post a thread on your own in Absolute Beginners, threads seem to get seen more frequently there - sorry I can't help.

---

### Post by Awjvail on 2008-04-05
Tried it on ext3. Got an error at about 98% installation.

[img]http://i27.tinypic.com/35cgzdw.png[/img]

---

### Post by forestpixie on 2008-04-05
I'm afraid that it's a bit beyond me then - all I would try would be to install grub from the livecd or download the alternate install cd. Sorry - I can point you in the right direction for installing grub with the livecd and at installing with the alternate.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by prshah on 2008-04-05
> **ncc50446 said:**
> but it doesn't see either one...what could I be doing wrong?
Thank you for any help :) Really want to try Linux again

Some SATA controllers are not immediately recognized by Linux/Ubuntu.

You should look in your BIOS for a SATA option with the words "Legacy" or "Native" or "ATA"  and then toggle it and try. If ubuntu then sees your partitions, proceed with the installation, and after the installation is complete, toggle the setting back.

---

