---
title: "USB flashdrive 14.04 install on Lenovo T440p (UEFI) running Win 7"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by Jacdeb6009 on 2015-03-14
I have a new Lenovo Thinkpad T440p with Windows 7 installed. This is a company machine and I cannot install Linux on it ("corporate IT does not support this") and I can (for the same reason) not set up a dual-boot system on the machine's SSD.

With my previous machine (an older Dell Vostro) I simply created an Ubuntu install on a USB flashdrive (15 Gbyte as "/" and 15 Gbyte as "/home"). This allowed me to do the things I needed using Linux.

With the new machine I wished to do the same. The UEFI on the T440p was set to allow UEFI and Legacy boot with UEFI as the first priority, further it was also set to allow CSM support and Secure Boot was disabled.

On startup the machines splash screen displays a message stating "Press enter to interrupt normal boot", ignoring this message boots the machine directly to Windows 7. Presssing enter brings up a menu which allows you to enter the EUFI (BIOS) setup or select a boot device (SSD, DVD or Network).

I selected DVD to boot from an Ubuntu 14.10 (64-bit) disk. This worked well and I could confirm that things worked as I am used to. I then inserted the 32Gb flashdrive I had previously used and proceeded to install Ubuntu in the same way as I always do. The intended set up was to have the boot loader installed on the flash drive so that when it is not connected to the machine, it is a Windows machine, but with the flash drive installed it would be a dual boot (although I would use this only to run Linux).

All went well and the install completed normally. Upon re-booting the machine with the flashdrive connected I got the GRUB menu I expected, selected Ubuntu which booted without problems. I then removed the flash drive and tried booting Windows. This did not work. The screen displays a note saying "Booting in insecure mode" and then displays a GRUB screen (GNU GRUB version 2.02~beta2-15) and a "grub>" prompt.

Going into the UEFI (BIOS), and looking at the Boot priority order, showed the following:

1. ubuntu
2. Windows Boot Manager
3. USB CB
4. USB FDD
5. ATAPI CD HL-DT-ST DVDRAM GU90N (dvd drive)
6. ATA HDD0 SAMSUNG M27TD256HAFV-000L9 (256 Gbyte SSD)
7. ATA HDD1:
8. ATA HDD2:
9. USB HDD
10. PCI LAN (two options IPV4 and IPV6)

With Ubuntu selected as first priority, the machine will boot into Ubuntu off the flash without a problem. Removing the drive and trying to boot Windows results in the appearance of the GRUB prompt. Changing the Boot Order and selecting the Windows Boot Manager as the first priority means that the machine boots Windows whether the flash drive is connect or not.

The two screenshots show the partition setup for the flash drive and the SSD.

