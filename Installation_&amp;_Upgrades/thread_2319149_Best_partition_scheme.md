---
title: "Best partition scheme"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by mac-2check on 2016-04-01
Hello, 

I've got my father a new laptop, but I'm not sure about the partition scheme.

4 years ago when I bought my laptop, I divided it this way:

$ sudo parted -l
Model: ATA TOSHIBA MK3265GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  211MB   210MB   fat32                                 boot
 2      211MB   31,5GB  31,2GB  ext4            Basic data partition  msftdata
 3      31,5GB  318GB   287GB   ext4                                  msftdata
 4      318GB   320GB   2097MB  linux-swap(v1)


I checked a few pages, and it seems that the first partition I have - sda1 - fat32 is not really needed, so I think the new laptop, which has a 500 GB disc could be divided this way:

1. Sda1 40 GB ext4 - for the system - mount point: /
2. swap 8 GB
3. Sda2 - the rest 

I wonder if:
- the swap partition should be the last one, or it doesnt matter?
- on my laptop after booting, I have to always mount #3 partition. if I set a mounting point for the last and biggest partition on the new laptop (/mnt/disc-1 for instance), will it be automatically mounted after the start of the system?


thanks for replies,

Martin

---

### Post by oldfred on 2016-04-01
With gpt partitioning, the FAT32 partition is your boot files for UEFI boot.

You have to have a ESP - efi system partition which is FAT32 formatted with boot flag(if parted/gparted) or code ef00 if gdisk used.
That really is a very long GUID code so UEFI knows to look there for boot files. Not same as boot flag in BIOS/MBR old systems.

Or if you want BIOS boot, you have to have a bios_grub partition for grub to correctly install.

How you boot install media, UEFI or BIOS with new UEFI systems is then how Ubuntu (and Windows) installs.

During install, you cannot create an add a data partition. You can create and use a separate /home.
I normally partition in advance and use data partitions not /home, but /home is often easier for newer users to create.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by grahammechanical on 2016-04-01
A new laptop? Then it will most certainly have a UEFI boot system with GPT partitioning. Will Linux be the only OS?

If Windows is installed it will most definitely be installed in EFI mode & if you want to dual boot with Ubuntu then you will need to install Ubuntu in EFI mode. If Ubuntu is to be the only OS then it does not matter if we install Ubuntu in EFI mode or BIOS/Legacy/CSM mode. But with GPT partitioning certain boot files go into a boot partition. If it is an EFI mode install then efi boot files will go into a efi boot partition. If it is a BIOS mode install then Grub boot files will go into a bios boot partition. This is because of GPT partitioning. And it is not the same as having a /boot partition where Linux kernels go.

If dual booting with Windows the Ubuntu installer will make use of the existing efi boot partition to put the Linux boot files. No need to create one. If erasing Windows and installing Ubuntu it will be best to install Ubuntu in EFI mode as the installer will make use of the existing efi boot partition. But if installing Ubuntu in BIOS mode you will have to create a bios boot partition to work with GPT.

30 - 40 GB for Ubuntu ( / ) is more than enough. The Swap partition should be a little larger than RAM if it is intended to hibernate the OS. It can be smaller if there is no intention to hibernate. How much RAM does the machine have? 4GB and you thinking swap = twice RAM? If RAM is 8 GB then depending on what the user intends to use the machine for the OS might rarely use swap.

Hard discs are circular. They have inner & outer edges. We think in terms of first & last but that is visualizing things in a linear way that does not really apply to circular discs.

Regards.

---

### Post by Bucky Ball on 2016-04-01
Other's have given good advice and I only really have this to say about your scheme. You probably don't need 40Gb for / if you have a separate /home. 20-25Gb should be fine. Also, unless you're hibernating, 2Gb fine for RAM. 8Gb overkill. You'll never use it if not hibernating (also mentioned previously). 

As for the /swap partition being at the end, I *always* put it at the end, but I'm old schoool. In the days when it mattered, you put the OS on the fastest part of the drive (first partition), data on the next bit and /swap last, the slower or slowest part of the drive. Nowadays people seem to stick it anywhere, but I'm not into that! Nothing's changed here, I still use 7200rpm drives and I still try to squeeze what speed I can out of the beast. :| :D

---

### Post by mac-2check on 2016-04-02
Hello, thanks for the replies, I followed the wiki page, which oldfred posted, but I did not succeed.

