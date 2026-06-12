---
title: "UEFI trials"
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by Tod Merley on 2016-01-18
A friend of mine would like to be able to boot Ubuntu from flash drive onto a Lenovo Yoga running W10.  This did not seem like a good idea to me but I have never tried it so...

I rotate my older Dell laptop and my newer “too cheap” HP[1].  The HP was used for these experiments.

Probably the strangest thing that I discovered through these experiments is that from the time the “restart” button was pressed after the installation program has completed to when the sign on screen of the newly installed OS appeared was consistently ONE HALF HOUR.  Something was delaying the first boot each time.  Install to SSD or flash drive.  Normal boot times thereafter.  Any idea why?

I guess I count it a fairly successful day as I did boot to Ubuntu 15.10 secure boot UEFI after booting to and updating a flash drive – which – was booted to non-secure UEFI Ubuntu 15.10 by disabling secure booting in bios and then choosing to boot by UEFI file and selecting /efi/ubuntu/grub on the flash drive.  I then reset bios to factory defaults to then booted back to the secure Ubuntu on the system SSD.

Along the way I discovered that the machine will not boot to any flash drive UEFI system without a valid UEFI OS on the system SSD (or HDD)  except that it will boot to one from a DVD without any SSD present.  I also found out that if the system SSD has an EFI partition and a flash drive has a partition set aside for EFI the Ubuntu installer will use the system SSD EFI partition but apparently place the key on the flash drive (this was while attempting to install to the flash drive).  Booting to the flash drive after this flowed well from the grub menu but booting to the system SSD at that point resulted in an authentication failure requiring a button press to actually boot to the SSD.  Attempts to boot to the SSD without the flash drive present resulted in no OS found.

I got around this by removing the system SSD when I installed to flash drive which yielded the results I mentioned as my “fairly successful day” mentioned above.

I was wondering if others could and would relate similar or other experiences using UEFI.  Long time to first boot? Only boots from key on one drive?

I was wondering if any have used UEFI as an alternate boot loader “no grub required”?

Any good UEFI managers out there?

[1] At least very similar to an HP 2000-2D49WM

---

### Post by Dennis N on 2016-01-18
Interesting observations. I'm not clear what you mean by 'key'.

On your questions:

Ubuntu's installer has a rule when running in UEFI mode to always install grub files to the first SATA drive on your system at the time of installation that has an EFI system partiton - sda. These identify the target OS which contains more grub files and grub.cfg to create the grub menu. If you install from a flash drive, and remove it, the EFI grub files it created are still there on the SSD, but the grub files on the target OS is no longer there to continue the process and show a boot menu. Even worse, If another UEFI Ubuntu OS was already installed on the SDD, using the same EFI system partition, it's unbootable as well, since the installation of the OS on the flash drive will replace the original grub files of the Ubuntu OS on the SSD. Nothing boots (unless Windows is installed too, or a non-Ubuntu Linux such as Fedora). This situation can be repaired, however. 

UEFI boot manager determines which boot loader to start based on its menu order unless you manually select one. It can't replace a boot loader in starting an OS.

I can't explain the 1/2 hour delay you experienced. Never seen anything unusual like that.

---

### Post by grahammechanical on 2016-01-18
This is an example of the kind of boot files that are needed to load both Windows and Ubuntu when they are installed in EFI mode on a motherboard with a UEFI boot system
> 
File system:       vfat
    Boot sector [SIZE=2]type[/SIZE]:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/bootx64.efi /ubuntu/shimx64.efi 
                       /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /Microsoft/Boot/bootmgfw.efi 
                       /Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

They go into a partition especially for that purpose. As already pointed out, this efi boot partition is usually on the main disk when Windows is on the machine and the Ubuntu installer automatically makes use of the partition for the Ubuntu efi boot files. The installer will then put certain grub configuration files in /boot of the Ubuntu partition on whatever drive Ubuntu was installed on.

My machine does not have an UEFI boot system. So, I cannot talk from personal experience. It is my guess that, if you want something more than installing Ubuntu to a USB memory stick with persistence, then the USB drive/memory stick would have to have GPT partitioning with a efi-boot partition and Ubuntu installed using the Something Else option.

