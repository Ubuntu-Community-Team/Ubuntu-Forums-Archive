---
title: "Windows 7 Hanging at Starting Screen after Dualboot Installation"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by ajdlc47 on 2014-01-28
Hello everyone, I have been struggling for a couple of days now trying to figure out why this happening. So I recently have installed Ubuntu Studio along side my existing installation of Windows 7 64-bit. I was having a really hard time trying to install Ubuntu Studio 13.10 along side my Windows installation. Once I finally got it working. I wanted to repartition my HD so it can have more space. Well, this is where things go bad, I am pretty new to Ubuntu so what I did was I just deleted the partition that Ubuntu was installed on and I ran the installation again via DVD. So it installed with some errors but once that happened I tried to reboot and I was stuck at the grub_rescue screen. I couldn't get out of it. Luckily, I was able to make a Boot-Repair Disc and I ran the recommended and that fixed the grub_rescue screen and I was able to get into Ubuntu. But, I didn't like that there were errors in the install so I retried that installation of Ubuntu again and it worked with no problems. I am currently in Ubuntu Studio right now typing this up on the web browser. But here is my issue, when I try to boot to the Windows install, it just hangs on the Starting Windows screen. I have an SSD so normally that loads pretty quickly. I have let it sit there for about 20 to 30 minutes and nothing. I have tried almost everything I could find. I have ran Test Disk but I don't get the option to repair boot, I have ran Boot-Repair and have tried some of the advanced options (I can't remember which ones but I think it was the fix Windows ones), and the one that is really throwing me off is I have tried to use a Windows Rescue Disc to fun the bootrec.exe /fixboot command but whenever I load up the disc it says it's not compatible with my system. I know I am using the right one. I have Windows 7 Home Premium 64-but edition and that's the Rescue Disc I have. One thing that really stood out was that, I tried just a regular Windows 64bit Home Premium Installation CD and it gave me the same error when trying to run the "Repair my computer" option. So I decided just to see what my drives looked like so I clicked on Install. When I was at the menu that showed my drives, it said that Windows could be installed on the partition that already Windows on it because it was in like GIP or GTS format, I know it was G something, and not NTSF. Which I found odd because I never changed that partition on the drive. But in GParted it says it's NTFS. I am frustrated out of my mind right now. If anyone can help me out with this I would truly appreciate it. I had Windows working fine and then boom it just hangs.
Sorry if this explanation seems kind of choppy, I am running on fumes right now. I have been at this for about 2 days almost non-stop. I just want to get my Windows back, and I am trying to avoid a fresh install. 

Thanks

---

### Post by fantab on 2014-01-28
Boot with Ubuntu install DVD/USB, 'Try Ubuntu Without Installing', Open Terminal [ctrl+alt+T], run the following commands and post its output here:

```
sudo parted -l
sudo fdisk -l
```

You've said you ran Boot-Repair, do you have a LINK to BootInfo Summary? If you do, then post the link here.

---

