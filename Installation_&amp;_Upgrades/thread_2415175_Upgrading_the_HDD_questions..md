---
title: "Upgrading the HDD questions."
date: 2019-03-21
forum: Installation &amp; Upgrades
---

### Post by pielam on 2019-03-21
HI,  all,

I recently acquired a new & bigger SSD. I was needing to know if someone would help me with The OS installation. I would prefer using a GUI over the terminal since my typing is problematic at best. But if that isn't possible, that's cool too as long as I can copy  & paste that is.
    

Currently my Ubuntu Mate 18.04 system is configured as follows:
--- a 120 gb SSD with the entire OS loaded (USR & all system folders). This SSD uses the native Linux file system (Journal 4 ???) [new to Linux so I don't always remember the exact terminologies]
--- a 500 gb HDD (the old mechanical kind).  I used this drive in the past as a Win 7 storage drive. It has lots of old files on it & it's in the native Win OS format(NTFS). I plan on replacing this drive with the new SSD. I have no plans for it at the moment.
    

What I had in mind doing, once the new SSD is physically installed was to disconnect the 120gb SSD & then load the Ubuntu MATE OS as I did before from either a bootable flash drive or from a bootable DVD.(currently, my USB ports aren't working correctly. That's another issue for me to deal with later).
    
From this point I'm not sure how to proceed. I want to boot from the new SSD with the old 120 SSD in the system as storage for pix or music or ???. 
    
After installing Ubuntu on the new SSD, the old SSD and the new SSD will both be set as prhttps://uk.news.yahoo.com/bercow-sparks-commons-uproar-aiming-040539938.htmlimary boot partitions. Obviously, the old SSD will have to be modified somehow, right? But how?
    
That is my dilemma for now… Can I get some expertise on this?

---

### Post by TheFu on 2019-03-22
I'm not sure if you want 1, 2, 3 storage devices connected when everything is done. I'm easily confused.

Cloning partitions is easy, lots of different ways - dd, ddrescue, partimg, clonezilla, gparted, fsarchiver.  When cloning the partitions, it really needs to be done from from a flash/usb/cd/dvd boot anyways.
After you clone them, the fstab needs to be updated for the new UUIDs of the mounts you want. Search for "ubuntu fstab" for an article at help.ubuntu.com about that.  If you make a mistake in the fstab, you'll need a live-boot USB/CD/DVD to go in rescue mode, mount the correct partition from the correct device and fix/correct the fstab entry. 

We'll need specific facts. The easiest way to post those facts are to connect up all 3 disks, then boot into any Ubuntu, install **boot-repair**, and run it.  Don't try to repair anything, just gather data/facts. There's a button on the bottom center of the page that gathers the boot-info data and posts it to a URL.  Post the URL back here, please.

Also, using device names like sda1, sdb4, etc, say what you want old --> new.

Please use the default fonts, sizes and colors when posting here.

---

### Post by oldfred on 2019-03-22
Drive order is normally set by SATA port order. Or SATA0 becomes sda, SATA1 is sdb etc.
So best to keep drives in SATA port order.

If you do a new clean install, you will not have issues, but if you clone drive, you cannot keep both drives connected as duplicate UUIDs are not allowed. You can change UUIDs, but then if you want old install to work, you have to reinstall grub and edit fstab amoung other updates.

Is system UEFI or BIOS and is current install UEFI or BIOS?

If USB ports do not work, really time for system or motherboard. You really need to have Ubuntu live installer on a flash drive to make repairs. I used to use DVDs years ago, and have many coasters. I actually used some of those bad DVDs as coasters. Flash drives are re-usable.

---

### Post by pielam on 2019-03-25
[FONT=arial][I]
I'm not sure if you want 1, 2, 3 storage devices connected when everything is done.[/I]

  Sorry, I'll try to be clearer…
  Just 1 additional storage drive). I'm only wanting to re-use my current SDA drive C: ). My current SDB (my second drive D) will be shelved for now…(while I decide what to do with it)
  
  Both of these disks are single partitioned. My  current SDA is Journal 4 while my current SDB is NTFS.
  
  *Cloning partitions is easy*
  
  Good to hear, unfortunately, I'm not so sure if that approach will work for me.
  
  *lots of different ways - *
  
  Any recommendations?
  
  *When cloning the partitions, it really needs to be done from from a flash/usb/cd/dvd boot anyways.*
  
  Yes, I can imagine that it would…
  
  *After you clone them, the fstab needs to be updated for the new UUIDs of the mounts you want. Search for "ubuntu fstab" for an article at help.ubuntu.com about that. If you make a mistake in the fstab, you'll need a live-boot USB/CD/DVD to go in rescue mode, mount the correct partition from the correct device and fix/correct the fstab entry.*
  
  Now, I'm confused. Slow your roll, partner.   :D   I think you're forgetting that I'm new to Linux & Ubuntu. Yes, I'm familiar with a lot of techniques & procedures (not all, though) but what I do know is **all **MS Windows & MS DOS based. Also, I'm just starting to learn more about *BIOS & UEFI* based systems. There's a lot of the newer stuff that I'm still learning about.

  To summarize, let's just say that I'm very old-school & have lots of catching up to do. :KS

  *We'll need specific facts. The easiest way to post those facts are to connect up all 3 disks*
  
  I can do that. Does it matter that the 3rd drive would be blank?
  
  *then boot into any Ubuntu*
  
  Gotcha…
  
  *install boot-repair, and run it.*
  
  OK, but how? Never heard of "boot-repair". Sorry, but what is it & how would I get it?

  *Don't try to repair anything, just gather data/facts. There's a button on the bottom center of the page that gathers the boot-info data and posts it to a URL. Post the URL back here, please.*

  Now that sounds like something I can do, maybe. LOL

  *Also, using device names like sda1, sdb4*

  Done, hope it helps. Fortunately, I've learned the Linux naming conventions a while back.

  *say what you want old --> new.*

  Sure, no problem:

  **OLD **(Current setup:

  SDA : 120gib SSD, single partition set as Journal 4 file system, entire Ubuntu MATE 18.04 on this one drive.

  SDB : 500gib old slow traditional mechanical spinning drive, single partition set as NTFS, was once a storage disk when its PC was running MS Windows 7. (will remove from system once the new configuration is set up)

**NEW**:

  SDA : 1tb SSD, Single partition set as NTFS (for USB compatibility reasons), will contain most, **but not all,** of the Ubuntu OS.

  SDB: (the old SDA) it will be used for storage of MP3s & photos, single partition set as NTFS (for USB compatibility reasons as well ??? )

  *Please use the default fonts, sizes and colors when posting here. *

  If it makes it easier for others, I certainly will, no problem. I didn't think what I used was overly obnoxious. The reason I changed the defaults was to make it easier for me to read since I have  a visual impairment. My eye Dr. classified me as "legally blind".

  I failed to mention this in my original  post, sorry. I didn't think it was necessary to mention, but I was wrong, obviously.

BTW, I compiled this reply using MS One Note for legibility reasons(mine) & mostly because it has a spell checker that catches **most **of my typos.

If the look of this post is nonconforming or breaks something, I'll happily conform my replies to the default settings.

[/FONT]  [FONT=Calibri] 
[/FONT]

---

### Post by oldfred on 2019-03-25
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Only keep NTFS if you have a working Windows install, or at least a Windows repair flash drive. You cannot run chkdsk nor defrag from Ubuntu. And Windows will not run from a USB drive.

---

### Post by pielam on 2019-03-25
[FONT=arial]*Drive order is normally set by SATA port order. Or SATA0 becomes sda, SATA1 is sdb etc.*
  
  Makes sense, got it. I wasn't sure about that.
  
  
  *If you do a new clean install, you will not have issues, but if you clone drive, you cannot keep both drives connected as duplicate UUIDs are not allowed. You can change UUIDs, but then if you want old install to work, you have to reinstall grub and edit fstab amoung other updates.*
  
  Sounds like you understand more about what I'm wanting to do. It also sounds like, although doable, it might be more than I can handle at this point. :(
  
  *Is system UEFI or BIOS and is current install UEFI or BIOS?*
  
  I'm a little fuzzy about this on that particular PC. Originally, when I first built that PC, about 3 years ago, it was just a budget build using mostly parts that I had left over from other projects. It was also just a secondary system. Not my daily primary system. Therefore, a lot of the details that I would ordinarily know, I either don't remember at all or just faintly remember. Anyway, I THINK it's a BIOS system. Is there an easy way to know which one it is?
  
  *If USB ports do not work*
  
  That's just it, I think they actually do work. I plan on testing this later.
  
  Here's the low-down:
  When I first installed Ubuntu, it was from a bootable Flash Drive (FD) with the 18.04 MATE ISO on it, no problems. ALL my FDs (I have several) use FAT32. Ubuntu does not see any of them, but does see my USB floppy drive & also sees my SDB even though right now, I'm not using SDB for anything at all.
  
  When I installed Ubuntu, I mistakenly opted to use the Journal 4 file system not knowing that my FAT32 FDs would no longer work in Ubuntu, but would work in a Windows OS. I'm pretty sure, but not certain that my FDs would work if I used NTFS in Ubuntu. What are your thoughts on this theory?
  
  *Please use Thread Tools above first post to change to [Solved] when/if answered completely.*
  
  I plan on doing that, hope I don't forget… Thanx for the reminder…[/FONT]

---

### Post by oldfred on 2019-03-25
The ext4 format for the Linux / (root) partition would have nothing to do with not reading USB FAT32 flash drives.
But if you used flash drive as an installer, it may depend on what tools you used to create installer. Many now use dd or dd under the hood to create a hybrid DVD/flash drive configuration that is not a normal FAT32 format. And gparted and other tools then do not correctly see the hybrid drive as it does not have a partition table. You have to erase the beginning of drive, so then partition tools can create partitions.

Windows required vendors to install  new systems with UEFI and gpt partitioning back in 2012 when Windows 8 was released. The Windows 7 installer was updated to offer UEFI install also. Users could install in either UEFI or BIOS. Some large users wanted old BIOS mode for compatibility with other systems.
But if older hardware, it may not have UEFI as an option.

Both Ubuntu & Windows install in the boot mode UEFI or BIOS that you boot install media in. Old systems only have BIOS, but UEFI can boot in either mode, but may require additional UEFI/BIOS settings for one or the other which can make it a bit more complicated.

---

### Post by TheFu on 2019-03-26
One key difference between Windows and all Unix-like OSes is that file systems are very important.  Ubuntu cannot be installed to NTFS.  Also, Windows tends to call things "drives" but they aren't.  They are partitions. This is VERY IMPORTANT.

sda = whole drive
sda1 = 1st partition on sda.
sda2 = 2nd partition on sda. 
.....
sda99 - 99th partition on sda. Even more are possible thanks to GPT.  MBR or MSDOS partitions are limited to 4 'primary' partitions and some number of 'logical' partitions inside 1 of those primary ones.

In Linux, NTFS can only be used for data directories, not the OS and not /home/.  If you plan to do any programming or scripting on Linux, then those directories need to be on Linux file systems too, though for certain languages, it is *possible*, it is never a good idea.  I agree with Oldfred about avoiding NTFS and FAT-whatever unless you absolutely must have it.  Linux file systems (and there are 30 different choices), have features that NTFS doesn't.

Also, in a small system, SATA ports might happen to align with device names, but that is NOT guaranteed.  It is based on which disk controller is "discovered" first during the boot process.  This is why Linux switched to using UUIDs long ago.  At every boot on systems with multiple HBAs (host bus adaptors - a fancy name for disk controllers), the order that adaptors are found can change.  sda might be sdj next boot on some systems.  There are a few techniques to get a specific disk mounted without having to trust the sda, sdb, sdc ..  order.   UUIDs is one.  Disk LABELs is another.  There are also by-path techniques which tie the HBA and port on the HBA into the mount. For example:

```
posc:/dev/disk$ ls
by-id/  by-partlabel/  by-partuuid/  by-path/  by-uuid/

/dev/disk$ find by-path/ |sort
by-path/
by-path/pci-0000:00:1f.2-ata-2
by-path/pci-0000:00:1f.2-ata-2-part1
by-path/pci-0000:00:1f.2-ata-2-part2
by-path/pci-0000:00:1f.2-ata-2-part3
by-path/pci-0000:00:1f.2-ata-5
by-path/pci-0000:00:1f.2-ata-5-part1
by-path/pci-0000:00:1f.2-ata-5-part2
by-path/pci-0000:00:1f.2-ata-5-part3
by-path/pci-0000:00:1f.2-ata-6
by-path/pci-0000:00:1f.2-ata-6-part1
by-path/pci-0000:05:00.0-usb-0:1:1.0-scsi-0:0:0:0
by-path/pci-0000:05:00.0-usb-0:1:1.0-scsi-0:0:0:0-part1
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:0
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:0-part1
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:0-part2
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:0-part3
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:1
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:1-part1
by-path/pci-0000:05:00.0-usb-0:2:1.0-scsi-0:0:0:1-part2

```
This can be extremely handy when there are multiple HBAs in a system and device names are changing. The path will not change without a physical modification.

So instead of using /dev/sda1 in the fstab, I could use .... let me find the right one ... ```

$ find by-path/ -ls |grep sda1
      504      0 lrwxrwxrwx   1 root     root           10 Mar  2 10:43 by-path/pci-0000:00:1f.2-ata-2-part1 -> ../../sda1
```
So the answer is ... /dev/disk/by-path/pci-0000:00:1f.2-ata-2-part1 for the fstab. This assumes sda1 is a partition with a file system.

Anyway, the point is that device names aren't fixed, not 100% for certain.

---

### Post by TheFu on 2019-03-26
boot-repair URL?  This is important.

And you can probably ignore my prior post for now. Just note that sda and sdb aren't always in that order on all systems with every boot. That's the important part. USB drives move around all the time.

---

