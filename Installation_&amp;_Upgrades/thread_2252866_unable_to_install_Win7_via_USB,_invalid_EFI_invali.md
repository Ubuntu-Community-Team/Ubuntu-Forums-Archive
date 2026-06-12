---
title: "unable to install Win7 via USB, invalid EFI invalid filepath"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by edoardoamisano on 2014-11-15
Hello,
I have a Hp envy 4, some type of ultrabook i guess and i bought it with win8, then the hard disk broke so with the new hard disk I first installed kubuntu. I`m using Kubuntu and everything works well, but for college I need a Windows, and i`ve downloaded it and created a bootable USB with it. I start the computer and it goes directly to Kubuntu (the first option in the Bios/Uefi is to boot from the usb), so i tried to boot it via the grub. As I read in other threads I do:

set boot=(hd1)
chainloader +1

then it says:
efi invalid filepath

I tried with an Win8.1 bootable usb and the same thing happens. Also, I tried to install Kali linux but it skipped to kubuntu, but I haven`t tried with the grub.


Thank You

---

### Post by oldfred on 2014-11-15
Systems with Windows 8 pre-installed have UEFI with gpt partitioning. And Windows only boots from a gpt partitioned drive with UEFI.
But you may have installed Kubuntu in BIOS boot with either gpt or MBR partitioning.

How you boot installer both Windows & Linux is how it wants to install, but if partitioning is not correct it will not work.

Post this:
sudo parted -l

---

### Post by edoardoamisano on 2014-11-15
@oldfred, it says that it is a gpt when i do sudo parted -l. When i try to install windows it says thats it`s no possible because the device is of a gpt partition style. I don`t understand what it means. I partitioned the hard disk leaving a 100gb partition, first i tried it as a ntfsc and than i left it as a unallocated that windows converted it as ntfsc before giving me the gpt partition style problem. 
Any idea on how can i fix this, i`d like not to format the whole hdd but if it`s the only way i will try

Thank you again, and sorry for my english..

---

### Post by oldfred on 2014-11-15
Please post:
sudo parted -l

Are you Booting Kubuntu in UEFI mode? If not that is the issue as if drive is gpt Windows will only install in UEFI mode.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by edoardoamisano on 2014-11-15
[ATTACH=CONFIG]257992[/ATTACH]

---

### Post by oldfred on 2014-11-15
You have the efi partition, and since you show it mounted I think you are booting with UEFI.

Not sure why then Windows would not install to the unallocated space, if you have booted Windows in UEFI mode from flash drive. But you must boot Windows installer in UEFI boot mode, not BIOS/CSM/Legacy.

You could create the system reserved (MSR) as 128MB unformatted,  and main install NTFS partitions in advanced and see if then it installs?

Another who installed Windows 7 in UEFI.
[http://ubuntuforums.org/showthread.php?t=2249107](http://ubuntuforums.org/showthread.php?t=2249107)

---

