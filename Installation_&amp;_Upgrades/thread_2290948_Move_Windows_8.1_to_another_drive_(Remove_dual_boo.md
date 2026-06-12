---
title: "Move Windows 8.1 to another drive (Remove dual boot)"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by markf2 on 2015-08-16
1. I installed Lubuntu 15.04 alongside my existing Windows 8.1. I no longer boot Windows.
2. I would like to move Windows to another hard disk (external USB enclosure I can boot if I ever need to run Windows.).[INDENT]2a. I would like to remove grub from that external drive if that's a learning experience.[/INDENT]
3. I want to delete Windows from my internal drive. Not sure if that involves deleting any of the first 3 (small) partitions, editing grub.cfg, etc.

The following is what I have. The [COLOR=#ff0000]red devices[/COLOR] are the [COLOR=#ff0000]small boot partitions[/COLOR]. The [COLOR=#0000ff]blue devices[/COLOR] are the [COLOR=#0000ff]Windows drives[/COLOR] I want to move. (I am keeping the two black devices.).[INDENT][COLOR=#ff0000]sda1[/COLOR] is type "Microsoft Windows Recovery" and contains directories "Recovery" and "RicaTools." directories.
[COLOR=#ff0000]sda3[/COLOR] is type "Microsoft Reserved" and contains a directory "System Volume Information"[/INDENT]

```
$ lsblk -f 
NAME   FSTYPE LABEL  UUID                                 MOUNTPOINT
sda                                                       
&#9500;&#9472;[COLOR=#ff0000]sda1 ntfs   System 2EA6CB62A6CB2963[/COLOR]                     
&#9500;&#9472;[COLOR=#ff0000]sda2 vfat          2CCC-4E68                            /boot/efi[/COLOR]
&#9500;&#9472;[COLOR=#ff0000]sda3 ntfs          9EEACDA0EACD74D5[/COLOR]                     
&#9500;&#9472;[COLOR=#0000ff]sda4 ntfs   System 0818CFA418CF8EDE[/COLOR]                     
&#9500;&#9472;[COLOR=#0000ff]sda5 ntfs   Data   C81075CD1075C34C[/COLOR]                     
&#9500;&#9472;[COLOR=#0000ff]sda6 ntfs   Music  346C8B956C8B5092[/COLOR]                     
&#9500;&#9472;sda7 ext4          e47a517e-7184-472a-97ef-bc1656318fc8 /
&#9492;&#9472;sda8 swap          16807d6c-b3d7-4207-a654-6376a3e9ef19 [SWAP]

```

Using *gparted,* I partitioned the external disk as GPT and created the exact sized partitions of the first 6 partitions (sda1-6). And then used *gnome-disks* "Create (& Restore) Disk Image" on those 6 partitions.

It didn't seem to work perhaps due to those partitions having the same (duplicate) GUID/UUID values. I replaced the internal disk. But, it wouldn't boot. I saw an error flash on the screen a couple times about /EFI (something, blah) but it was too fast to read it. It just sat there on a black screen.

I spent all day yesterday on it. 

Can someone tell me what to do? It seems like it should be simple. I'm probably looking at something wrong. (I don't understand how EFI, GRUB and EPT work together. I wouldn't mind removing GRUB from that external Windows-only disk. But, I don't mind learning how to make it work with GRUB either.). I don't understand if the external drive should be MBR (and not copy the first 3 small partitions?). 

Thanks. I wasn't sure where this fits in the forums. Since it's something of a post-install change to the installation. I thought it fit here.

**EDIT:** I notice others include bootinfo. I pasted it [here]("http://paste.ubuntu.com/12103030/").

---

### Post by oldfred on 2015-08-16
You cannot boot Windows from USB, it is designed to check and only boot from internal drives.
But you can back it up to external drives.

With gpt you are not supposed to copy partitions, but can copy entire drive. Gpt partition table & internal data in each partition seem to have data that if copied by partition would then not match.

You show a grub menu entry to boot Windows but it now is not showing any Windows boot files or a Windows install? Sometime script does not always see everything?
You also show several NTFS partitions. If not booting Windows you need to backup & reformat to a Linux format, or make sure you have a Windows repairCD or flash drive so you can run Windows fixes like chkdsk on NTFS partitions. You cannot do that from Linux.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by markf2 on 2015-08-16
> **oldfred said:**
> You cannot boot Windows from USB, it is designed to check and only boot from internal drives.
But you can back it up to external drives.

With gpt you are not supposed to copy partitions, but can copy entire drive. Gpt partition table & internal data in each partition seem to have data that if copied by partition would then not match.
Thanks! I didn't realize Windows can't be booted from a USB drive. Nor that cloning GPT partitions is a problem.

I still want to put my Windows 8.1 partition on the other (smaller) drive so I can at least swap it into my laptop (internal drive) and get back to Windows if I ever had to.

How can I do this? I've read about using dd to copy partitions. But, you seemed to say it's not ok to do that with GPT drives? 

A lot of the google results I see don't distinguish between GPT and MBR, so I'm never sure if what I read is applicable. I can't use Clonezilla because the target drive is smaller (and I think you said I shouldn't clone individual partitions?).

Thanks again.

---

### Post by oldfred on 2015-08-16
I have never used any of the cloning tools. And you cannot use dd as dd really is for same size to same size. It will not work to go from larger to smaller.

But I thought the Windows backup tools worked also with UEFI which is gpt by default.
There are some ways to edit/repair gpt partition issues. That may be required after a copy. 
But as long as both drives are not installed or used at same time, that copy is same GUIDs and UUIDs would not be an issue.

Some more details:
 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

---

### Post by yancek on 2015-08-16
> Thanks! I didn't realize Windows can't be booted from a USB drive.

Makes sense as it can't be installed to a USB drive.  If you try, you will get the message below:

> windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports

---

### Post by ubfan1 on 2015-08-17
I successfully used Macrium Reflect (free copy of new release) to copy an EFI and running copy of Windows (gpt) partition from the internal hdd to an SDD.  The created SDD (on USB3) was then mounted internally, and booted with no problems.  Both disks were gpt, the Windows moved was 8.1.  I subsequently updated the SDD Windows to 10 without issue.

---

### Post by markf2 on 2015-08-19
I solved my conundrum. I'll describe what worked for me. There's probably a better way. But, this has been one of the most *mind boggling* things I've ever done. It should be simple. When I googled the topic there were so many different ways, and it never was clear if it involved Grub or not, or MBR vs. GPT, or EFI. I've never been this confused about a topic -- and I've had a computer since the original IBM PC!

Again, my environment is: GPT partitioned drive on a new'ish laptop with EFI (no bios/setup menu to access EFI entries). Lubuntu 15.04, Windows 8.1.  Goal was to 1) move Windows partitions to another drive so I could boot that target drive if I ever needed to access Windows again. And, 2) remove Windows from the source drive so I could expand my Linux partition, etc.

I made a lot of use of gnome-disks and gparted. These are in the application menu (Preferences and System tools). But, it was never clear to me what I can do with these if I invoke them through the menu. So, everything I did was from an LXTerminal window (System tools), starting those two apps as "sudo gnome-disks" and "sudo gparted /dev/sda" 

Note: It's helpful to pass the device to gparted because it's as SLOW as working with an old 1.44mb floppy drive. Unbelievable! You'll spend an hour doing basic tasks the way it takes so long to refresh itself *over and over* again. OMG! Pass one or two devices on the command line to limit what it's working with. I also read something in the [gparted FAQ saying you can kill a process]("http://gparted.org/faq.php#faq-11") to make it work faster. I can't say I noticed that worked. But, I may have done it wrong.

**1.** I used gparted (Device->Create partition table) to create a GPT partition on the target disk. (The source is GPT. So, I assumed this is what I need.).

**2.** I copied the partition schema using:
[INDENT][I]sudo sgdisk -R /dev/(target) /dev/(source) 

[/I][/INDENT]
It's **very important** to understand that the order of devices or you'll wipe out your source drive. It is **target first** (then source). If your source is sda, and your target is sdb, then you'd specify them as sdb sda (in the command above). 

Before using this command, I used gparted to shrink partitions down to a cumulative size which could fit on the target. Then I moved the partitions to the front of the source drive, making *all* the unallocated space exist after the partitions. (There may be a small unallocated space at the front. I left that alone. It might involve booting.). I also had one partition with data that I could move to an external drive, allowing me to get rid of that partition on the source drive so sgdisk wouldn't' see it. Note: gparted warned me that moving the Windows and Linux partitions would make fail to boot. I went ahead and did it. It didn't seem to cause a problem. (I did have a problem, but I believe it was due to something else. It's discussed below.).