Delays in OS loading are most likely down to the failure to find certain files, followed by repeated attempts to find those files. Which often result in failure to load the OS but in your case a kind of success. A file system check may also be taking place which is perhaps taking a long time due to the data transfer rate of the drive.

Regards.

---

### Post by oldfred on 2016-01-18
If an external device, UEFI boots from /EFI/Boot/bootx64.efi not /EFI/ubuntu.

My work around for full install to flash drive was to copy /EFI/ubuntu from sda to sdb (or whatever flash drive is). You must have the ESP - efi system partition on flash drive or external drive with gpt partitioning.

And then copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi. You need the /EFI/ubuntu folder as the version of grub that is copied seems to be hard coded to find the /EFI/ubuntu/grub.cfg that is a configfile with the UUID of the actual grub.cfg and your install on flash drive.

There is a grub install command to add the parameter --removable, but that is a manual grub install and you have to maintain the grub.cfg in the flash drive. I think you may be able to make it a configfile entry into an actual install's grub.cfg but have not tried that. I only use a direct grub install for my grub2 loopmount of ISOs where I manually create grub entries anyway.

---

### Post by Tom_S. on 2016-01-18
> **Tod Merley said:**
> A friend of mine would like to be able to boot Ubuntu from flash drive onto a Lenovo Yoga running W10.
...
I got around this by removing the system SSD when I installed to flash drive which yielded the results I mentioned as my “fairly successful day” mentioned above.


I had the same problem - the Ubuntu installer will install to sda (the system SSD) even if you tell it not to, on a UEFI system. Being that I have a Surface Pro 3 I couldn't pull the system SSD. Thanks to forum members I developed a procedure that worked for me: [http://ubuntuforums.org/showthread.php?t=2309963](http://ubuntuforums.org/showthread.php?t=2309963)

---

### Post by Tod Merley on 2016-01-19
[Dennis N. wrote:]Interesting observations. I'm not clear what you mean by 'key'.[end quote]

At this point I am not sure as well.  I think I am talking about the security certificate which is used by the secure boot UEFI bios function to “sign” the OS before loading.  I need to come to understand where these are and how they are used.  If the DVD can always load then perhaps a flash drive should be able to be made which will always load on any UEFI machine in secure mode – I think.

[Dennis N. wrote:]On your questions:

Ubuntu's installer has a rule when running in UEFI mode to always install grub files to the first SATA drive on your system at the time of installation that has an EFI system partiton - sda. These identify the target OS which contains more grub files and grub.cfg to create the grub menu. If you install from a flash drive, and remove it, the EFI grub files it created are still there on the SSD, but the grub files on the target OS is no longer there to continue the process and show a boot menu. Even worse, If another UEFI Ubuntu OS was already installed on the SDD, using the same EFI system partition, it's unbootable as well[end quote]

Yup I pretty well proved this during my experiments.  

[Dennis N. wrote:], since the installation of the OS on the flash drive will replace the original grub files of the Ubuntu OS on the SSD. Nothing boots (unless Windows is installed too, or a non-Ubuntu Linux such as Fedora). This situation can be repaired, however.*

UEFI boot manager determines which boot loader to start based on its menu order unless you manually select one. It can't replace a boot loader in starting an OS.[end quote]

Yes the machine I was working with had the Windows drive removed.  I actually got the box because my other laptop was in the shop (well actually going to the shop) and it was cheap, had a DVD drive (a place to put a Ubuntu SSD), and learning about W8 seemed a potential plus.  However two months after the warranty ran out Windows updates began crashing – eventually it was too much of a time waister so the DVD drive bay went back in and the Ubuntu drive became the main.

During the experiments I simply let the installer choose how to format the drive.

[Dennis N. wrote:]I can't explain the 1/2 hour delay you experienced. Never seen anything unusual like that.[end quote]

Very good information.  I am considering making a bug report.

---

### Post by Dennis N on 2016-01-19
Good comments. I will add a couple of additional observations:

1) The fact that Ubuntu's installer in UEFI mode always installs some grub files to an EFI system partition on the first SATA drive doesn't apply to other Linux distros and their installers: For example, Fedora installer will allow you to install grub files to the disk and EFI system partition of your choice - and you can have more than one EFI system partition per drive. I think maybe Ubuntu did this to simplify the installer? I have used two EFI system partitions on the same drive to see if it works. It does.

