---
title: "first timer - ubuntu 16.04 failed something"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by frtali on 2016-10-10
Hey, i Just bought a new latitude and swapped the hard drive to ssd sandisk ultra ii.

I tried installing Ubuntu 16.04 about 4 times, all installation went smoothly (although I entered the installation from a weird &#8220;slim&#8221; menu, and I didn&#8217;t had to enable the flash drive in bios to begin with &#8211; nor did I had the option of enabling the specific usb drive).

**All my attempts to install ended in the same result - When I tried to boot, it went to dell memory check because it couldn&#8217;t find any bootable device (ahci enabled in bios, safe boot disabled - Gparted did recognize the flash drive + hard drive. only drive in bios &#8211; SATA 0).** I&#8217;m really afraid that I made a some kind of a mess with the new hard drive.I would like to know how to reverse the procedure and do it right this time.

installing process;
After I created bootable flash drive with PowerISo. I tried to install Ubuntu about 4 times:
1.      First time: I choose &#8220;erase disk and install Ubuntu&#8221;. Everything seemed ok.
2.      Seconed time: tried &#8220;something else&#8221; and messed with the partitions (all according to a youtube guide). Same result.
3.      Third time: tried &#8220;something else&#8221; with another youtube guide that instructed to first go to &#8220;try Ubuntu&#8221; and use the &#8220;Gparted&#8221;. (_Then there was a note that some drive is listed as 2420 mb and is actually 512_).
4.      Last attempt; &#8220;tried install Ubuntu alongside Ubuntu&#8221;.

thanks!

---

### Post by oldfred on 2016-10-10
New systems have three ways to boot. And boot of flash drive install may not be same boot mode system is set for.
How you boot install media - UEFI with Secure boot, UEFI, or BIOS/CSM/Legacy is then how system is configured to boot. So boot mode settings in UEFI must match the install mode.

Since new system you want UEFI/gpt. If you installed in BIOS mode, you probably set drive to the 35 year old BIOS/MBR configuration.

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
[URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

What brand/model system?
With my Asus & Gigabyte motherboards, I had to make many settings to get them to boot with Secure boot off (called "Other", not Windows), boot from USB, and then boot in UEFI mode, not CSM mode.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    [URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]
[/URL]

---