Sgdisk erred at the end about the target drive not having enough space to hold the unallocated space of the source drive. This didn't seem to be a problem (yet.).

If I were going to use the target drive with the source, I would probably have to run: sudo sgdisk -G /dev/sd(target) to randomize the UUIDs of the disk and all its partitions. It's probably good practice to do that. But, I don't know what that might have done to Grub (if the boot process depends on the UID.).

Afterthought: I've been thinking: if the source disk had any partitions at the end (extending beyond the size of the target disk), and I didn't need those partitions on the target disk, it's possible sgdisk would have simply erred on those like it did the unallocated space. If I were doing it again, I would try that.

**3.** I formatted each target partition to the same format as the source.

I used gnome-disks but my grub partition is fat32 and gnome-disks didn't have that option. I used gparted to format it. Maybe I should have used gparted for everything. Or, maybe it wouldn't have mattered if it was fat16.

**4.** Now I had the target drive with partitions equal in size to the source, same formats. But, it seemed the metainfo wasn't the same. Labels, flags, mount options. 

I went through gnome-disks and gparted, comparing each partition to see if it was the same, changing boot flags, labels.

I wasn't very confident about what I was doing, especially with the mount options in gnome-disks. Also, I got confused about the swap disk. I thought it was mounted. To unmount it I turned swap off. I think I had to do that to get to the mount options too. I think I should have left swapon. 

