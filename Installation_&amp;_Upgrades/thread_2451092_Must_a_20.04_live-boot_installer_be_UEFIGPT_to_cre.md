---
title: "Must a 20.04 live-boot installer be UEFI/GPT to create a UEFI/GPT SSD install?"
date: 2020-09-26
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2020-09-26
I'm trying to create a UEFI/GPT live-boot USB drive to install 20.04 in UEFI/GPT mode.

I have  a USB drive (with no .iso on it) that is formatted thusly: 

Its partition table is GPT.  

It has a 200 MB empty space at the beginning; 

It has a 1 GB, fat32 ESP partition (sdc1) with boot and esp flags enabled; 
(this partition already has some files and folders in it (from a previous attempt): boot folder, casper folder, EFI folder, README.diskdefines file, and .disk folder)

This flash drive also has a 6 GB, ext4 partition (sdc2) where the 20.04 installer will go; and a 2 MB empty space at the end.

I just tried to use Unetbootin to install an ubuntu-mate-20.04.1-desktop-amd64.iso onto ***sdc2***, and it hung. (It *is* an EFI image.)

I have a feeling  that this is not the right way (or right location) to put the .iso on this USB drive.  

Because if I install the .iso onto*** sdc2***, I don't know that the boot files will detect the ESP partition (sdc1).

But, as  indicated above, I already have boot files in the ESP  partition from a previous attempt.  Should I delete them before running  Unetbootin to put the .iso on the flash  drive to make it live-boot?

Because my last attempt hung, I now have some of the iso's files on the flash drive, but I'm thinking I should delete them and start over.  However, it appears that Unetbootin only allows to install the  .iso on either sdc1*** or*** sdc2. 

(I was thinking that if  I  could choose just*** sdc***, that Unetbootin would detect the ESP partition I already have, and install the boot files there. 

How can I  get  the .iso onto a flash drive so that I have a working UEFI/GPT installer, ready to create a UEFI/GPT SSD install?

---

### Post by oldfred on 2020-09-26
Some installers use dd (or dd hidden under the hood) to create an unpartitioned hybrid DVD/flash drive installer.
Others extract the ISO to a FAT32 formatted partition. If BIOS boot also requried, they add a BIOS boot loader to flash drive.
It is possible  to use grub2's loopmount command to directly boot many ISO. ISO has to be configured for grub's boot.  You have to have grub and manually create the correct boot stanza to boot the ISO which can be in any partition. 

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Tools often recommended:
rufus,mkusb, iso2usb,unetbooting, balena etcher

---

### Post by C.S.Cameron on 2020-09-27
Does the USB currently boot to a GRUB menu?
If so then you can put your ISO on your ext4 sdc partition and add a menuitem for it in sdc1's grub.cfg.

See: [https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782](https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782)

It might be easier to overwrite the USB with a Rufus UEFI install which will guarantee an UEFI install to the HDD if Partition scheme: GPT is used with Target system UEFI (non CSM) options.

---

### Post by watchpocket on 2020-09-27
So far what I've done is, I've taken another (8 GB) USB flash drive (different than the one I was using in my first post), and created a bootable Ubuntu UEFI (I hope UEFI) USB drive, according to [this tutorial]("https://techbit.ca/2018/09/creating-a-bootable-ubuntu-uefi-usb-drive/"), which uses the "Disk" utility.

(Elsewhere, Rod Smith, btw, [advises against using Unetbootin]("https://www.rodsbooks.com/linux-uefi/") to create a UEFI install media.)

This boots to a grub menu where I can choose "Try Ubuntu before Installing."  I select that, and it does boot into the full 20.04 interface.  But *before *that happens, I get a worrisome error message at the top of a black screen: 

[I]**"4.7413[**a few other digits here[B]] Initramfs: packing failed, decoding failed"

[/B][/I]But then it does go ahead and boot into the trial 20.04.  I noticed in gparted that this USB drive's partition table is msdos.  Does the USB drive's partition table need to be GPT to successfully install onto an SSD in full UEFI/GPT mode?  

Given that error message, I wonder if I should try to do  an installation to my SSD with this USB drive?  

I may just want to start over and re-create a USB installer without such errors.

---

### Post by oldfred on 2020-09-27
I now only use gpt for everything. But have used gpt for all new drives since about 2010.

Some installers only create a BIOS boot if MBR and only UEFI if gpt.
Most can be either partitioning and boot in either mode. It depends on install tool used. Not sure about Disks. Not seen many use it.  I only use Disks to add labels to partitions as have seen it not do things as well as gparted for partitioning.

You may need to check that download was correct. But now it verifies as part of boot of live installer. That may have been issue?

 md5sum (older versions) or sha256sum (new versions)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)
