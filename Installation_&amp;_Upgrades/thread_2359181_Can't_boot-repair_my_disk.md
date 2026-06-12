---
title: "Can't boot-repair my disk"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by behosbeawesome on 2017-04-21
Hello everyone , i recently installed ubunutu 16.04 LTS and ran into some wireless issues so i uninstalled it , after that i tried many ISOs like arch linux , windows xp  , antegros even GPARTED llive session but i couldn't boot from any of those, After that I tried to boot into ubunutu live session and success but no luck installing boot-repair-tools so i downloaded the iso from sourcefrog but i couldn't boot from it either ? , so basically i can't boot from any ISO despite ubunutu 16.04 LTS the iso i installed lately .
here's my boot repair summary  after managing to download it on my live ubunutu : [URL="http://paste2.org/vsJp53Ed"]http://paste2.org/vsJp53Ed 
[/URL] ( Note that i get the error : Filesystem repair requires to unmount partitions )
and then successfully repaired but still can't boot from any iso  
i've tried many things uefi , legacy , change the usb ports , use dd or Unetbootin .

---

### Post by oldfred on 2017-04-21
Report shows just swap & empty ext4 partition.

Boot-Repair tried to run fsck. But that often is not a full fsck but just an internal check of drive.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda2
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda2 

You mention XP & UEFI. Is this an older system or newer with UEFI?
What brand/model system? What video card/chip?

If only installing Ubuntu may be better to use gpt partitioning.
And UEFI may be better, if hardware is UEFI.
But some systems require wireless drivers installed using Ethernet connection as installer does not  have every wireless driver.

---

### Post by behosbeawesome on 2017-04-21
i created a new partition table as msdos and left all the space unallocated tried to launch boot-repair and no recommended repair option , i'll try now to boot from ANTEGROS / Arch linux and see if there's success .
i mean by UEFI mood that i tried to boot every single iso in UEFI Mood and legacy mood also

---

### Post by oldfred on 2017-04-21
UEFI uses gpt, not MBR(msdos).
If partitioning in advance and only Linux use gpt. Then you can install in UEFI mode if you have the ESP - efi system partition or in BIOS mode if you have the bios_grub partition. Both only required on gpt partitioned drives.

I do not think Boot-Repair tries to do anything to an empty drive.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[URL="http://askubuntu.com/questions/446968/legacy-vs-uefi-help"]http://askubuntu.com/questions/446968/legacy-vs-uefi-help

      [/URL]
 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL] 

    [URL="http://askubuntu.com/questions/446968/legacy-vs-uefi-help"]
[/URL]

---

### Post by behosbeawesome on 2017-04-21
Well thank you sir for your kind help , I really appreciate that :KS
Actually I read about GPT and used it instead of MBR ( no difference for me ,But since I'm a Linux user lets go for GPT )
After that i created 3 partitions using GParted with live Ubuntu USB (as this is the only thing i can boot from )
sda1 /root  flaged as "boot,efi,BIOS_GRUB"
sda1 /home
sda3 /swap-area 
okay so now i burned Arch Linux 64bit onto my USB and tried to boot if I disabled Legacy boot i get black screen 
if legacy boot is enabled i get the error [Probing edd=off disable ok...]
the same thing happen almost with every ISO (tried Antegros 64bit )  like i said before .
So what should i do ?
Oh and one question should i install GRUB from a live Ubuntu before I install any other distribution ?

---

### Post by oldfred on 2017-04-21
Grub is normally installed as part of most Linux installs now.

You cannot have /, ESP & bios_grub as one partition. Those are three separate partitions with different formats.
I do not use /home, but a /mnt/data partition as I have several Ubuntu installs and mount same data in all of them.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
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

