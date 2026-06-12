---
title: "best clean install practices"
date: 2018-11-15
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2018-11-15
Even thought I've been told that Ubuntu should run reasonably on an older system, after a long time struggling to make my current sytem (AMD 2.2ghz, 3GB RAM, 25GB ubuntu partition) run well  (it is contstantly greying out, bogging down, requiring daily reboots) I have "upgraded" (or rather got a new better old system) to an Intel I7 3.4Ghz 64bit with 8GB Ram and a 250GB HDD. I'll have an external 2T HDD attached. (and I'll want to keep the Windows 7 installed on the side.)

Apparently one error I made in my last install was not putting HOME in the best location (I think it wound up on the Ubuntu partition and so was frequently filling up and giving me No Disk Space errors).

before I get started on my fresh install on this new machine, can anyone give me a thumbnail sketch of an easy optimal configuration? How much space to allocated to Ubuntu, where to located HOME (and how to do that assuming it's not obvious)

I'd just like to get it right this time (or better)(

many thanks

---

### Post by oldfred on 2018-11-15
Every user has unique requirements. 
There is no one best answer, just multiple options depending on use.

My own installs are 25GB for / (root) and I include /home inside /, but have no data in /home, only the mostly hidden user settings. And even some large hidden folders like Thunderbird & Firefox profiles are in my data partition.

Most newer users just use / but need a larger / if saving lots of data.
Next suggestion is a separate /home partition, so / can be smaller & /home as large as you can make it. Makes backup slightly easier, and you then can reinstall Ubuntu or upgrade / easier (reusing /home but not reformatting it).

Or if dual booting with Windows, you may also want a shared NTFS data partition for some or most of your data. Back when I had XP I used a shared NTFS data partition. As I started using XP less & less, I created an ext4 data partition and had several Ubuntu versions installed using same data.

One advantage of /home partition is it is automatically added to fstab to mount on reboot and ownership & permissions are automatically set. If you use a data partition you have to do all that manually. But some users also split data partition(s). They may want all music or videos in a separate partition but keep some data in /home. It all is up to your desires. My own configuration had changed over the years.

So if you understand creating a mount in fstab and setting ownership & permissions, or are willing to learn, then data partition(s) may make sense. 
Best not to have too many partitions with smaller drives as then available space management can be an issue. If data in one partition, your available space can be used for any data. 

Default install is now just / (root). Swap is now a 2GB file, but a swap partition will be used if found. With 8GB of RAM, you should never use swap unless editing video or similar RAM intensive application. 

If UEFI install, which you probably should use with new system, it will also create and ESP - efi system partition (FAT32 with boot flag).
Older Windows 7 DVDs were BIOS only, newer DVDs allow UEFI boot. But Windows has to have the now 35 year old BIOS/MBR configuration for BIOS boot. And it must have gpt partitioning for UEFI boot.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]https://help.ubuntu.com/community/UEFI

Ubuntu should be installed in same boot mode as Windows, UEFI or BIOS.
For both Windows & Ubuntu how you boot install media from UEFI boot menu UEFI or BIOS, is then how it installs.
But if you force Windows install in BIOS mode to gpt drive, it will in effect erase drive in conversion from gpt to MBR, or vice-versa.

---

