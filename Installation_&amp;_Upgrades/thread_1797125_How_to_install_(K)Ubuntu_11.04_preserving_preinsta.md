---
title: "How to install (K)Ubuntu 11.04 preserving preinstalled 64bit Windows with UEFI?"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by ahuai on 2011-07-04
My question concerns installing Ubuntu on a machine that uses UEFI.
I know that a lot has already been posted concerning EFI issues ( I have found this to be particularly helpful: [http://ubuntuforums.org/showpost.php?p=10976381&postcount=8](http://ubuntuforums.org/showpost.php?p=10976381&postcount=8)); however  I am completely swamped. Since I believe that my problem is (or may become) a common one I am begging for help in this new thread:

I just purchased a new Acer Aspire X 3960 desktop PC. When I entered the BIOS to change boot priorities in order to install my Kubuntu I found that it boots from an EFI partition. And hence entered what feels like a world of mental pain.

What I would like to do:
Install Ubuntu or Kubuntu preserving the preinstalled Windows 7 64bit.

The problem:
Can it be done? Information I have so far gathered suggests that for dual boot with EFI, Ubuntu should be installed first because it will erase information on the EFI partition previously inscribed by Windows, which would cause Windows boot to fail. All I have, however, are rescue-Dvds to restore Windows and all configurations back to factory settings. Which is what I have now. Which doesn´t solve the problem. I do not have any other 64bit-version of Windows and I also read that known solutions do not work well with the 32bit version (which I do have. Somewhere.). So I would like to preserve the pre-installed version, if in any way possible. (I know that reducing disc-space of a Windows installation may also ruin it. But that seems like a different issue. This is about EFI)

What I would like to know:
First off, I read the word 'firmware' a scary amount of times. Do I run the risk of seriously messing up my PC and end up in state where I won't be able to boot any OS?

Can anyone provide me with a howto for dual boot install preserving my Windows? 

How do I deal with installing Ubuntu using EFI AT ALL? Do I just use the installer DVD like always and it will automatically attempt to do whatever it should be doing to make it work? Or is it always necessary to hand-configure it?

Do Kubuntu and Ubuntu differ in any way here, because I normally prefer KDE but in this case will go for what promises more community support.

I have not tried anything yet because right now I cannot afford to be completely without a PC. But I will be happy to post my experiences if someone trustworthy promises I won`t wreck my PC an always be able to boot Ubuntu somehow...

Many thanks in advance!

---

### Post by srs5694 on 2011-07-04
> **ahuai said:**
> My question concerns installing Ubuntu on a machine that uses UEFI.
...
I just purchased a new Acer Aspire X 3960 desktop PC. When I entered the BIOS to change boot priorities in order to install my Kubuntu I found that it boots from an EFI partition. And hence entered what feels like a world of mental pain.

UEFI booting *is* different, and unfortunately, Ubuntu's support for it is still bug-ridden; however, it *can* be done, and once it's set up it has some distinct advantages over BIOS booting. No doubt Ubuntu's UEFI support will improve with future versions.

> What I would like to do:
Install Ubuntu or Kubuntu preserving the preinstalled Windows 7 64bit.

The problem:
Can it be done? Information I have so far gathered suggests that for dual boot with EFI, Ubuntu should be installed first because it will erase information on the EFI partition previously inscribed by Windows, which would cause Windows boot to fail.

This is true; Ubuntu's installer is stupid enough to erase the EFI System Partition (ESP), which is a partition in the UEFI scheme that holds boot loaders and related information. [I use the word "stupid" here very deliberately. I generally try to avoid loaded words like that, but in this case it fits.]

Fortunately, there are solutions to this problem. At least two of them are quite workable:


[list]
[*]**Install in BIOS mode** -- Most UEFI implementations include a BIOS boot mode for support of legacy OSes. It's possible to install Ubuntu in BIOS mode, install a UEFI-capable boot loader (I recommend [ELILO](http://elilo.sourceforge.net) rather than Ubuntu's default of GRUB 2), and then reconfigure the firmware to boot in UEFI mode. It should then be possible to boot Ubuntu in UEFI mode and forget about the BIOS-mode stuff -- unless perhaps you need to boot an emergency disc that doesn't support UEFI mode. If you go this route, you'll have to create a small [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) for the purpose of BIOS-based booting, but you'll be able to delete this after you've switched over to UEFI booting. The BIOS Boot Partition can be smaller than 1 MiB, so you'll not miss the space it consumes.
[*]**Back up the ESP** -- You can boot the Ubuntu install disc in its "try it now" mode (or whatever it's called), back up the ESP to whatever medium is convenient, and then restore the Windows files when you're done installing Ubuntu. This should work fine, with one caveat: Ubuntu will create a FAT16 ESP, but Windows likes to see a FAT32 ESP. Thus, if you ever need to re-install Windows, you may have problems. You can overcome this glitch by doing two backups and two restores: Back up the ESP as it is now, back it up again (to another file) after Ubuntu installs, create a new FAT32 filesystem after Ubuntu installs, restore both backups, and then edit /etc/fstab to refer to the ESP by device number or update its "UUID" number (since it will have changed).
[/list]


> All I have, however, are rescue-Dvds to restore Windows and all configurations back to factory settings.

You may want to check out [this site,](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) which provides "stock" Windows 7 DVD images, supposedly sanctioned by Microsoft for people like you who want to do standard installs and who have valid licenses but only "recovery" DVDs that load bloatware or trash other partitions.

> (I know that reducing disc-space of a Windows installation may also ruin it. But that seems like a different issue. This is about EFI)

This is one of the little advantages of UEFI: Windows is much less fussy about its boot partition when it's installed in UEFI mode. You can resize and move that partition with GParted with no ill effects -- or at least, I was able to do so two or three times in some tests I performed. One of these involved moving the partition in such a way that the new location shared *no* sectors with the old location, so I know I didn't just "luck out" with key files not moving.

> What I would like to know:
First off, I read the word 'firmware' a scary amount of times. Do I run the risk of seriously messing up my PC and end up in state where I won't be able to boot any OS?

No -- or at least, no more so than when you muck about with OS installations on any other computer. I don't know the context in which you're seeing the word "firmware," but an OS installation on UEFI won't modify the firmware in any serious way. One thing it might do, however, is to adjust the firmware's registry of available boot loaders. That registry can be easily cleared and rewritten, though, so in a worst-case scenario, you'll just have to do that to get the computer to recognize your boot loaders again.

> Can anyone provide me with a howto for dual boot install preserving my Windows? 

It's not exactly that, but I've got a [Web page on UEFI DUET,](http://www.rodsbooks.com/bios2uefi/) which is a way to get BIOS-based computers to boot in UEFI mode. Most of that page doesn't apply to you, but the page has comments on installing Windows, installing Linux, and boot loader choices, much of which applies to "real" UEFI systems. (You can ignore all the stuff about copying files to USB flash drives, though; that's just to get around some limitations in DUET that don't exist in UEFI implementations on motherboards.)

> How do I deal with installing Ubuntu using EFI AT ALL? Do I just use the installer DVD like always and it will automatically attempt to do whatever it should be doing to make it work? Or is it always necessary to hand-configure it?

In theory, installation should proceed in UEFI mode pretty much as it does in BIOS mode. In practice, there are some quirks. I document two of those on the Web page I just referenced, and you brought up one of those: Ubuntu's awful habit of wiping out the ESP. The other is that I had problems getting Ubuntu's installer to boot reliably using UEFI DUET; however, I didn't have these problems with a real UEFI-based computer or with VirtualBox's UEFI implementation, so I think that's DUET-specific. Because of these problems, I recommended on my page not even attempting an Ubuntu install under UEFI DUET; but on a "real" UEFI implementation, it's not quite that bad.

If you do proceed with a UEFI-based installation, you've got to be careful to tell it to use the ESP. IIRC, this isn't necessary if you select an automated option (install side-by-side or take over the whole disk), but it is if you use the manual partitioning option. With that option, you've got to flag the ESP as an "EFI boot partition," or some similar not-quite-standard term, or it won't be able to install GRUB. (Actually, deliberately omitting this partition from the list might prevent Ubuntu from trashing the ESP -- but then you'd need to find another way to get a Linux-capable boot loader installed. Presumably you could do this manually from the install disk in the "try it now" mode. If you try this, I recommend still backing up the ESP before you begin, and then using ELILO rather than GRUB 2, since ELILO has given me much less grief than GRUB 2.)

> Do Kubuntu and Ubuntu differ in any way here, because I normally prefer KDE but in this case will go for what promises more community support.

I'm afraid I have no idea about this.

---

### Post by ahuai on 2011-07-05
uuuuukay, thanks alot, the fog is slowly clearing... although it's pretty hazy still ;)

I think this is the solution I would like to try:
> **Back up the ESP** -- You can boot the Ubuntu install disc in its  "try it now" mode (or whatever it's called), back up the ESP to whatever  medium is convenient, and then restore the Windows files when you're  done installing Ubuntu. This should work fine, with one caveat: Ubuntu  will create a FAT16 ESP, but Windows likes to see a FAT32 ESP. Thus, if  you ever need to re-install Windows, you may have problems. You can  overcome this glitch by doing two backups and two restores: Back up the  ESP as it is now, back it up again (to another file) after Ubuntu  installs, create a new FAT32 filesystem after Ubuntu installs, restore  both backups, and then edit /etc/fstab to refer to the ESP by device  number or update its "UUID" number (since it will have changed).So far I have tried to backup the current ESP. Here's what I did (and I am not sure at all that I did it right...):

I started the Kubuntu 11.04 64bit Live-Dvd in tryout-mode. 
I first ran fdik because I really had no clue what the partition table would look like:
```
ubuntu@ubuntu:~$ sudo fdisk -l
Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9233dc6b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        2295    18432000   27  Unbekannt
/dev/sda2   *        2295        2308      102400    7  HPFS/NTFS
/dev/sda3            2308       61955   479110144    7  HPFS/NTFS
/dev/sda4           61955      121602   479115992    7  HPFS/NTFS

```Since you said that Windows wants a FAT32 ESP I expected fdisk to list such a partition, but it didn't. ("Unbekannt" means unknown, sorry I switched language settings to German out of habit, won't happen again!)

I then checked what was mounted to /media:
```

ubuntu@ubuntu:~$ ls -al /media/
insgesamt 20
drwxr-xr-x  6 root   root    140 2011-07-05 22:05 .
drwxr-xr-x 33 root   root    320 2011-07-05 21:35 ..
drwx------  1 ubuntu ubuntu 8192 2011-07-05 12:16 Acer
lrwxrwxrwx  1 root   root      6 2011-07-05 23:31 cdrom -> /cdrom
drwx------  1 ubuntu ubuntu 4096 2011-07-05 12:15 Data
lrwxrwxrwx  1 root   root     45 2011-04-25 23:35 .directory -> /etc/kubuntu-default-settings/directory-media
drwx------  1 ubuntu ubuntu 4096 2011-07-05 21:47 Elements
lrwxrwxrwx  1 root   root     42 2011-04-25 23:35 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwx------  1 ubuntu ubuntu 4096 2010-02-10 17:59 SYSTEM RESERVED

```Elements is my USB drive, Acer contains the Windows. DATA and SYSTEM RESERVED look like this:
```
ubuntu@ubuntu:~$ ls -al /media/SYSTEM\ RESERVED/
insgesamt 384
drwx------ 1 ubuntu ubuntu   4096 2010-02-10 17:59 .
drwxr-xr-x 6 root   root      140 2011-07-05 22:05 ..
drwx------ 1 ubuntu ubuntu   4096 2010-02-10 17:59 Boot
-rw------- 1 ubuntu ubuntu 383562 2009-07-14 01:38 bootmgr
drwx------ 1 ubuntu ubuntu      0 2010-02-10 09:08 System Volume Information

``````

ubuntu@ubuntu:~$ ls -al /media/Data/
insgesamt 4
drwx------ 1 ubuntu ubuntu 4096 2011-07-05 12:15 .
drwxr-xr-x 6 root   root    140 2011-07-05 22:05 ..
drwx------ 1 ubuntu ubuntu    0 2011-07-02 16:34 $RECYCLE.BIN
drwx------ 1 ubuntu ubuntu    0 2010-02-10 09:08 System Volume Information

```So I am guessing, that SYSTEM RESERVED is probably the ESP I want to backup. This I did.
```
sudo cp -vr /media/SYSTEM\ RESERVED/ /media/Elements/ESP_backup
```Now I am admittedly a bit clueless... 
Since all partitions were listed as NTFS I am not sure how to recognize the ESP in the Kubuntu setup partitioning menue. I guess I could just go for the automated side-by-side install.
If I understand you correctly, installation should leave me with a regularly functioning Kubuntu booted via EFI and my Windows temporarily unaccessible. The Windows ESP will then be overwritten with the Kubuntu ESP.

Now, how do I restore bootloader information for Windows? Do I just copy what I just backed up and insert it alongside whatever will have been written during Kubuntu installation?
Is it correct that somehow restoring this information in the ESP will get Windows to work but may cause problems in the future because it wants its ESP on a different file system?
How do I create a FAT32 partition in the running system, what do I need to put on it and how do I edit the fstab?! 
Sorry for being so clueless. The truth is, I have been using (K)ubuntu for years but the wildest thing I ever had to do was fix GRUB from a Live-CD after Windows had overwritten the MBR... neverever had any real problems: A spectacularly good reason to keep using it :p!

I also have to report that the live-Dvd didn't exactly run smoothly. It took forever to load and when I restarted the computer it put out that all linux processes had been terminated (as usual) and then just crashed printing out sth in the line of not being able to find the designated hard drive. (Worked normal after restarting it.) I had previously entered the bios to change boot priorities but accidently exited without saving the changes. The computer was booted from CD nonetheless. I didn't find that very reassuring... Is there anything special I need to do in the BIOS to boot from CD? I figured I'd just set the DVD device as first boot device and the rest didn't really matter and later I'd set it back to UEFI...?

Again thanks alot for your help and I'll really appreciate it if you found the time to help me along some more!

---

### Post by srs5694 on 2011-07-06
> **ahuai said:**
> I started the Kubuntu 11.04 64bit Live-Dvd in tryout-mode. 
I first ran fdik because I really had no clue what the partition table would look like:
```
ubuntu@ubuntu:~$ sudo fdisk -l
Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9233dc6b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        2295    18432000   27  Unbekannt
/dev/sda2   *        2295        2308      102400    7  HPFS/NTFS
/dev/sda3            2308       61955   479110144    7  HPFS/NTFS
/dev/sda4           61955      121602   479115992    7  HPFS/NTFS

```Since you said that Windows wants a FAT32 ESP I expected fdisk to list such a partition, but it didn't. ("Unbekannt" means unknown, sorry I switched language settings to German out of habit, won't happen again!)

Based on your partition table, it appears that you are *not* running in UEFI mode; you're running in BIOS mode. I say this for two reasons:


[list]
[*]Your disk is clearly an MBR disk, not a GPT disk; fdisk can't handle GPT disks. This is relevant because Windows insists on booting from a GPT disk on UEFI-based computers and from MBR disks on BIOS-based computers. (Linux isn't so limited, but the fact that the computer came with Windows installed makes the Windows limitations relevant.)
[*]As you observed, there's no EFI System Partition (ESP); it would show up on an MBR disk as being of type 0xEF (that is, "ef" under the "Id" column). On a GPT disk, an ESP shows up as having the "boot flag" set if you use parted or GParted; or as a partition of type EF00 if you use gdisk.
[/list]


Most (maybe all) of the current crop of UEFI-based PCs provide a BIOS compatibility mode, and it appears that Acer is using that mode for its Windows installation. Thus, you're going to have to reassess how to proceed. I can think of at least three options:


[list=1]
[*]Treat the computer as a BIOS-based computer and install Linux just as you would on such a computer. There's plenty of documentation on how to do this and in the short term you're likely to encounter fewer problems this way. The big stumbling block is that Acer has used all four of your computer's primary partitions, which means you're going to have to delete one of them or find a way to convert at least one from a primary partition to a logical partition. (My [FixParts](http://www.rodsbooks.com/fixparts/) program can convert from primary to logical, but with some significant limitations.) The usual advice for this type of situation is to find the partition that holds the Windows recovery files, use a utility that should be on your computer to burn those files to a set of recovery DVDs, and delete that partition. This will free up a primary partition you can use to create an extended partition that can in turn hold as many logical partitions as you like to hold your Ubuntu installation.
[*]Use a standard Windows installation disc for your version of Windows (such as the ones you can get [here](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)) to install a "stock" version of Windows, then install Ubuntu (or do it the other way around). This will get rid of any extras that the computer manufacturer installed, which could be good or bad, depending on your point of view. An advantage is that this will give you the flexibility of choosing whether to install Windows in BIOS mode or in UEFI mode. Presumably you'd use the same mode for Ubuntu, although it's easier to install Ubuntu in one mode and use it in the other mode.
[*]Follow [these instructions](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI) to convert your existing installation from BIOS mode to UEFI mode and then install Ubuntu in UEFI mode (or in BIOS mode and then switch to UEFI mode). This will preserve whatever extra software Acer installed on your computer and will switch you to GPT partitioning, so the fact that Acer chewed up four primary partitions will be unimportant. The Acer recovery tools might not work, though, so you should definitely get yourself a standard Windows DVD for emergency use.
[/list]


Personally, my preference, were I in your shoes, would be for option #2 with the UEFI boot variant; however, UEFI expertise is still pretty rare, so you're most likely to get help going with option #1 or #2 with the BIOS boot variant.

I'll answer some of your remaining questions with the assumption that you go with one of the UEFI options (and install Windows first, if you go with #2)....

> If I understand you correctly, installation should leave me with a regularly functioning Kubuntu booted via EFI and my Windows temporarily unaccessible. The Windows ESP will then be overwritten with the Kubuntu ESP.

Correct -- at least, assuming KUbuntu is like a stock Ubuntu install in how it handled ESPs.

> Now, how do I restore bootloader information for Windows? Do I just copy what I just backed up and insert it alongside whatever will have been written during Kubuntu installation?

Yes. That's one of the advantages of UEFI: Booting is controlled by ordinary files, not by code hidden away in boot sectors. Restore the files, and you restore the system's ability to boot.

Well, almost. You might also need to adjust some boot options in the firmware to get it to recognize the boot loader files. The details of how to do this vary with the firmware implementation, so I can't offer specific advice on how to do this, but there should be an option somewhere to let you locate boot loaders by file and launch them or add them to a menu.

> Is it correct that somehow restoring this information in the ESP will get Windows to work but may cause problems in the future because it wants its ESP on a different file system?

The Windows 7 installer wants to see a FAT32 ESP, but Ubuntu creates a FAT16 ESP, so if you need to re-install Windows after installing Ubuntu, the Windows installer will flake out -- it'll either tell you it can't install or it'll start the process, create a *second* ESP, and then fail to complete because there are two ESPs and it's become totally confused by that fact. At least, that's what I found in my tests. This limitation does *not*, AFAIK, affect Windows' ability to boot or perform other routine tasks, should your ESP be converted to FAT16 and the Windows files restored to it.

> How do I create a FAT32 partition in the running system, what do I need to put on it and how do I edit the fstab?! 

The text-mode mkdosfs command creates a FAT filesystem. Assuming your ESP is /dev/sda1 (which it might or might not be, depending on how you proceed), you'd do something like this:

```

sudo umount /dev/sda1
sudo mkdosfs -F 32 /dev/sda1

```

The umount command ensures that the ESP isn't currently mounted. The mkdosfs command with the -F 32 option creates the FAT32 filesystem.

Alternatively, you could use GParted to do it: You'd select the ESP and tell GParted to create a FAT32 filesystem on it.

The /etc/fstab entry for an ESP in Ubuntu is likely to look something like this:

```
UUID=5699-8F49  /boot/efi       vfat    defaults        0       1

```

The UUID= value is almost certain to be different on different systems, as this is a filesystem serial number. It will therefore change when you create a new filesystem on the partition. After you do this, you'd need to change that value to reflect whatever it is for your system, which you can determine with blkid:

```

$ **sudo blkid /dev/sda1**
/dev/sda2: LABEL="ESP" UUID="5699-8F49" TYPE="vfat"

```

Alternatively, you could replace "UUID=5699-8F49" (or whatever the real value is) with "/dev/sda1". This might be a bit safer for an ESP, given the way that the Ubuntu installer is "overly generous" with its filesystem creation on the ESP.

What you'd put on the ESP is whatever files all your OSes combined put on their individual ESPs. If you want to try another boot loader, you'd also put its files there. Most or all of these files reside in the EFI subdirectory. (In Ubuntu, the ESP is normally mounted at /boot/efi, so it'd be /boot/efi/EFI in Ubuntu.) The subdirectories are named after the OS or publisher, so you'll probably have /boot/efi/EFI/Microsoft and /boot/efi/EFI/ubuntu. There's also likely to be a /boot/efi/EFI/BOOT subdirectory that holds a default boot loader file. (Microsoft will put a copy of its boot loader there.) If you experiment with other boot loaders, you might name the subdirectories after the boot loaders, like /boot/efi/EFI/refit or /boot/efi/EFI/elilo.

> Sorry for being so clueless.

No problem. UEFI is still new and poorly understood. Perhaps you'll be able to help others in a few weeks or months!

> I also have to report that the live-Dvd didn't exactly run smoothly. It took forever to load and when I restarted the computer it put out that all linux processes had been terminated (as usual) and then just crashed printing out sth in the line of not being able to find the designated hard drive.

You might want to investigate this further, since it could have some bearing on whether you want to proceed with a BIOS or UEFI installation. If your live DVD was booted in UEFI mode, it's conceivable that it's buggy on your system and you might want to avoid it. OTOH, if it was in BIOS mode, you might want to try to get the live DVD booted in UEFI mode in case that might be more reliable. It's also possible it was slow just because it's running from a DVD or that your DVD burn was a bit on the hard-to-read side.

You can tell which mode you were in from a Terminal window:

```
$ **dmesg | grep EFI**
[    0.000000] Command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000048000) (0MB)

```

On an EFI or UEFI system, this output will continue for quite a while reporting EFI memory mappings, then conclude with a couple of lines about the EFI framebuffer device. On a BIOS boot, you'll see nothing as output from this command, or at most a line or two that happen to match because "EFI" appears as a substring of some other word.

There is a [known bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721576) that causes some UEFI systems to crash when rebooting. There's a simple workaround, although it doesn't work for everybody. (Read the bug report for details.) It's conceivable this is what you ran into when you shut down.

> Is there anything special I need to do in the BIOS to boot from CD? I figured I'd just set the DVD device as first boot device and the rest didn't really matter and later I'd set it back to UEFI...?

Unfortunately, I can't offer a lot of help on that score, since the UEFI user interfaces seem to vary a lot, and I'm not sure exactly what options you must set to get yours working in any particular way. If you get totally confused, you could try taking a screen shot with a digital camera and posting it to show the relevant menus.

---

### Post by ahuai on 2011-07-06
Thanks again!

I next followed this suggestion of yours concerning the buggy live-dvd boot:
> You might want to investigate this further, since it could have some  bearing on whether you want to proceed with a BIOS or UEFI installation.  If your live DVD was booted in UEFI mode, it's conceivable that it's  buggy on your system and you might want to avoid it. OTOH, if it was in  BIOS mode, you might want to try to get the live DVD booted in UEFI mode  in case that might be more reliable. It's also possible it was slow  just because it's running from a DVD or that your DVD burn was a bit on  the hard-to-read side.Apparently the BIOS/EFI interaction on my machine is a bit confusing (at least to me based on what I read so far).

When the boot order is set to default values (EFI, hard drive, DVD, other, LAN) the computer boots from the Kubuntu 64bit dvd - and only the 64bit not the 32bit version - if inserted.
Right before it does so, ```
Error: prefix "" not set
``` will be printed on the screen for a couple of seconds, it then takes several minutes to boot, works normal in tryout mode and crashes when trying to reboot after shutting down Kubuntu.

I followed your suggestion to see what mode the dvd was booted in:
```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.10 by Acer Inc.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000077000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000077000-0x0000000000078000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000078000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000054d000) (4MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000054d000-0x0000000001000000) (10MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] EFI: mem07: type=4, attr=0xf, range=[0x0000000001100000-0x000000000148d000) (3MB)
[    0.000000] EFI: mem08: type=3, attr=0xf, range=[    0.000000] EFI: mem167: type=7, attr=0xf, range=[0x0000000100000000-0x00000001bf800000) (3064MB)

