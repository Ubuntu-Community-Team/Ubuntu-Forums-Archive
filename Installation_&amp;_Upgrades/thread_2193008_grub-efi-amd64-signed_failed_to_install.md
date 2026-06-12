---
title: "grub-efi-amd64-signed failed to install"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by scratch65535 on 2013-12-10
I can't seem to get grub to install.  I've tried several times, even supplying a /boot partition by hand.  Everything else appears to go well, installing from dvd, but then I get the dreaded message.

The system is an ASUS 990FX motherboard, Phenom II x6, 32GB, installing to the front 60GB of a WD RE4 1TB drive.

---

### Post by ubfan1 on 2013-12-10
Can you mount (while running live media) the EFI partition and take a look at /EFI/ubuntu ?  Sometimes this directory gets corrupted and the grub install will fail until it is fixed (bug #1090829).

---

### Post by scratch65535 on 2013-12-11
What I'm seeing is that the install gets to the point where it tries to install grub2, and then fails because it can't install to '/target/'.  And that crashes the installer completely, which shouldn't happen.  Why is it trying to install to /target/ instead of /boot - do you know?

Is there a non-interactive boot loader I can stick in?  I don't need grub - freebsd has a nice, albeit primitive, boot manager that will work fine if I can just get a vanilla loader that will boot ubuntu.  I can probably even use syscmdr 7, if I can just get a loader for ubuntu.

I haven't tried your suggestion yet, but since the installer crashed again with the same error, I'll take a look for /efi/ubuntu now.

It's interesting that it apparently thinks the problem, or some problem, is in the ubiquity installer, which it seems to say is not an ubuntu package and should be removed.

---

### Post by scratch65535 on 2013-12-11
> **ubfan1 said:**
> Can you mount (while running live media) the EFI partition and take a look at /EFI/ubuntu ?  Sometimes this directory gets corrupted and the grub install will fail until it is fixed (bug #1090829).

There is no such file/directory, if I understand what you're asking.  There's /cdrom/efi/boot/bootx64.efi and /cdrom/efi/boot/grubx64.efi, and there's /cdrom/ubuntu that appears to be a link to /cdrom (I might be wrong - I don't know the graphic syntax, but it looks as though it just points back up to /cdrom)

---

### Post by fantab on 2013-12-11
'Try Ubuntu" from DVD/USB, open Terminal and post the output of the following:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by scratch65535 on 2013-12-11
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA WDC WD1003FBYX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  256MB   255MB   primary  ext4
 3      256MB   4352MB  4096MB  primary  linux-swap(v1)
 4      4352MB  64.4GB  60.1GB  primary  ext4
 2      64.4GB  1000GB  936GB   primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 

xubuntu@xubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b1eace2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2       125837145  1953520064   913841460    7  HPFS/NTFS/exFAT
/dev/sda3          499712     8499199     3999744   82  Linux swap / Solaris
/dev/sda4         8499200   125835263    58668032   83  Linux

Partition table entries are not in disk order
xubuntu@xubuntu:~$

------------------------------------------------

The disc was formated by XP, so it's an MBR disk.  The motherboard does have a UEFI bios, but it has no choices about whether to boot EFI or legacy.  So I'm wondering now whether I'm not getting anywhere because the installer is getting confused by the nature of the disc.  Should I be looking to install a non-efi version of grub?  If so, how?

---

### Post by fantab on 2013-12-11
```
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  256MB   255MB   primary  ext4               [COLOR=#b22222]??[/COLOR]
 3      256MB   4352MB  4096MB  primary  linux-swap(v1)
 4      4352MB  64.4GB  60.1GB  primary  ext4
 2      64.4GB  1000GB  936GB   primary  ntfs
```

If the first partition is your /boot partition then it needs to have a '**boot**' flag. You can use gparted to put a boot flag there, [Rt. click on the partition in gparted, 'manage flags', select 'boot'].

You have 'msdos' partition table, which means you are not booting in EFI. Because Windows and Ubuntu CANNOT boot in EFI from 'msdos' disk.

---

### Post by scratch65535 on 2013-12-11
So what about the version of grub?  It appears to be trying (and failing) to install the efi version - is that significant?

And am I going to get the disk in trouble using gparted?

---

### Post by fantab on 2013-12-11
Just putting a 'boot' flag with gparted  is NOT going to land you in trouble.
Yes, Check in your BIOS and check what boot mode it is set to, UEFI, AUTO, or Legacy/CSM... change it to 'Legacy/CSM'... even this won't land you in trouble.
When you boot your Ubuntu DVD/USB what color screen welcomes you, Black or 'purplish'?

---

### Post by scratch65535 on 2013-12-11
There doesn't appear to be a boot mode setting in the bios that I can find, on-screen or in the printed docs.  The only boot choices I have are things like splash, int19, etc.

After setting the boot bit, I tried installing the boot by hand using grub-install.  I installed it to the main partition since I can't seem to find a requirement saying it's to have its own partition.  I reckoned it would clear the bit in the boot partition and set it in the main one.  But not so.  When I rebooted, it booted as far as grub, but didn't get any further even when I told it "boot".  When I loaded from the dvd and looked at the part table, the boot bit was still where I left it and there was no bit in the main part.  So what I reckon I'll try now, unless you have some other idea, is to grub-install to that boot partition and see whether that helps.

(If I understand what you mean, it's greenish rather than black or purplish)

---

### Post by oldfred on 2013-12-11
This shows both a BIOS boot screen (purple) and an UEFI boot screen black with standard grub menu.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If UEFI/BIOS is the newer UEFI, the Ubuntu installer will boot in either UEFI or BIOS from flash drive. UEFI menus are not always very clear on what they call the choices.

Boot flag in BIOS/MBR is only used by Windows to know which partition is the bootable Windows. Grub does not use it, but some BIOS need to see a boot flag to let you boot at all, so we still suggest one on a primary partition.
In UEFI gparted uses the boot flag to set which partition is the efi partition. It really is not the same thing as a BIOS boot flag.
With BIOS you must have MBR(msdos) partitioned drives for Windows.
With UEFI you must have gpt partitioned drives for both Windows & Ubuntu.
But Ubuntu will also boot from a gpt partitioned drive with BIOS boot mode or UEFI boot mode. 
And it seems the installer may try to install in UEFI mode on a previously formatted MBR drive, which will not work.

---

### Post by scratch65535 on 2013-12-11
> **oldfred said:**
> 
And it seems the installer may try to install in UEFI mode on a previously formatted MBR drive, which will not work.

And it seems that that's exactly what it's trying to do (the boot screen is black, with the 3 menu items).  How does one dissuade it?

---

### Post by oldfred on 2013-12-11
You have to choose in UEFI menu. 
Usually one does say UEFI and the other may say Legacy/BIOS/CSM or just not say UEFI.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If secure boot is on, only UEFI boot choices that are secure boot will be offered to boot.
Some also have separate settings for Secure boot (UEFI only), UEFI on/off, CSM on/off. 
Or They offer both UEFI or CSM when secure boot is off.

And a few say they had to add a password to UEFI to turn secure boot off. Not sure if required or user just thought that worked. If password is added, vital to keep that somewhere as you may not use it often and if it is forgotten you may then have really big issues (or a brick).

---

### Post by scratch65535 on 2013-12-11
What UEFI menu?

---

### Post by oldfred on 2013-12-11
Some examples others have posted.

---

### Post by scratch65535 on 2013-12-11
I don't have anything like those.  This is what I have (see my next post)

---

### Post by oldfred on 2013-12-11
If small like 640x480 or a bit larger, you use advanced editor and click on the paperclip icon in the edit panel at the top. That will open a upload screen to attach your screenshots. 

       Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by scratch65535 on 2013-12-11
[QUOTE=oldfred;12871311]If small like 640x480 or a bit larger, you use advanced editor and click on the paperclip icon in the edit panel at the top. That will open a upload screen to attach your screenshots.

The forum apparently didn't like them when they were .bmps, so now they're .jpegs

[ATTACH=CONFIG]248529[/ATTACH][ATTACH=CONFIG]248527[/ATTACH][ATTACH=CONFIG]248526[/ATTACH]

None of the menus give me a choice of whether to have EFI, I just get what I get.

---

### Post by oldfred on 2013-12-11
Your option ROM is the extra ROM for BIOS booting?
Usually called this:
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by scratch65535 on 2013-12-11
No, I got excited and thought the "option rom" option was it, too.  But it's not, it's an option to have peripherals report their boot experience if they can.

---

### Post by oldfred on 2013-12-11
When you look at boot options, does it open up and show a lot of choices?
Someone posted these which are similar but have more choices.

---

### Post by oldfred on 2013-12-11
See also this:
[http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)

A user in this thread:
Turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
[http://ubuntuforums.org/showthread.php?t=2193044](http://ubuntuforums.org/showthread.php?t=2193044)

---

### Post by scratch65535 on 2013-12-12
> **oldfred said:**
> When you look at boot options, does it open up and show a lot of choices?
Someone posted these which are similar but have more choices.

No, I posted the image from mine.  It doesn't have those choices.  Maybe whoever posted those has v3 of the board, or they got those with a bios update.  Mine definitely does not have them.

I'll try patching it with boot-repair, but if that doesn't work I'll  just give up.

---

### Post by scratch65535 on 2013-12-12
That is a _really_ broken install disk.

Just on the off chance -it's older than the ASUS one- I checked the bios on my "client" machine.  It does have settings for legacy, so I set them, booted the cd, and it couldn't see my mouse or keyboard.  XP can see them, the startup panel for the disk can see the keyboard at least, but 12.04.3 can't see either one when in legacy mode on this machine.

Which is the last version of xubuntu NOT to do efi at all, straight old-style?

---

### Post by oldfred on 2013-12-12
Both Ubuntu & Windows worked with my USB mouse. But grub is before drivers are loaded and uses the BIOS defaults. 
My motherboard (not Asus) has enable USB ports for mouse & keyboard setting. Does yours?

---

### Post by scratch65535 on 2013-12-12
> **oldfred said:**
> Both Ubuntu & Windows worked with my USB mouse. But grub is before drivers are loaded and uses the BIOS defaults. 
My motherboard (not Asus) has enable USB ports for mouse & keyboard setting. Does yours?

This board and bios (GB 970) auto-recognises USB mice and keyboards, and that's what I use.  I also use a VGA/USB KVM, but had to take that out of the circuit to even get the what-do-you-want-to-do page to see the keyboard.  

Long story short, I haven't used PS2 since they became hard to find.  Straight USB at all times.  I don't even think I have a working ps2 mouse any more.

---

### Post by Ren_Crain on 2014-02-01
> **fantab said:**
> ```
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  256MB   255MB   primary  ext4               [COLOR=#b22222]??[/COLOR]
 3      256MB   4352MB  4096MB  primary  linux-swap(v1)
 4      4352MB  64.4GB  60.1GB  primary  ext4
 2      64.4GB  1000GB  936GB   primary  ntfs
```

If the first partition is your /boot partition then it needs to have a '**boot**' flag. You can use gparted to put a boot flag there, [Rt. click on the partition in gparted, 'manage flags', select 'boot'].

You have 'msdos' partition table, which means you are not booting in EFI. Because Windows and Ubuntu CANNOT boot in EFI from 'msdos' disk.

How do I do this is I am using EFI? I'm having all of the same problems. 

Would just installing another grub2 package help?

---

### Post by oldfred on 2014-02-01
@Ren_Crain
If using UEFI, please start a new thread and post this. 
Also what model computer & video card/chip.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by globster on 2014-02-06
I had the same problem with ASUS M5A97 mainboard. After i made the internet connection on installation everything worked just fine.

---

### Post by pete20 on 2014-03-26
> **globster said:**
> I had the same problem with ASUS M5A97 mainboard. After i made the internet connection on installation everything worked just fine.

This solved the problem, too!!
Booting from flash drive through UEFI... Without internet connection the grub-efi-amd64-signed failure showed up during xubuntu 13.10 installation!

Wonderful,
Pete

---