I have bought this laptop: [http://www.acer.com/ac/it/IT/content/professional-model/NX.EFAET.002](http://www.acer.com/ac/it/IT/content/professional-model/NX.EFAET.002)
which has preinstalled Linux Linpus, so I thought it would be linux-friendly, but it doesn't seem so.

I tried to install xubuntu a couple of times, once I let the installer do it, then I tried my own idea, but nothing worked. At last, I used the boot repair disc, and it said it was successfully repaired, but still when I turn on the laptop I get: "no boatable device".

I've got the log from boot-repair linux so maybe it'll help: [http://paste.ubuntu.com/15580145/](http://paste.ubuntu.com/15580145/)

I also tried to google, and it seems people have had similar problems:

[http://ubuntuforums.org/showthread.php?t=2289346](http://ubuntuforums.org/showthread.php?t=2289346)

Since, it's a new machine, I'd rather ask you for help, than randomly try to repair it on my own.

Martin

---

### Post by oldfred on 2016-04-02
Every Acer we have seen requires you to set a UEFI password and enable trust on the grub/ubuntu files.
You may need to upgrade UEFI from Acer also. 

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

It looks like you have an UEFI install on a MBR partitioned drive. While that may work, UEFI normally uses gpt partitioning.
You also installed grub to sda1, you almost never install grub to a partition like sda1, but to a drive like sda. With UEFI installs, grub always installs correct its UEFI boot files into the ESP - efi system partition. 

Probably better to start over, but you may be able to convert.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by mac-2check on 2016-04-02
.

---

### Post by mac-2check on 2016-04-02
I found a guide and it works, so Im gonna install it again (this time properly) , and see if it works

Here is what seems to work for me: 

 I got it work at Acer Aspire ES1-111-C827. Should be working on other  devices, too. Probably the BIOS-entries are a bit different. All you  have to do is to register the newly installed UEFI-file as trusted for  executing in BIOS-security options.
  Before installation goto BIOS-Settings, make sure to have this:
  
[LIST]
[*]Security: set supervisor password; 
[*]Boot - BootMode: UEFI; 
[*]Boot - SecureBoot: enabled; 
[/LIST]
  After installation again go to BIOS-Settings
  
[LIST]
[*]Security - Select an UEFI file as trusted for executing Enter; 
[*]HDD0 appears Enter; 
[*]EFI appears Enter; 
[*]goto <ubuntu> Enter; 
[*]choose the first entry with .efi ("shimx64.efi" at my device) Enter; 
[*]give it a name Enter; 
[/LIST]
  save changes on exit BIOS; restart. Thats it.
     
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

Thanks for help guys!!!!

---

### Post by mac-2check on 2016-04-02
I reinstalled it, it doesnt work, yet I feel I'm close to solution.


When I boot the laptop I get an error saying: Default boot device missing or boot failed... and Im given the option to boot again, there is a boot option called System - this name I chose the first time I used the guide above, which worked. Then I reinstalled the system, but the settings for booting seems to remain the same, and when I go to bios and again follow these steps:
  

[LIST]
[*]Security - Select an UEFI file as trusted for executing Enter; 
[*]HDD0 appears Enter; 
[*]EFI appears Enter; 
[*]goto <ubuntu> Enter; 
[*]choose the first entry with .efi ("shimx64.efi" at my device) Enter; 
[*]give it a name Enter; 
[/LIST]

it doesnt work, and in the boot manager I see only one option: system - the same I used the first time. I used different names, but always appears only one - system

 I tried boot repair disc, which succeeded, but adds: *do not forget  to make your bios boot on sda1/efi/ubuntu/shimx64.efi.file*

I think I need to completely rewrite the file shimx64.efi.file, so that it fits the new system.


Would you know how?

---

### Post by oldfred on 2016-04-02
Shimx64.efi is the secure boot version of grubx64.efi.
Did in UEFI you set that as "trusted" and if you reinstalled, you probably have to reset it again.

And if secure boot is on, only shim will work, not grubx64.efi.
Shim should work for both UEFI secure boot on, and UEFI with secure boot off. 
Only with secure boot off, may you see two entries for ubuntu in UEFI boot menu. One uses shim and other uses grub. With secure boot off either should work.

With Secure boot on, you also have to boot installer in secure boot mode, so not just shim but signed kernels get installed. With secure boot off, you get the standard/unsigned kernels.

---

### Post by mac-2check on 2016-04-02
reset helped, and Im now writing from the new laptop. I ll mark the thread as solved.
Thanks for help :)

---