From these it appears that the boot loader for Linux (GRUB) is installed on the SSD and not on the flash drive (which is where I thought I had set it to be installed and where on my old machine it used to be installed. The fstab (found on the flashdrive at /etc/fstab and shown below) shows /boot/efi created on the SSD.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=fe31225f-df58-4373-add3-902ddb58b4bb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=F0E5-06EA  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdb5 during installation
UUID=2939ec3b-322e-4b57-a014-4a7b1ac1f3d9 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=e11653ba-734d-455c-9f3e-2237a552d717 none            swap    sw              0       0

```


 What I wish to achieve is the following.

  
1. A machine that will boot Windows directly from the SSD when the flash drive is not connected.
2. A machine that will boot to the GRUB menu the flash drive is connected.

 
This is how it worked on my old Dell machine (but this had a conventional BIOS and not UEFI).

In my limited understanding of these things, it seems that the Linux bootloader (GRUB) got installed to the SSD and not the flashdrive and that to get things to work in the way I want them to work, the Linux bootloader needs to be "moved" from SSD to the flashdrive.

From this two questions:

  1. Is my understanding correct, and if so how do I move the bootloader (without messing up the Windows install)
2. If I have this all wrong, what do I need to do to get things to work in the way I want (as it was on my older Dell).
 
In the meantime the workaround for me is to set the boot order to the Windows Boot Manager by defualt (number 1) and change the order to have the Linux bootloader as 1 in the UEFI when I wish to run Ubuntu. This will work, but it is a nuisance as one of the things I use Ubuntu for is a daily back up of my computer.

Any advise would be greatly appreciated.

Cheers,

---

### Post by fantab on 2015-03-15
Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool to *"create a bootinfo summary"* note the url to the file and post the link here.
Keep the flashdrive plugged in when you use BR.

From the screenshots it looks like you've installed ubuntu in MBR mode. So Windows is booting in EFI and Ubuntu in MBR. Not a good thing.
To install Ubuntu you need a GPT partition scheme on the flashdrive. and it should also have an ESP FAT32 partition. Bootinfo should be able to tell us more.

Meanwhile go through this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Jacdeb6009 on 2015-03-15
Hi fantab,

Thanks for taking the time to respond.

I have run boot-repair as you suggested.  O booted the machine from a live DVD, installed boot-repair and ran it.  The report can be found at:
[INDENT]
[http://paste.ubuntu.com/10602658/](http://paste.ubuntu.com/10602658/)
[/INDENT]

I ran a second boot-repair with Ubuntu booted from the USB flashdrive and this report is at:

[INDENT]
[http://paste.ubuntu.com/10602724/](http://paste.ubuntu.com/10602724/)
[/INDENT]

I have looked at both, but I am afraid that I do not make head or tail out of either of these.

Your advice would be greatly appreciated.

Cheers,

---

### Post by ubfan1 on 2015-03-15
Looks like you set up the USB as a legacy boot, not a UEFI boot.
Read:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
for info on UEFI.
Basically, you need to boot the live media in UEFI mode to perform a UEFI installation.  The installer SHOULD make a 300M FAT32 partition with the boot flag on the target USB for holding the UEFI bootloaders (in directories /EFI/Boot and /EFI/ubuntu).  The nvram on you your host SHOULD simply have the USB device first.  And NOTHING other than the nvram order needs to be written to the host machine.  Now what actually happens may vary, but you can always just copy any files in the wrong directories to the right ones, the bootloaders are just files under UEFI, or use boot-repair to do the necessary work (and probably some unnecessary work too).  The minimal USB EFI partition is:
1)/EFI/ubuntu holding a grub.cfg file which merely bring in the maintained grub.cfg from your /boot/grub directory.
2)/EFI/Boot/bootx64.efi  which is a copy of grubx64.efi (with secure boot off).  If you want to enable secure boot, you should instead make /EFI/Boot/bootx64.efi a copy of shimx64.efi, and have grubx64.efi there too.  Actually, the secure boot setup works for both, so I'd do the additional work of copying one more file.
The host machine needs to have the USB device first in boot order, the default bootloader will be the /EFI/Boot/bootx64.efi, and that's it.
The installers tended to put everything on the host's system's EFI, but that's just in the /EFI/ubuntu directory, so may be easily removed (or just left there as a backup).

---

### Post by fantab on 2015-03-15
> **ubfan1 said:**
> Looks like you set up the USB as a legacy boot, not a UEFI boot.
Read:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
for info on UEFI.


+1.

```
parted -l:

Model: ATA SAMSUNG MZ7TD256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
**[COLOR=#b22222]Partition Table: gpt[/COLOR]**
Disk Flags:

Number  Start   End    Size   File system  Name                          Flags
1      1049kB  316MB  315MB  ntfs         Basic data partition          hidden, diag
2      316MB   840MB  524MB  fat32        EFI system partition          boot, esp
3      840MB   974MB  134MB               Microsoft reserved partition  msftres
4      974MB   256GB  255GB  ntfs         Basic data partition          msftdata


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 31.5GB
Sector size (logical/physical): 512B/512B
[COLOR=#b22222]**Partition Table: msdos**[/COLOR]
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
1      4129kB  15.0GB  15.0GB  primary   ext4            boot
2      15.0GB  31.5GB  16.5GB  extended
5      15.0GB  30.0GB  15.0GB  logical   ext4
6      30.0GB  31.5GB  1451MB  logical   linux-swap(v1)
```

As you can see Samsung HDD or /dev/sda is GPT partitioned. GPT [GUID Partition table] is a MUST for an OS to work in UEFI mode.
The Kingston or /dev/sdb is 'msdos' partitioned and this does NOT support UEFI booting.
Reinstall ubuntu in UEFI mode on USB device. You may also find this [**HOW TO**]("http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/") useful.
Remember -
1. how you boot Ubuntu DVD/USB to install is how you install. If you boot the media in UEFI mode then Ubuntu will install in UEFI mode.
[**See Here**]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know how you've booted.
2. Install bootloader, Grub to USB drive only, in your case /dev/sdb.

Good Luck.

---

### Post by oldfred on 2015-03-16
I thought you had to have gpt to boot in UEFI mode. But obviously live installer is not, so it is not an absolute requirement.
It looks like you installed in BIOS/CSM boot mode, but Boot-Repair converted to UEFI, by reinstalling the grub UEFI boot loader into the internal drive.

You could convert back to BIOS boot for Ubuntu and leave Windows as UEFI. But Booting is more difficult as you have to switch modes UEFI/BIOS each time you reboot into the other system. Generally better to have both as UEFI.

Even when I installed a second  copy of Ubuntu to a second drive and told it to install grub to sdb, it still installed grub to sda's efi partition. I just then copied that boot folder to the sdb efi partition.

You do not have to try to have both boot mode. Sudodus has had issues as updates get out of sync. But this shows how to install to a flash drive.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by Jacdeb6009 on 2015-03-17
Thanks fantab, ubfan1 and oldfred.

Quite a bit of valuable information to get my head around.  I will read through all of this in some more detail and then see what is to be done.  I will get back to this thread with further questions or, with a bit of luck, be able to mark it solved :)

Cheers,

---

### Post by sudodus on 2015-03-17
The following link describes how to install Ubuntu in UEFI mode. I removed the internal disk to avoid confusion during the installation.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)

---

### Post by Jacdeb6009 on 2015-03-18
Thanks sudodus,

I will take a good look through the explanation in the link you posted over the weekend (getting there...).  The installation is usable at the moment, but I have to keep changing the boot sequence in the nvram to boot Ubuntu... a bit of a nuisance.

Anyway, lots of info from everyone so I am sure I can get it to work.

Cheers,

---

### Post by rawlins02 on 2015-04-10
I have purchased the same computer. Preparing to install 14.04. Has this been solved?

---

### Post by oldfred on 2015-04-10
What is important is that you install Ubuntu in the same mode as Windows either UEFI or BIOS.
And if two drives use Something Else.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

See also info in the link in my signature.

---

### Post by rawlins02 on 2015-04-10
Yes thanks I will look for UEFI or BIOS. I'm planning on reading each of the how-tos you've listed carefully before attempting the install.

---

### Post by Jacdeb6009 on 2015-04-10
Hi Rawlins02,

My machine is a work machine (as you may have gathered from my earlier posts) and I am a bit reluctant to scratch around too much in case it gets FUBAR'd (and with Windows that is all too possible).

For the time being I have left it as it is.  On startup I press enter to get to the "boot" menu, then F12 to select the boot menu, then select ubuntu from this menu and "good to go".

It's a nuisance, but for now it works and since I only do this to run a backup every morning, it's no big deal.  The whole "business" takes me about 5 minutes (10 max.) and I can shutdown and reboot Windows.

At work (because of the restrictive policies) I am forced to use Windows, so the "dual boot" is only so I can run a proper back-up.

When I have a bit of time, I will read through all of the documents again and try and fix it.

I think it is not difficult to get it right the first time, the problem is that I simply did an external USB install as I have always done it (and I have done a large number of these), but with a UEFI set up that does not work in the same way...

I am sure with a bit of care you will get it to work!

---

### Post by sudodus on 2015-04-11
I have been trying different methods to make stable 'UEFI and BIOS' Ubuntu systems for USB pendrives. The current version looks very promising :-) See this link
[URL="http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506"]
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/URL]

---