I think I damaged something on the source drive when I was clicking back and forth comparing things. So, be careful here. I wasn't confident how exactly "the same" each partition had to be, or if I was making things worse by trying to make them the same. 

**5.** Now I had drives with partitions that appeared to be exactly the same. Now the question is how to get the data there.

This is one of the more frustrating aspects. I found recommendations to use dd, rsynch (tar, cat, cp). But, none of them seemed to be endorsed with great confidence. Someone always pointed out how "without this flag.... "

Somehow I realized gparted has a copy/paste feature. I right-clicked a source partition and chose "copy", then right clicked the corresponding target partition (and "paste").

gnome-disks has a create/restore partition image too. This might have worked.

I saw many references to clonezilla working if you resize/move all your partitions to make the source drive's actually allocated space fit within the target's drive's capacity. It apparently involves choosing advanced options during the device-to-device operation, and choose "-icds" (and also "-k1" if an MBR partitioned drive, which mine isn't). I couldn't get it to work. 

I also saw a thread with [step-by-step instructions (with screenshots) for using the free MondoRescue]("http://askubuntu.com/questions/409204/how-to-clone-to-a-smaller-harddisk"). I would have probably done this if I hadn't stumbled upon gparted's copy/paste feature.

**6.** I now have a target drive which should boot like the source.

However, I wanted to boot the source *once* because I had a bad feeling about all the clicking back and forth I did, checking the metainfo. I was afraid I updated the wrong drive a time or two. 

Indeed, the source drive wouldn't boot Linux. It seemed to be a grub error. I think I screwed something up with the mount options in gnome-disks.

[INDENT]**6.1** I booted my Lubuntu install thumb drive (created by using unetbootin to write the .ISO to the thumb drive).