2) I originally used secure boot only. This changed when I learned some other Linux distros (even Linux Mint) will not install or boot with secure boot on. So to dual boot Ubuntu and Linux Mint, it is convenient to leave it off.

---

### Post by Tod Merley on 2016-01-20
Thank you very much for the response.

> **grahammechanical said:**
> This is an example of the kind of boot files that are needed to load both Windows and Ubuntu when they are installed in EFI mode on a motherboard with a UEFI boot system

They go into a partition especially for that purpose. As already pointed out, this efi boot partition is usually on the main disk when Windows is on the machine and the Ubuntu installer automatically makes use of the partition for the Ubuntu efi boot files. The installer will then put certain grub configuration files in /boot of the Ubuntu partition on whatever drive Ubuntu was installed on.

I did a bit of poking around in one of them (probably the one where the certs are):

tod@tod-HP2000:/media/tod$ sudo mkdir EFI
/media/tod$ sudo mount /dev/sdb1 /media/tod/EFI
tod@tod-HP2000:/media/tod$ sudo -s
root@tod-HP2000:/media/tod/EFI/EFI/ubuntu# hexdump -C shimx64.efi | less

...
00000040  0e 1f ba 0e 00 b4 09 cd  21 b8 01 4c cd 21 54 68  |........!..L.!Th|
00000050  69 73 20 70 72 6f 67 72  61 6d 20 63 61 6e 6e 6f  |is program canno|
00000060  74 20 62 65 20 72 75 6e  20 69 6e 20 44 4f 53 20  |t be run in DOS |
00000070  6d 6f 64 65 2e 0d 0d 0a  24 00 00 00 00 00 00 00  |mode....$.......|
00000080  50 45 00 00 64 86 08 00  05 09 0c 00 00 ba 11 00  |PE..d...........|
00000090  7a 0d 00 00 f0 00 06 02  0b 02 02 19 00 f6 09 00  |z...............|
...
000001b0  2e 74 65 78 74 00 00 00  ec f5 09 00 00 c0 01 00  |.text...........|
000001c0  00 f6 09 00 00 66 01 00  00 00 00 00 00 00 00 00  |.....f..........|
000001d0  00 00 00 00 20 00 50 60  2e 72 65 6c 6f 63 00 00  |.... .P`.reloc..|
000001e0  0a 00 00 00 00 c0 0b 00  00 02 00 00 00 5c 0b 00  |.............\..|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 40 00 10 42  |............@..B|
00000200  2e 64 61 74 61 00 00 00  18 d7 02 00 00 d0 0b 00  |.data...........|
00000210  00 d8 02 00 00 5e 0b 00  00 00 00 00 00 00 00 00  |.....^..........|
00000220  00 00 00 00 40 00 70 c0  2f 31 34 00 00 00 00 00  |....@.p./14.....|
00000230  49 04 00 00 00 b0 0e 00  00 06 00 00 00 36 0e 00  |I............6..|
00000240  00 00 00 00 00 00 00 00  00 00 00 00 40 00 10 40  |............@..@|
00000250  2e 64 79 6e 61 6d 69 63  f0 00 00 00 00 c0 0e 00  |.dynamic........|
...
00000290  00 00 00 00 00 00 00 00  00 00 00 00 40 00 40 40  |............@.@@|
000002a0  2e 64 79 6e 73 79 6d 00  38 e5 00 00 00 70 11 00  |.dynsym.8....p..|
...
0013ab00  f9 e8 44 0d 03 97 d1 50  13 30 81 98 30 81 80 a4  |..D....P.0..0...|
0013ab10  7e 30 7c 31 0b 30 09 06  03 55 04 06 13 02 55 53  |~0|1.0...U....US|
0013ab20  31 13 30 11 06 03 55 04  08 13 0a 57 61 73 68 69  |1.0...U....Washi|
0013ab30  6e 67 74 6f 6e 31 10 30  0e 06 03 55 04 07 13 07  |ngton1.0...U....|
0013ab40  52 65 64 6d 6f 6e 64 31  1e 30 1c 06 03 55 04 0a  |Redmond1.0...U..|
0013ab50  13 15 4d 69 63 72 6f 73  6f 66 74 20 43 6f 72 70  |..Microsoft Corp|
0013ab60  6f 72 61 74 69 6f 6e 31  26 30 24 06 03 55 04 03  |oration1&0$..U..|
0013ab70  13 1d 4d 69 63 72 6f 73  6f 66 74 20 54 69 6d 65  |..Microsoft Time|
0013ab80  2d 53 74 61 6d 70 20 50  43 41 20 32 30 31 30 02  |-Stamp PCA 2010.|
0013ab90  13 33 00 00 00 54 4e 86  ab 83 93 72 d6 e9 00 00  |.3...TN....r....|
0013aba0  00 00 00 54 30 16 04 14  9f 9d e1 37 53 8f 3b 28  |...T0......7S.;(|


It seems to be mostly tables.


> **grahammechanical said:**
> My machine does not have an UEFI boot system. So, I cannot talk from personal experience. It is my guess that, if you want something more than installing Ubuntu to a USB memory stick with persistence, then the USB drive/memory stick would have to have GPT partitioning with a efi-boot partition and Ubuntu installed using the Something Else option.

Normally I try to stay away from changing the several megabyte seemingly “blank” portion of a flash drive and use gparted to make some space.  But after your mention of GPT I decided to let the installer do the partitioning of the drive (erase and install).

Currently I have done a UEFI secure boot install of Ubuntu 15.10 to the machine SSD and to a flash drive successfully.  However making the flash drive (I had to remove the SSD to do this – installer issue) broke secure boot to the SSD.  I think I would call the whole “secure boot” thing a bit under developed at this time.  At the moment secure boot is disabled allowing the machine to boot to the SSD just fine.  The flash drive does not show up in the BIOS Boot Manager screen (ESC > F9) but I can boot to the drive by selecting “Boot from EFI File” selecting the drive and then “EFI” then “ubuntu” followed by “grubx64.efi”.  

> **grahammechanical said:**
> Delays in OS loading are most likely down to the failure to find certain files, followed by repeated attempts to find those files. Which often result in failure to load the OS but in your case a kind of success. A file system check may also be taking place which is perhaps taking a long time due to the data transfer rate of the drive.

Regards.

After noting that my first update after install contained a note that “all files have been downloaded” I am suspicious that my selection of “download files while installing” during the installation process resulted in a “background” downloading which took the half hour between “reboot” button push and installed OS screen open.

Next time I will try to remember to not choose that and see if the issue goes away.

---

### Post by Tod Merley on 2016-01-21
I hope to make full use of all of the responses to this thread but seem to be good to respond to only one post a day even though the information has likely sent me on a quest to &#8220;learn and try&#8221; as I work toward a fully Ubuntu UEFI secure boot drive for my friend.

I have set up a UEFI learning folder now filled with many presentations, PDFs, and links to sites and blogs.  The spec alone is over 2000 pages.  Bootloader and firmware security are two areas of great development these days it seems.

The link below is kind of a gem in that it allowed me to get a bit of a picture of how the secure boot keys are used and where some of the EFI files on a Linux EFI partition come from:

[http://blog.hansenpartnership.com/wp-uploads/2013/02/UEFI-Secure-Boot-2013.pdf](http://blog.hansenpartnership.com/wp-uploads/2013/02/UEFI-Secure-Boot-2013.pdf)

The number of PDFs, presentations, and blogs that deal with how very much vulnerable firmware including UEFI secure boot BIOS is amazing and disturbing.  I guess I will go with only one specifically because the references are so useful:

[https://events.ccc.de/congress/2014/Fahrplan/system/attachments/2566/original/venamis_whitepaper.pdf](https://events.ccc.de/congress/2014/Fahrplan/system/attachments/2566/original/venamis_whitepaper.pdf) 

Thanks for helping and happy reading.

---

### Post by sudodus on 2016-01-21
I can add some links, that you may find useful.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), particularly (but not only) the paragraph about [UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

[mkusb](https://help.ubuntu.com/community/mkusb)

[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

You can run a live system from an external drive (CD/DVD/USB/eSATA/flash card), or a persistent live system or an installed system (installed in a way similar to installed into an internal drive).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

If you want a portable installed system in UEFI mode, there are some difficulties, but the system of the following link works.

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

---