[https://ubuntuforums.org/showthread.php?t=2449090](https://ubuntuforums.org/showthread.php?t=2449090)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) &
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by sudodus on 2020-09-27
The advice how to make the USB boot drive depends on your answer to the following questions:

0. What is the size of the USB drive? (From your description I think 8 GB, but I may be wrong.)

1a. Are you making the USB boot drive in Ubuntu or some other linux distro?
1b. Or are you making the USB boot drive in Windows or in MacOS?

2a. Is it enough to get a live (live-only) USB boot drive, that can boot in UEFI mode (and run live sessions and install Ubuntu)?
2b. Or do you need a live system, that can store data past shutdown/reboot, a persistent live drive?
2c. Or do you want an installed system (like installed in an internal drive, but in a USB drive)?

3a. Is it enough, that the drive can boot in UEFI mode?
3b. Or should it boot also in BIOS mode (alias CSM alias legacy mode)?

Edit:

> 
"4.7413[a few other digits here] Initramfs: packing failed, decoding failed"


This output can be printed but the live session will work anyway. You need not worry too much about it (in a *live* session).

---

### Post by watchpocket on 2020-09-27
> **sudodus said:**
> The advice how to make the USB boot drive depends on your answer to the following questions:
0. What is the size of the USB drive? (From your description I think 8 GB, but I may be wrong.)

Correct.  I'm using an 8 GB USB drive.  I've been led to believe that using a smaller-capacity USB drive for this install might not provide enough space for creating a functioning live-boot drive, at least in this instance.

> 1a. Are you making the USB boot drive in Ubuntu or some other linux distro?

I am trying to creating a USB boot drive in Ubuntu-MATE 18.04.4 on a desktop workstation.
 
That workstation has  2 internal one-terabyte SSDs.  One of those SSDs has the 18.04 install (which  is my current working system and which boots via BIOS); the other SSD is just for storage, not for booting into an OS.

> 1b. Or are you making the USB boot drive in Windows or in MacOS?

**No Windows, ever.  No MacOS.  I do not use those platforms **(unless I'm in out in some company office).  I don't dual-boot Ubuntu with Windows or Mac. I use the Ubuntu-MATE distro. 

 I'll eventually set up dual-boot of Ubuntu-MATE **20.04** LTS and Ubuntu-MATE **22.04** LTS (see below). Those  Ubuntu-MATE OSs will be on separate, internal SSD drives.

> 2a. Is it enough to get a live (live-only) USB boot drive, that can boot in UEFI mode (and run live sessions and install Ubuntu)?

My goal is to get a live USB boot drive working ***for the purpose of* ** installing ***a UEFI/GPT***  Ubuntu-MATE 20.04.1 onto an external, standalone one-terabyte SSD.  That SSD will have one big partition (root and /home) and a bit of free space at the  beginning and end. Very simple.  

This external drive will then replace my current *internal* 18.04 Ubuntu-MATE install.  (And I'll then put the 18.04 drive in an external enclosure.)

Because of the bug where UEFI apparently installs boot files on the first drive it sees,  I plan to physically unplug both of my current two internal SSDs when I do this UEFI/GPT install.  

The install will go directly from the plugged-in live-boot USB flash drive to the connected external SSD drive, with no internal drives present in the chain to muck up the install.

Much, much later I will have a separate (one-TB) internal SSD with Ubuntu 22.04 installed on it.   Then, both my internal 20.04 drive and the future 22.04 internal drive will both be  UEFI/GPT.  This is the plan for going forward that I'm trying to get started now.

> 2b. Or do you need a live system, that can store data past shutdown/reboot, a persistent live drive?

Yes, as stated above.

> 2c. Or do you want an installed system (like installed in an internal drive, but in a USB drive)?

Ultimately it will be an installed system on an internal SSD drive (it's just that that drive is, at the moment, *external*).  The USB drive is ***only*** for the  purpose of putting a working UEFI/GPT 20.04.1 onto an external SSD drive that will soon be moved to inside my desktop workstation box.

> 3a. Is it enough, that the drive can boot in UEFI mode?

Yes. What I want is a working system that is a UEFI/GPT Ubuntu-MATE 20.04, on an SSD that will ultimately be internal and will be my working system.

> 3b. Or should it boot also in BIOS mode (alias CSM alias legacy mode)?

No.  I want to move away from BIOS to UEFI.  If I discover for any reason that the install *absolutely must be* BIOS as well, I suppose I would then want it to be -- if possible -- bootable via BIOS as well as UEFI.  But I don't think that'll be the case, and I'd like to avoid that.  My machine does have the capacity to boot via UEFI.

> This [error message] output can be printed but the live session will work anyway. You need not worry too much about it (in a *live* session).


Well, I get the willies when I see error messages like  that.  The USB drive does boot into the  trial 20.04, though.   I'll probably give it a try.


 I do have a question about the SSD drive I want to install to:  Is my current formatting of it correct or workable?

Right now I have that (empty) SSD  formatted like this:

(a)  its partition table is set as GPT; 
(b)  it has a  200 MB allocated empty space at its beginning;
(c)  its first partition  is a fat32, one-GB to be used as the ESP;
(d)  its second partition is the large (893 GB) partition where root and home will go;
(e)  it has a small (2 MB) unallocated empty space at its end.

Is this the way I can have the SSD drive set up ahead of running an installer on it, to create a UEFI/GPT SSD drive?  Will the installer put the boot files on what I have set up as the fat32 ESP drive?

Or should I delete all this and be creating the partitions as part of the install process?  I've already tried this install once with a previous 4-GB live boot USB key, instructing in the process NOT to wipe the drive, but UEFI did not appear in the partition-setup pop-up "use as" menu.  

(I think that previous key was set up to be a BIOS boot, and  thus didn't work for UEFI.)

---

### Post by dragonfly41 on 2020-09-27
> [COLOR=#000000]My goal is to get a live USB boot drive working for the purpose of installing a UEFI/GPT Ubuntu-MATE 20.04.1 onto an external, standalone one-terabyte SSD. That SSD will have one big partition & a bit of free space at the beginning and end. Very simple.[/COLOR]

I would just add that I would place an ESP Fat32 partition (500mbytes) before your Ext4 partition.
You can then use this to boot your SSD on its own when needed.
I have two external SSD's so configured (switched using rEFInd)..

---

### Post by watchpocket on 2020-09-27
Thanks. See what I just now added to the end of my post directly above.  I have the SSD (that  I want to install to) formatted that way now, but I need to make sure the install will go correctly.  I've been looking at rEIFInd also, I'll likely try to use it as well.

---

### Post by oldfred on 2020-09-27
Its Ubuntu's Ubiquity that will not let you choose where to install grub2's UEFI boot files.
You can do a work around, or reinstall grub after your install. Default will install /EFI/ubuntu into first drive seen. If you disconnect all other drives, either logically in UEFI or physically then it will install to your external drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is in the install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by sudodus on 2020-09-28
> **watchpocket said:**
> 
 I do have a question about the SSD drive I want to install to:  Is my current formatting of it correct or workable?

Right now I have that (empty) SSD  formatted like this:

(a)  its partition table is set as GPT; 
(b)  it has a  200 MB allocated empty space at its beginning;
(c)  its first partition  is a fat32, one-GB to be used as the ESP;
(d)  its second partition is the large (893 GB) partition where root and home will go;
(e)  it has a small (2 MB) unallocated empty space at its end.

Is this the way I can have the SSD drive set up ahead of running an installer on it, to create a UEFI/GPT SSD drive?  Will the installer put the boot files on what I have set up as the fat32 ESP drive?

Or should I delete all this and be creating the partitions as part of the install process?  I've already tried this install once with a previous 4-GB live boot USB key, instructing in the process NOT to wipe the drive, but UEFI did not appear in the partition-setup pop-up "use as" menu.  

(I think that previous key was set up to be a BIOS boot, and  thus didn't work for UEFI.)

- You need only 1 MiB unallocated drive space at the head end of the drive, unless you want something else to get the best possible alignment of partition boundaries. There may be special preferences for the SSD hardware.

- 1 GiB for the ESP is a waste of drive space. I think 256 MiB is enough.

- You need no bios_grub partition. But if you want to boot in BIOS mode, you need such a partition when using GPT. In that case 1 MiB is enough (unless you want something else to get the best possible alignment of partition boundaries).

See more details about partitioning at this link: [help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace).

[HR][/HR]
Edit:

There is a simple way to create a USB boot drive, that can boot both in UEFI mode and BIOS mode.

- Use the Ubuntu Startup Disk Creator, which ***clones*** the content from the Ubuntu MATE iso file to the USB drive.

The boot mode (UEFI or BIOS) is selected by the computer's built-in UEFI/BIOS system, and you set the preferred boot mode in a menu of that system. In most computers it is also possible to use a hotkey to get a temporary boot menu. (I think you know how to manage this in your computer. If not, please ask and we will try to help.)

The following command line can be used to check if Ubuntu MATE (any live or installed Linux system) is running in UEFI mode or BIOS mode:
```

test -d /sys/firmware/efi && echo efi || echo bios

```

---

### Post by watchpocket on 2020-09-28
Thanks for the responses.  I'll report back once I've performed a UEFI install (or install attempt).

---

### Post by watchpocket on 2020-09-29
> **oldfred said:**
> Its Ubuntu's Ubiquity that will not let you choose where to install grub2's UEFI boot files.
You can do a work around, or reinstall grub after your install. Default will install /EFI/ubuntu into first drive seen. If you disconnect all other drives, either logically in UEFI or physically then it will install to your external drive.
Posted work around to manually unmount & mount correct ESP during install #23 & #26.

The way I'm doing that work-around is by physically unplugging my non-target (internal) drives.  [I][B]

But there are other mysteries preventing me from doing a UEFI-GPT install.  [/B][/I]

Again, I am not dual-booting.  I'm installing Ubuntu-MATE directly from a flash drive installer to an external SSD.  Nothing else in the chain.

The target external 960-GB SSD I want to install to is, at the moment, empty.  But I believe I have it correctly formatted:

Its partition table is **GPT**.
I've put **8 MB** of empty space at the** beginning**, and at the** end**, of the SSD.
The first partition (sdc1) is the **fat32 ESP, sized at 550 MB**. (This is the size recommended by rEFInd creator Rod Smith.) 
The 2nd, large, partition (sdc2) is ext4, sized at 893 GB. 
 / (root) and /home will go on this 2nd large partition.

I have the Ubiquity installer for Ubuntu-MATE 20.04.1 on a USB flash drive (made with Startup Disk Creator) working as it should. (Except, of course, for Ubiquity's UEFI bug).

I've only just learned that ***the installer USB drive*** ***must itself* * boot in EFI mode***, not BIOS mode.  Since my only working system is a BIOS 18.04, I am able to boot the Installer in EFI mode only because I installed the rEFInd boot manager on a separate USB flash drive. 

So I boot  from that rEFInd flash drive.  When rEFInd boots, it is guaranteed to be booting in EFI mode.  

Once booted in EFI mode via the USB rEFInd flash drive, I plug in the USB Ubiquity installer, so that*** it's*** booted in EFI mode.  Remember that my internal non-target drives are unplugged, and the install target is the external  SSD described above.

It's here that I get lost, because Ubiquity has no selection for UEFI.  It wants to format partitions as BIOS.  Also, I already have my partitions formatted, but Ubiquity wants to format them, and is clunky about letting me leave the formatting of them alone.  

(Maybe I should  go ahead and format them with the installer the exact same way I've already formatted them. But that shouldn't be necessary, should it?)

Is it possible to unzip the .iso of 20.04 and just copy over all the files and folders onto my sdc2 ext4 partition?  Instead of moving the .iso into the installer and creating/using the installer in the standard way?

If so, I would need to know exactly which files and folders to put in the ESP.  I  would guess the** *boot***,* **EFI***,and ***install* **folders would go in the ESP, but this is just a guess, I don't really know.  What about ***casper***, which contains an*** intird ***archive and the **vmlinuz** executable?

If this idea of copying is just wrong and hare-brained and won't work, how exactly should one proceed in the installer?  Do everything the BIOS way and then fix things afterward?  I wouldn't know which startup and-or GRUB files or folders to put into the ESP.

I do know that the ESP needs to be mounted as **/boot/efi **and sdc2 needs to be mounted as */  *(root) but I'm not sure where I define that from.  I'm not sure the installer allows to mount /boot/efi.  
  
In the install process, in defining the ESP, when I get to the pop-up menu that says ***"Use this partition as",  ***I just don't know how to proceed. Maybe selecting ***"Use as BIOS partition" ***(or whatever is the exact wording there) is the only way to go, with the idea that I'll have to go in afterward and muck around to somehow whip it into shape as a functioning EUFI system.  

> reinstall grub after your install
For me, easier said than done.  In order to do that, I would need to know more specifics about it than I know now.  Like which files exactly.

 What approach is best to take here?

---

### Post by oldfred on 2020-09-29
How you boot install media, is then how it installs.
You should not need to use rEFInd to boot live installer. You just choose the UEFI:flash drive entry in your UEFI boot menu, often f12, but varies by vendor.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The rEFInd boot manager only boots in UEFI mode, but is one of the few that some how can use UEFI's reboot feature to reboot into a BIOS boot. So using rEFInd may not guarantee UEFI boot.

The Ubuntu live installer ISO is by default configured to boot in either UEFI or BIOS boot mode, but depends on the install tool used. Some only create a BIOS installer or an UEFI installer.

It used to be you could just extract the ISO to a FAT32 partition and that would boot in UEFI mode only. But they added a couple of linked files which are not allowed in FAT32, breaking that method.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534)

I would also suggest a smaller / (root) of 30GB or so and rest as /home or data partition(s). My current install is using about 9GB including /home, no snaps, and all data normally in /home in a data partition.

More details on UEFI install in link in my signature.

Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by sudodus on 2020-09-30
You are making things complicated. Try this way:

0. Unplug the internal drive(s).

1. In the computer's UEFI/BIOS system, set it to boot in UEFI mode. If this is not possible, then you have to accept booting in BIOS mode (alias CSM alias legacy boot).

Please notice that Ubuntu works well (without any limitations) both in UEFI mode and BIOS mode, so there is nothing wrong with booting in BIOS mode in a computer, that you cannot boot in UEFI mode. And Ubuntu can boot in both UEFI mode and BIOS mode with a GPT as well as with an MSDOS partition table.

2. Boot into a live Ubuntu session from the USB boot drive. You can check the boot mode with
```

test -d /sys/firmware/efi && echo efi || echo bios

```

3. Start the installer and let it use the whole drive (the external SSD) where you want to install Ubuntu. Then it will automatically create necessary (and suitable) partitions for you. When you select this option it will overwrite whatever is on the drive, and it will warn you about that: 'Erase disk and install Ubuntu'. See the attached screenshot.

Please notice that frequent backup is more important if you encrypt the drive because it is very difficult to recover or repair a disk with a damaged file system. And there is no back door, so you must remember that passphrase. In other words, encrypt only if you need it, and then set up a good backup routine.

---

### Post by watchpocket on 2020-09-30
I've had partial limited success with my install. 

It's true I don't need to first boot rEFInd to boot the installer in EFI mode. My installer
wasn't booting in EFI mode because in the F10 boot menu, I had been selecting "Generic Flash
Drive" instead of "EFI Shell." Selecting the latter booted the installer in EFI mode by itself,
without having to boot to rEFInd first.
 
The other reason I had trouble earlier was that in Ubiquity, I had chosen to not format partitions (I
figured that because I'd already formatted them, I didn't need to now). That made it so
that, in the formatting pop-up menu, there was no entry to select to use the ESP as the ESP.
So I chose 'format' and was able to  select the entry for the ESP partition.
 
So, I was finally able to run the installer in EFI mode and the installation got 95% of the way 
through, when the installer crashed. The crash was due to a bug described [here]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1871268").
 
Reading through all the responses, the fix for the crash was to run the installer as a "normal" installation
with the *third-party-install* and *driver-update* checkboxes unchecked.  So I did that and the 
installation went all the way through and finished properly.

However, the drive doesn't boot. 

I'm hoping some of the below may provide clues. (The ***/sys*** dir below is empty.)
(I plan later to make a smaller /home partition.)

```
[rj@rjbox:~]  [v5.4.2]  zsh  2012  --> lf /media/rj
total 12
4 drwxrwx---+  3 root root 4096 Sep 30 19:19 ./
4 drwxr-xr-x   3 root root 4096 Apr  5 21:05 ../
4 drwxr-xr-x  20 root root 4096 Sep 30 18:13 8961ed2b-21e9-4ba0-a497-34256815e869/
[rj@rjbox:~]  [v5.4.2]  zsh  2012  -->
[rj@rjbox:~]  [v5.4.2]  zsh  2013  --> lf /media/rj/8961ed2b-21e9-4ba0-a497-34256815e869
total 2097256
      4 drwxr-xr-x   20 root root       4096 Sep 30 18:13 ./
      4 drwxrwx---+   3 root root       4096 Sep 30 19:19 ../
      0 lrwxrwxrwx    1 root root          7 Sep 30 18:09 bin -> usr/bin/
      4 drwxr-xr-x    4 root root       4096 Sep 30 18:20 boot/
      4 drwxr-xr-x    2 root root       4096 Sep 30 18:13 cdrom/
      4 drwxr-xr-x    5 root root       4096 Jul 31 12:33 dev/
     12 drwxr-xr-x  140 root root      12288 Sep 30 18:19 etc/
      4 drwxr-xr-x    3 root root       4096 Sep 30 18:13 home/
      0 lrwxrwxrwx    1 root root          7 Sep 30 18:09 lib -> usr/lib/
      0 lrwxrwxrwx    1 root root          9 Sep 30 18:09 lib32 -> usr/lib32/
      0 lrwxrwxrwx    1 root root          9 Sep 30 18:09 lib64 -> usr/lib64/
      0 lrwxrwxrwx    1 root root         10 Sep 30 18:09 libx32 -> usr/libx32/
     16 drwx------    2 root root      16384 Sep 30 18:07 lost+found/
      4 drwxr-xr-x    2 root root       4096 Jul 31 12:28 media/
      4 drwxr-xr-x    2 root root       4096 Jul 31 12:28 mnt/
      4 drwxr-xr-x    2 root root       4096 Jul 31 12:28 opt/
      4 drwxr-xr-x    2 root root       4096 Apr 15 07:09 proc/
      4 drwx------    3 root root       4096 Sep 30 18:15 root/
      4 drwxr-xr-x   14 root root       4096 Sep 30 18:13 run/
      0 lrwxrwxrwx    1 root root          8 Sep 30 18:09 sbin -> usr/sbin/
      4 drwxr-xr-x    2 root root       4096 Jul 10 09:59 snap/
      4 drwxr-xr-x    2 root root       4096 Jul 31 12:28 srv/
2097156 -rw-------    1 root root 2147483648 Sep 30 18:08 swapfile
      4 drwxr-xr-x    2 root root       4096 Apr 15 07:09 sys/
      4 drwxrwxrwt    2 root root       4096 Sep 30 18:20 tmp/
      4 drwxr-xr-x   14 root root       4096 Jul 31 12:30 usr/
      4 drwxr-xr-x   14 root root       4096 Jul 31 12:37 var/
[rj@rjbox:~]  [v5.4.2]  zsh  2014  -->
```

```
[rj@rjbox:~]  [v5.4.2]  zsh  2025  --> lf /media/rj/8961ed2b-21e9-4ba0-a497-34256815e869/boot  
total 189780
    4 drwxr-xr-x  4 root root     4096 Sep 30 18:20 ./
    4 drwxr-xr-x 20 root root     4096 Sep 30 18:13 ../
 4628 -rw-------  1 root root  4738430 Jul  9 19:50 System.map-5.4.0-42-generic
 4632 -rw-------  1 root root  4743112 Sep 10 06:12 System.map-5.4.0-48-generic
  236 -rw-r--r--  1 root root   237773 Jul  9 19:50 config-5.4.0-42-generic
  236 -rw-r--r--  1 root root   237769 Sep 10 06:12 config-5.4.0-48-generic
    4 drwxr-xr-x  2 root root     4096 Sep 30 18:08 efi/
    4 drwxr-xr-x  4 root root     4096 Sep 30 18:20 grub/
    0 lrwxrwxrwx  1 root root       27 Sep 30 18:19 initrd.img -> initrd.img-5.4.0-48-generic
78332 -rw-r--r--  1 root root 80209089 Sep 30 18:18 initrd.img-5.4.0-42-generic
78352 -rw-r--r--  1 root root 80229765 Sep 30 18:20 initrd.img-5.4.0-48-generic
    0 lrwxrwxrwx  1 root root       27 Sep 30 18:09 initrd.img.old -> initrd.img-5.4.0-42-generic
  180 -rw-r--r--  1 root root   182704 Feb 13  2020 memtest86+.bin
  184 -rw-r--r--  1 root root   184380 Feb 13  2020 memtest86+.elf
  184 -rw-r--r--  1 root root   184884 Feb 13  2020 memtest86+_multiboot.bin
    0 lrwxrwxrwx  1 root root       24 Sep 30 18:19 vmlinuz -> vmlinuz-5.4.0-48-generic
11392 -rw-r--r--  1 root root 11662080 Jul 31 12:46 vmlinuz-5.4.0-42-generic
11408 -rw-------  1 root root 11678464 Sep 10 06:36 vmlinuz-5.4.0-48-generic
    0 lrwxrwxrwx  1 root root       24 Sep 30 18:19 vmlinuz.old -> vmlinuz-5.4.0-42-generic
[rj@rjbox:~]  [v5.4.2]  zsh  2026  --> 
```

```
[rj@rjbox:~]  [v5.4.2]  zsh  2031  --> lf /media/rj/8961ed2b-21e9-4ba0-a497-34256815e869/boot/efi 
total 8
4 drwxr-xr-x 2 root root 4096 Sep 30 18:08 ./
4 drwxr-xr-x 4 root root 4096 Sep 30 18:20 ../
[rj@rjbox:~]  [v5.4.2]  zsh  2032  --> lf /media/rj/8961ed2b-21e9-4ba0-a497-34256815e869/boot/grub 
total 2384
   4 drwxr-xr-x 4 root root    4096 Sep 30 18:20 ./
   4 drwxr-xr-x 4 root root    4096 Sep 30 18:20 ../
   4 drwxr-xr-x 2 root root    4096 Sep 30 18:16 fonts/
   4 -rw-r--r-- 1 root root     712 Jul 31 12:33 gfxblacklist.txt
  12 -r--r--r-- 1 root root    9171 Sep 30 18:20 grub.cfg
   4 -rw-r--r-- 1 root root    1024 Sep 30 18:16 grubenv
2340 -rw-r--r-- 1 root root 2395475 Sep 30 18:16 unicode.pf2
  12 drwxr-xr-x 2 root root   12288 Sep 30 18:16 x86_64-efi/
```

  ```
  1 # /etc/fstab: static file system information.                                                                                                                                                          
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  8 # / was on /dev/sdb2 during installation
  9 UUID=8961ed2b-21e9-4ba0-a497-34256815e869 /               ext4    errors=remount-ro 0       1
 10 # /boot/efi was on /dev/sdb1 during installation
 11 UUID=6DE5-0FF8  /boot/efi       vfat    umask=0077      0       1
 12 /swapfile                                 none            swap    sw              0       0
```


Here's the drive in GParted:

[ATTACH=CONFIG]287079[/ATTACH]

On a different target SSD, I used the erase-disk install method suggested by sudodus (but I didn't encrypt and I didn't use LVM). I unchecked the driver-update box but did check for software updates (I checked both in the install for the SSD discussed above). The installer ran ok, but again, I can't boot to this drive either.  Both drives were installed to while internal non-target drives were unplugged.

---

### Post by oldfred on 2020-09-30
External drives only boot from /EFI/Boot/bootx64.efi.
That may show as UEFI:your drive or the same as you used to boot live installer, EFI Shell.

What brand/model system?
Do not normally see shell as boot option, but some systems have it.
Most just have two entries for live installer if configured for both BIOS & UEFI or only one UEFI:flash if just a flash drive with UEFI only. "flash" is name or label of flash drive you have installer on.

---

### Post by watchpocket on 2020-10-01
> **oldfred said:**
> External drives only boot from /EFI/Boot/bootx64.efi.
In light of this knowledge I've just created /EFI/Boot/ folders in my external drive. (permissions -r--r--r-- on both).  Then I copied into that /EFI/Boot/ folder these 3 files from my live-installer flash drive's /EFI/BOOT/ folder:

bootx64.efi
grubx64.efi
mmx64.efi

I don't know if *grubx64* and *mmx64.efi  *actually belong there or not, but I copied them anyway since they were in the installer's /EFI/BOOT folder.  After this, I still couldn't boot from the external drive I installed 20.04 on.  

(I did a fresh install on that drive earlier today -- the thing I did differently than yesterday's installs was, I selected to have the boot files put in the ESP partition (sdb1) instead of just on sdb.  ISTR that it's usually recommended NOT to put them on a specific partition, but thought I try that anyway.)

Next step is to bring Boot-Repair in.  I still have a /sys folder that's empty, which is no doubt one part of my problem of  not being able to boot.  I just don't get why /EFI/Boot and its files -- and the /sys folder's dirs & files -- weren't created automatically as part of the UEFI install.

Also, shouldn't /EFI/Boot/bootx64.efi go in the ESP partition? 

> That may show as UEFI:your drive or the same as you used to boot live installer, EFI Shell.

Well, since I couldn't boot to it, nothing showed as a selection for the external drive. 

When I unplug my internal working drives, and I press the F10 key as I boot with the USB live-installer flash drive plugged in, the menu I get shows the following:

"ubuntu"  (which if I select does nothing but an infinite-loop restart);
"INTERNAL EFI SHELL: USB Device Hard Drive" (this is the full name of the "EFI Shell" I referred to above. If I select it, the installer boots in *UEFI mode*.)
"Generic Flash Drive" (if I select this, the installer boots in *BIOS mode*.)

> What brand/model system?

Intel. I got the box from System 76, which pre-installs Ubuntu (though that was several versions ago):

[I]Machine:   Type: Desktop System: System76 product: Wild Dog Performance v: wilp6 serial: <filter> 
           Mobo: Intel model: DP45SG v: AAE27733-405 serial: <filter> BIOS: Intel v: SGP4510H.86A.0108.2009.0114.2036 
           date: 01/14/2009[/I] 

Despite the 2009 date, this box's BIOS menu does have a setting (which is activated) to boot UEFI instead of BIOS.

> Most just have two entries for live installer if configured for both BIOS & UEFI

That's basically what I have, as mentioned above.  Now to apply Boot-Repair to my external 20.04.

---

### Post by oldfred on 2020-10-01
Have you checked that you have latest UEFI available for that system?

Not sure you can just copy the boot files from a live installer to boot a full install. Grub/shim are smaller versions just to boot live installer. After install the full versions with added support are installed. And a /EFI/ubuntu/grub.cfg which is only 3 lines is created to configfile into full grub.cfg in your actual install.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You may need advanced mode to choose install & then choose drive to install into.
If UEFI system, be sure to boot live installer in UEFI mode, so repairs or reinstall of grub is in UEFI mode.

---

### Post by watchpocket on 2020-10-01
Hold on, I'll do this from the installer.

---

### Post by watchpocket on 2020-10-01
This was run from the installer: [https://paste.ubuntu.com/p/p8hDhtQytR/](https://paste.ubuntu.com/p/p8hDhtQytR/)

---

### Post by oldfred on 2020-10-01
While you have booted in UEFI mode to run Boot-Repair and still have an old ubuntu entry in UEFI, your install is BIOS.
And you are using the old MBR(msdos) partitioning.
If you set system to boot in BIOS mode, does it not boot?

I do prefer gpt whether BIOS or UEFI. But you have to have extra supporting partitions.
If BIOS, you need bios_grub partition 1MB unformatted for BIOS boot
If UEFI, you need a FAT32 partition with boot,esp flags for UEFI boot.
When I still had BIOS only system, but planned on newer UEFI system, I put both as first two partitions on all new or reformatted drives, including larger flash drives. Now with UEFI, I only add the ESP.

---

### Post by watchpocket on 2020-10-01
Here is an info report with my two internal drives unplugged. 

(Those internal drives are a BIOS 18.04 and a non-OS, non-booting SSD just for data storage.  Those internal drives are what you saw in the boot-repair report above.)

This report is just of the UEFI live installer (sda) and the external SSD I'm trying to install the UEFI/GPT 20.04.1 on (sdb).
[https://paste.ubuntu.com/p/HsJF6rSBK9/](https://paste.ubuntu.com/p/HsJF6rSBK9/)

---

### Post by oldfred on 2020-10-01
UUIDs look ok
The only issue may be that drive is seen as hd1 and USB installer is hd0. But when you reboot the boot drive will be hd0. But UUID should override that.
You could use Escape right after UEFI/BIOS screen to get to grub menu and edit the hd1 entry to hd0.
I often have to do that with my grub2 loopmount ISO boot as drives can change.

---

### Post by watchpocket on 2020-10-02
I'm taking a step back before I continue my UEFI/GPT setup to learn some fundamentals, starting with [this]("https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/"), which is recommended for anyone with limited understanding (as mine is) about how it works. It's also a good read, and very clear.

---

### Post by oldfred on 2020-10-02
That is one of the many links I have to explain UEFI installs and details including many Acronyms and links to details on them.
See link below in my signature.

---

### Post by watchpocket on 2020-10-05
Finally I got a bootable UEFI/GPT Ubuntu-MATE 20.04 installed on a removable drive. 

After installing the iso onto a target SSD  (carefully UN-checking the option to load third-party apps, because the  installer will crash toward the end of its run if you do) I at first followed the steps in [Part E of this tutorial]("https://www.58bits.com/blog/2020/02/28/how-create-truly-portable-ubuntu-installation-external-usb-hdd-or-ssd").  But the first time I did it failed -- I didn't understand what a chroot jail was, nor why I was creating a chroot.  I also followed the completely mistaken instruction in this guide where he says: 

*"First we&#8217;re going to unmount the media volume of the thumb drive (leaving &#8216;Try Now&#8217; Ubuntu running in memory only)."  *Also, his use of non-specific terms like *"in your system," *when he  should have specified that he was talking about the root partition of the target drive, didn't help. I actually tried to unmount the thumb drive "try it" system that I was booted from, and couldn't[I].

[/I]A better guide is [here]("https://www.dionysopoulos.me/making-a-portable-full-installation-of-ubuntu-on-a-usb-hdd.html?akengage_limitstart=120").  The key for me was where he says:* "*[I]installing the bootloader is only possible from inside the Linux  installation we want to boot. However, we need the bootloader to boot  that installation, leading to a Catch-22 issue. The solution is to run  the bootloader installation through a chroot jail."

[/I]At that point I understood that I needed to UNmount the root partition of the  target SSDso that I could re-mount it (and the ESP) in the chroot jail, after setting up a small working environment there.  

You  also have to put the right line in /etc/fstab, load the efivars, and install grub correctly with the --removable tag from inside the chroot /mnt dir -- it's all explained in the guide*. *It's all a bit tricky, you just have to pay attention and think about what you're doing. I didn't want to enter any commands until I completely understood every aspect of what a command (or set of commands) did and why I was using it.

Now, booting to the removable drive works, either with our without my internal BIOS-run Ubuntu-MATE 18.04 SSD connected. I do have to select* "INTERNAL EFI" *from the pre-grub menu, and I do first get an error message saying,* "System Boot Order not found -  initializing defaults," *but it then does go ahead and boot to the removable SSD's 20.04 login page. (This box does not have Secure Boot.)

So I may still have a few kinks to work out, but I finally jumped through the hoops necessary to get a working bootable removable-drive system.  Therefore, I'm now marking this thread solved. Thanks to all for the help and responses.

---