I googled and found this [easy-to-follow instruction to reinstall/update(?) grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") from the LiveCD session's grub. But, it didn't work. I got an error about xxxx_x64.efi (something or other) not being found. 

I googled more and learned about an [installable package named boot-repair]("https://help.ubuntu.com/community/Boot-Repair"). I installed it with these commands, which also start the program:

[/INDENT]
[INDENT=2]*sudo add-apt-repository ppa:yannubuntu/boot-repair*[/INDENT]
[INDENT=2]*sudo apt-get update*[/INDENT]
[INDENT=2]*sudo apt-get install -y boot-repair && (boot-repair &)*[/INDENT]
[INDENT]
I chose the "Recommended repair" and my Linux rebooted just fine. My grub menu has some junk in it. But, that will be a different learning experience.[/INDENT]

**7.** Now that my source drive boots to Linux, I replaced it with the target drive and it booted Windows without incident.

Within Windows I right clicked the "Computer" icon on the desktop and chose "manage." I went into the disk management option and deleted the Linux partitions. Rebooted, and Windows booted fine.

I'm not sure I even needed to copy the Linux partitions to the target. But, I read a lot of things saying grub might not work if something like a Windows system partition is removed. If I had to do this again, I'd try it without the Linux partitions (instead of copying them and then deleting them from Windows). 

I originally wanted to remove grub from this disk. But, my head hurts and I don't care anymore. (It just shouldn't be *this* complicated.).

**8.** I replaced the target disk with the source disk, and booted my Linux, then deleted the Windows partitions using gnome-disks.

Rebooted, no problem.

Then booted from the Lubuntu install stick (again) and used gparted there to resize the Linux partition to use more of the space. 

**9.** Other stuff.

**9.1.** I'd like to remove any unneeded boot partitions from the Linux drive (the source, now without Windows). I seem to have 3 small ones at the front of my drive. I believe the 2nd is grub. But, I don't know if I can delete the 1st and 3rd. 

**9.2.** I don't know how to update my Grub, but I'm sure I'll figure it out. I read somewhere that computers store something EFI-related in non-volatile memory, and that it should be removed when changing drives or boot partitions. Some computers give you a menu to do this in their "bios/setup" (EFI isn't really bios, but that's what people think of the setup being.). 

There is a command named efibootmgr -v which shows the NVRAM EFI entries. And, -B #### will delete it. 

I don't know if I need to do anything in that regard. [This thread talks about it]("http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader").

**9.3** Some commands that might be helpful while doing this:

[INDENT]e2label device [label] <<< sets disk label
ls -l /dev/disk/by-label <<< see all devices and label values (use "by-uuid" to see that).[/INDENT]
[INDENT]lsblk -f <<< shows a lot of info about the disks[/INDENT]
[INDENT=2]<<< use -o to see the field labels you can specify following the -o)[/INDENT]
[INDENT]fdisk -l <<< more disk info
parted /dev/sda <<< then press "p" to see more disk info.
gdisk /dev/sda <<< press "i" to see even more disk info.

[/INDENT]
**10.** Additional tools.

In addition to the boot-repair package mentioned above (and the free [MondoRescue]("http://www.mondorescue.org/")), the free [System Rescue CD]("http://www.sysresccd.org/SystemRescueCd_Homepage") looks like something I'll try next time.

---

### Post by oldfred on 2015-08-19
Your ESP - efi system partition, now partition on each drive should have folders for both Windows & Ubuntu. On Windows drive you can delete Ubuntu folder and on Ubuntu drive delete Windows folder in ESP. Then you can delete entries in UEFI.  

Windows also requires the system reserved partition which gparted usually shows as an error as it is unformatted.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


But you may not have to delete all entries in UEFI. Often removing or disconnecting drive will cause UEFI to reset and remove entries from that drive. Or you may have to add a Windows entry back into UEFI next time you plug it in.

You cannot boot with both drives connect as the duplicate UUID & GUID will cause conflicts. 
I would still suggest a full backup of Windows with Macrium Reflect.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

