---
title: "very short &amp; fast question on booting WinXP from GRUB"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by thirdd on 2008-11-07
Hello everybody,

As i crashed my MBR two times and had to reformat my complete partition I just wanted to check if my new menu.lst configuration is correct.

My first primary partition is a EXT3 running ubuntu, the next one are 3GB swap and then follows a primary partition hosting WinXP as NTFS.

fdisk list this:

> Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x2bd2c32a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       10070    80887243+  83  Linux
/dev/sda2           10445       19456    72388890    f  W95 Erw. (LBA)
/dev/sda3           10071       10444     3004155   82  Linux Swap / Solaris
/dev/sda5           10445       19456    72388858+  82  Linux Swap / Solaris

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

somewhere between my installations and fighting with GRUB (i randomly tried hd0,1, hd1,0 etc but not hd0,4 :oops:) i wrote an note saying:

> /dev/sda5 = WIN
hd(0,4) = WIN

thats why I want to change my menu.lst to :

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7e2e05ab-dfb6-4d8b-919d-65fc446e67be ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

...

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,4)
savedefault
chainloader     +1
```


**Could anybody just tell me if this is correct?**

I would be glad not to crash GRUB again :-)

Thanks in advance

---

### Post by Coreigh on 2008-11-07
Counting starts at 0 not 1 so it would be (hd0,3).

Also I have always had the impression that Windows demands the first partition. Or does partition not matter as long as it is C: to Windows?

---

### Post by caljohnsmith on 2008-11-07
> **thirdd said:**
> ```
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x2bd2c32a

Gerät boot. Anfang Ende Blöcke Id System
/dev/sda1 * 1 10070 80887243+ 83 Linux
/dev/sda2 10445 19456 72388890 f W95 Erw. (LBA)
/dev/sda3 10071 10444 3004155 82 Linux Swap / Solaris
[COLOR="Blue"]/dev/sda5 10445 19456 72388858+ 82 Linux Swap / Solaris[/COLOR]

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge 
```
For one thing, your sda5 Windows partition is marked as a swap partition now, not NTFS or FAT32. Do you know what you might have done to cause that? You could try manually changing it back to NTFS/FAT32 (whichever it was), and see if you can recover the partition. So do you remember whether it was NTFS or FAT32? 

The other issue is that if sda5 is your Windows partition, Windows will normally not boot from a logical partition unless it puts its boot files in a primary partition. Did you at some point have a primary NTFS/FAT32 partition that you deleted?

---

### Post by thirdd on 2008-11-07
Thanks for your replies.

The WinXP partition was (or is) NTFS and I don't know what happend to it. But I know that when GRUB crashed it said my ext3 ubuntu partition would be "Amoeba" or something like this. And all I did was changing it to Linux again and I reinstalled GRUB.

Anyway I am able to mount the NTFS partition in ubuntu and I can sucessfully read and write it.

As I reinstalled GRUB I read somewhere that my NTFS partition is actually hd(0,4) (which makes sense when sda1 is hd(0,0) and sda5 is my NTFS partition).

But I am not sure enough of my menu.lst to dare a new atempt ...


Oh and I did not have any other NTFS/FAT32 partitions that I deleted.
I always had those three in this order and the NTFS partition is a primary partition too! (At least it was when I created it)

---

### Post by caljohnsmith on 2008-11-07
If sda5 is still listed as "swap" by fdisk, you could change it back to NTFS by doing:
```
sudo fdisk /dev/sda
```
"t" to change file system type, "5" for the partition, "7" for the file system type, "w" to write the change, "q" to quit fdisk. I would recommend backing up anything important in Windows first, since you did say you could mount sda5. After that, how about posting the following:
```
sudo fdisk -lu
sudo mount /dev/sda5 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Then I can see if you have your Windows boot files or not.

---

### Post by thirdd on 2008-11-07
At the moment my win partition contains 

> drwxrwxrwx 1 root root       4096 2008-11-02 23:10 .
drwxr-xr-x 5 root root       4096 2008-11-07 22:06 ..
drwxrwxrwx 1 root root       4096 2008-11-01 00:53 Dokumente und Einstellungen
-rwxrwxrwx 1 root root 2137444352 2008-11-02 23:10 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-11-01 09:18 Intel
-rwxrwxrwx 1 root root 3196059648 2008-11-02 23:13 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-11-01 12:46 Programme
drwxrwxrwx 1 root root          0 2008-11-01 15:02 RECYCLER
drwxrwxrwx 1 root root       4096 2008-11-01 00:51 System Volume Information
drwxrwxrwx 1 root root      57344 2008-11-02 23:06 WINDOWS