### Post by ajdlc47 on 2014-01-28
Hello Fantab, thank you for the reply, this is what happens when I try to use the "Try Ubuntu Without Installing" from my flashdrive that I created and used to install Ubuntu Stduio: [http://imgur.com/cKW4Kb1](http://imgur.com/cKW4Kb1)  that's the screen I get. The little white cursor image is a black X. I can move it around but nothing happens.

Also this is my GRUB Menu, what I thought was strange was the many boot options I had for Windows: [http://imgur.com/6g49D1K](http://imgur.com/6g49D1K)

I don't have the link to the original BootInfo Summaries from when I ran Boot-Repair the first couple of times, honestly I wasn't planning on using the forums, I thought I would be able to handle it myself so I didn't save them. If you want I can run Boot-Repair again and then link the new BootInfo Summary if that helps. 

Whoops, forgot to mention that I ran the code in terminal from the Ubuntu Studio install that is currently on my PC, so not from a disc or USB drive.
**Here is the output in Terminal from "sudo parted -l"**
```

Model: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  211MB   210MB   fat32           EFI system partition          boot
 2      211MB   345MB   134MB                   Microsoft reserved partition  msftres
 3      345MB   93.2GB  92.8GB  ntfs            Basic data partition          boot
 4      93.2GB  93.2GB  1049kB                                                bios_grub
 5      93.2GB  111GB   18.3GB  ext4
 6      111GB   120GB   8547MB  linux-swap(v1)


Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  211MB   210MB   fat32        EFI system partition          boot
 2      211MB   345MB   134MB                Microsoft reserved partition  msftres
 3      345MB   1000GB  1000GB  ntfs         Basic data partition          msftdata
```

**And here is the output from "sudo fdisk -l" **

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee587651

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x527cd163

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

---

### Post by fantab on 2014-01-28
Yep, Bootinfo Summary should help determine the issue. Please post a new one.

---

### Post by ajdlc47 on 2014-01-28
Here is the link to the boot info summary: [http://paste.ubuntu.com/6835630/](http://paste.ubuntu.com/6835630/)

---

### Post by fantab on 2014-01-29
Your Ubuntu is installed on /dev/sda and Windows is on /dev/sdb.
Both the Hard Disks have EFI System Partition [ESP].
Normally when installing Ubuntu  and if you have two HDDs you will designate the Grub Location, in your case it should be ESP /dev/sda1 since Ubuntu is installed there. ESP /dev/sdb1 should be for Windows as Win is installed there. You have installed everything everywhere, that is, you have both Windows and Ubuntu boot files on both the HDDs ESPs. Probably that is why you have many Windows entries in the Grub menu.

When you ran Boot-Repair it renamed the Windows boot file: /EFI/Microsoft/Boot/bkpbootmgfw.efi
You should re-run Boot-Repair with the option '**Restore EFI backups**' and that should do. And also double check that your Grub is being installed to /dev/sda1.
Make sure you boot your Ubuntu DVD/USB to use Boot-Repair, in EFI mode only... [See Here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").
Make sure you setup /dev/sda1 or Ubuntu as your first boot in UEFI boot menu.
Always make note of the Bootinfo Summary Link, and post it here if have any more boot issues.

You can clean up the Grub menu to unwanted/unnecessary entries with [efibootmgr]("http://manpages.ubuntu.com/manpages/hardy/man8/efibootmgr.8.html").

You have setup /dev/sda5 as a 'legacy boot/non-EFI' partition with 'bios_grub" flag. This is used when you boot Linux from a GPT disk in a Legacy/non-UEFI mode. This not needed in your case. Just remove the 'bios_grub' flag with Gparted.

Good Luck.

---

### Post by ajdlc47 on 2014-01-29
Geesh it really looks like I messed a lot up. Thank you for all your help Fantab. Sadly, it is still hanging. I tried the Restore EFI Backups option just like you said and I purged and reinstalled GRUB as well, and it is still hanging on the Starting Windows screen. Boot repair gave me this message when it as done: >    The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


It also said I may want to try again and enable the option of "Backup and Rename Windows EFI Files." When I ran the Restore EFI Backups, it asked me if I wanted to do that and I said no. Should I redo it and say yes next time or try another method? Also, should I try what Boot Repair told me to do and create that new partition?

I also made sure I was in EFI mode. I ran Boot Repair from within my Ubuntu Installation, is that a problem or should I try it from the DVD? I can't boot from the USB for some reason I don't know what  happened but it just gives me that black screen that I posted earlier. I can try a DVD though and see if that works.

---

### Post by fantab on 2014-01-29
> **ajdlc47 said:**
>  When I ran the Restore EFI Backups, it asked me if I wanted to do that and I said no. Should I redo it and say yes next time or try another method? Also, should I try what Boot Repair told me to do and create that new partition?

Since we want to restore efi backups you should say 'YES' when BR confrims your action.
No need to create any partition.

---

### Post by ajdlc47 on 2014-01-30
> **fantab said:**
> Since we want to restore efi backups you should say 'YES' when BR confrims your action.
No need to create any partition.

Hello Fantab, I am sorry for the late reply, I had to come home and work on some things from my job that have taken up my time the last few days. So I ran MBR with the restore of efi backups, and Windows is still hanging. Here is my pastebin link [http://paste.ubuntu.com/6846711/](http://paste.ubuntu.com/6846711/)
Also, here is the message I was talking about when I use my Windows Home premium disc to just see what's going on with the drives: [http://imgur.com/Vq9rtd9](http://imgur.com/Vq9rtd9) I don't know if it will help but now you can see what I am talking about.

---

### Post by fantab on 2014-01-30
```

parted -l:

Model: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          [COLOR=#b22222]Flags[/COLOR]
1      1049kB  211MB   210MB   fat32           EFI system partition          boot
2      211MB   345MB   134MB                   Microsoft reserved partition  msftres
**[COLOR=#b22222]3      345MB   93.2GB  92.8GB  ntfs            Basic data partition          boot[/COLOR]**
**[COLOR=#b22222]4      93.2GB  93.2GB  1049kB                                                bios_grub[/COLOR]**
5      93.2GB  111GB   18.3GB  ext4
6      111GB   120GB   8547MB  linux-swap(v1)


Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
**[COLOR=#b22222]1      1049kB  211MB   210MB   fat32        EFI system partition          boot[/COLOR]**
2      211MB   345MB   134MB                Microsoft reserved partition  msftres
3      345MB   1000GB  1000GB  ntfs         Basic data partition          msftdata
```

The partitions (/dev/sda3 and /dev/sdb1 ONLY) I have painted red above have 'boot' flags. Remove them. You can remove them with Gparted booted Live.
Also remove the 'bios_grub' flag on /dev/sda4.
In Gparted select the partition you need to work on, Right Click -> Select 'Manage Flags' -> uncheck 'boot' and close. Apply Changes.

I think those flags are confusing the boot. 
Also which one is your Windows C: partition, the 92Gb on HDD1 or 1000Gb on HDD2?

---

### Post by ajdlc47 on 2014-01-30
My Windows is on the C: 92gb partition. The other partition is just a storage partition. Okay so I just removed the flags. I am going to try and boot into Windows now.

Fantab, you are genius! Thank you so much for your help. I have my Windows back and my Ubuntu works fine! Thank you, thank you, thank you! :)
One last question, should I do anything at this point? Or am I good to go?

---

### Post by fantab on 2014-01-31
Congrats! I am glad that boot issue is resolved.

> **ajdlc47 said:**
> 
One last question, should I do anything at this point? Or am I good to go?

Nothing really, you are good.
However, making a backup of your EFI partition, ie. /dev/sda1 will be a good idea. 
You can use [This Tool]("http://www.macrium.com/reflectfree.aspx") to do so, read [documentation]("http://kb.macrium.com/Popular.aspx") for more help, but you can use ANY good partition backup tool.

---