**and so on and on for many lines...**


[    0.000000] EFI: mem168: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] EFI: mem169: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    3.076855] fb0: EFI VGA frame buffer device
[    3.850582] EFI Variables Facility v0.08 2004-May-17
[    3.975633] fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver

```So I assume that in some way an EFI boot was attempted and didn't work the way it should have.

I then changed the boot order in the BIOS so the dvd drive would be first boot device. No error messages were shown, it took half the time to boot and the dmesg | grep command did not return anything. So it must have booted in BIOS mode.

I next tried to see how Windows is normally booted by changing the boot order like so: Hard drive, dvd, EFI.
Windows was booted the usual way with one little change:
Normally (using default boot order) when starting up the computer, the first thing I see is an Acer-screen with a prompt to enter setup. This gets me into the BIOS.
Then a black screen will appear with another prompt to enter setup (with a different set of keys) which will start something named Intel (R) Boot Agent GE v1.3.65.
It looks like a BIOS with fewer options and apparently doesn't do anything. When entering the boot options menue here it simply states that the boot order will be set according to BIOS settings. It also prints out some system information (MAC adress, disc space and such). I assumed that this is part of the firmware pertaining to UEFI, but again, it does not offer me anything like manipulating lists of boot loaders or even mention or list anything like that. I have googled it and not found anything useful.
When booting with the hard drive set as my first boot device the prompt to enter this second setup is NOT shown and Windows just boots normally.

So as my fdisk partition list made obvious (at least to you), my Windows installation is not a UEFI installation. BUT apparently something other than regular BIOS mode is preconfigured that causes bootable CDs to load in EFI mode if inserted and prints out that second setup prompt when the boot order is set to default settings.

This is avoided when a higher boot priority is assigned to the hard drive than to the EFI drive (or whatever it is, since a respective drive is nowhere to be found.)

So my guess is:
I should set the boot order accordingly, and install Kubuntu like usual in BIOS mode.
I will first try it like you suggested...
> Treat the computer as a BIOS-based computer and install Linux just as  you would on such a computer. There's plenty of documentation on how to  do this and in the short term you're likely to encounter fewer problems  this way. The big stumbling block is that Acer has used all four of your  computer's primary partitions, which means you're going to have to  delete one of them or find a way to convert at least one from a primary  partition to a logical partition. (My [FixParts]("http://www.rodsbooks.com/fixparts/")  program can convert from primary to logical, but with some significant  limitations.) The usual advice for this type of situation is to find the  partition that holds the Windows recovery files, use a utility that  should be on your computer to burn those files to a set of recovery  DVDs, and delete that partition. This will free up a primary partition  you can use to create an extended partition that can in turn hold as  many logical partitions as you like to hold your Ubuntu installation....and post my experiences. If that fails I'll install a "stock windows" like you suggested.

> Correct -- at least, assuming KUbuntu is like a stock Ubuntu install in how it handled ESPs. I have researched it a little and found nothing on the contrary. At least the version of GRUB is supposed to be identical.

I am however still insecure that some firmware settings that I cannot control may cause me severe trouble. I have so far not found anything that will let me control EFI settings which obviously have been made for my hardware somewhere...
The BIOS is pretty weird too, when changing the boot order +/- keys are to be used and pressing them will move the highlighted items one spot, then two spots, first up then down. I don't know what the heck that is supposed to be good for, I ended up hitting one of the keys in the same spot again and again until the result was close enough to what I wanted.

---

### Post by srs5694 on 2011-07-06
> **ahuai said:**
> I followed your suggestion to see what mode the dvd was booted in:
```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.10 by Acer Inc.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
```

So I assume that in some way an EFI boot was attempted and didn't work the way it should have.

It sounds to me like it worked, but may have been slow. It might have been slow because of an EFI/OS issue or because of an EFI/DVD issue. If the latter, it might perform better once installed in EFI mode, but it'll probably be quicker and safer to do a BIOS install rather than risk sluggish performance because of an EFI problem. The crash on shutdown could be the known bug I referred to earlier.

> Then a black screen will appear with another prompt to enter setup (with a different set of keys) which will start something named Intel (R) Boot Agent GE v1.3.65.
It looks like a BIOS with fewer options and apparently doesn't do anything. 

I'm not entirely sure what this is, but based on some Googling, I suspect it has something to do with network booting.

> BUT apparently something other than regular BIOS mode is preconfigured that causes bootable CDs to load in EFI mode if inserted and prints out that second setup prompt when the boot order is set to default settings.

This sounds like a correct inference. Those boot options are sometimes written to make things as clear as mud! ;)

> So my guess is:
I should set the boot order accordingly, and install Kubuntu like usual in BIOS mode.

This sounds sensible to me.

> I am however still insecure that some firmware settings that I cannot control may cause me severe trouble. I have so far not found anything that will let me control EFI settings which obviously have been made for my hardware somewhere...

On the contrary -- you *have* found the relevant settings; they just aren't labelled very clearly!

---