but I am just going to back it up and change the type like you said

---

### Post by caljohnsmith on 2008-11-07
Unfortunately your Windows boot files are missing, so if they weren't on some other drive/partition that was deleted, I'm not sure why you wouldn't have them. But the good news is that I also have Windows XP, so I've attached the three necessary boot files that you need to this post. And more importantly, I modified the boot.ini for the correct partition since your Windows is on sda5. Just download the attached file to your Ubuntu desktop, and then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
tar xvf Windows_boot_files.tar.gz
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
After that, open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Windows entry with:
```
title Windows XP
root (hd0,4)
chainloader +1
```
Reboot, select Windows in the Grub menu, and let me know how far you get this time. :)

---

### Post by thirdd on 2008-11-08
Thanks a lot for you help caljohnsmith.

sda5 is now correctly listed as NTFS and I can still mount, read and write it.
I copied the windows boot files (and they are 777) but when I choose windows in GRUB i doesnt get further than the blinking cursor ...
But anyway its better than before because GRUB still works and I can still boot ubuntu.

Is it possible that I need to work with map(,) or hide() as my NTFS partition is not the first but third primary partition? I read somewhere that this matters.

Should I change my menu.lst to

```

title Windows XP
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
root (hd0,0)
chainloader +1
```

or to

```

title Windows XP
hide (hd0,0)
hide (hd0,2)
unhide (hd0,4)
root (hd0,4)
chainloader +1

```

?

---

### Post by thirdd on 2008-11-08
As i read that it is necessary to use "rootnoverify" and "makeactive" on several pages concerning GRUB and windows i changed my menu.lst to

```

title Windows XP
rootnoverify (hd0,4)
makeactive
chainloader +1
```

but now I get the following when I start to boot WinXP

> 
Error 12: Invalid device requested

The description for this error doesnt get me really further ...
Does anybody know what could be the problem?

---

### Post by louieb on 2008-11-08
Please post a new **sudo fdisk -l **

A couple of things Windows does not like being install in a logical partition its possible but not easy. The 2nd is you will want to remove the boot flag from the Linux partition and set the window partition boot flag. (only one partition can have its boot flag set).  

Got to say interesting problem  haven't seen anything quite like that, 
Heres some reading on windows in a logical partition: 
[Understanding MultiBooting]("http://www.goodells.net/multiboot/index.htm") 
[Multi-Booting with Windows in an Extended Partition]("http://www.goodells.net/multiboot/principles.htm")

---

### Post by caljohnsmith on 2008-11-08
OK, we are making progress, but first I should mention that you shouldn't use the "makeactive" line with your Windows entry because Grub can't set a logical partition as bootable (active); it is not necessary to do so, because you can boot Windows without having to set the boot flag on its partition. So please change your Windows entry to:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Also, it looks like you will need to repair the Windows boot sector, so if you have your Windows Install CD, boot that up, go to the "recovery console", and do:
```
fixboot
```
That may be all it takes to get Windows booting properly, but if you get a "Starting up..." message and then it hangs, let me know, and we can most likely fix that too. I think we are really close to getting your Windows to boot.

---

### Post by thirdd on 2008-11-08
Thanks again for your help.
I had the same problem after removing "makeactive" and even "fixboot" did not help. Probably it is because I reformatted and reinstalled so many times, and just partitions and not the hole disk.

That's why I finally deleted all partitions and started from 0 and everything went fine. 
First I installed WinXP on a brand new first primary partition leaving half of the space unpartitioned.
After that I installed Ubuntu and partitioned the remaining unpartitioned half within the Ubuntu installer into an ext3 and a swap partition. After that Ubuntu even automatically created and working entry in the menu.lst for GRUB.

What I´ve learned from a lot of hours of reformating and reinstalling and crashing and rebuilding GRUB is that its f*** easy if one starts from 0 and lets win take his desired first primary partition and installs ubuntu after that.

---

