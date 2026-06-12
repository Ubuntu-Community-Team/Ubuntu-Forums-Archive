---
title: "(UEFI) Trying to install Ubuntu 13.04, having grub2 issues. Booting to a black screen"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by AyJJ7fd on 2013-10-06
I am trying to install Ubuntu 13.04 onto a 1TB internal hard drive via a USB drive. I go through the installation fine, but every time I try to boot the drive, there is only a black screen with a blinking cursor. I have let the installer automate the partitioning of the drive, and have also tried partitioning the drive myself multiple ways. Each way is unsuccessful. Here is my most recent boot-repair summary: [paste.ubuntu.com/6187013]("http://www.paste.ubuntu.com/6187013")[COLOR=#000000]. /sda is the drive I am trying to install Ubuntu onto, and /sdb is the 8GB USB drive with LiveOS on it.
Can someone help me figure this out?[/COLOR]

---

### Post by Amorphous Serendipity on 2013-10-06
Hi AyJJ7fd,

I've seen this happen a few times in the past for several reasons. In this case it looks like a partitioning issue.

Actions I would take:
1 - Burn the Ubuntu ISO to a CD/DVD (I know it's old school, but at least it will rule out issues with the UFD)
     a - If you need to use a UFD I would format it and use something like Yumi to make it bootable.
2 - Boot into Ubuntu.
3 - Start gparted, remove all partitions from the HDD and create a new partition table.
3  - Start the Ubuntu installer and do manual partitioning (you can just  do a simple partition setup such as: /boot [ext4], swap, and then /  [ext4] -- The key is to have /boot first and that it is bigger than 200MB.)

If  that doesn't work, this may be an issues with how you computer is  reading the HDD (doubtful, but still). You can try disabling  UEFI/enabling legacy boot options and switching from IDE to AHCI or the  reverse (odd, I know, but I've actually seen it work).

I hope this resolves your issues.

Please note!: I am assuming you are not dual booting.

---

### Post by oldfred on 2013-10-07
What video card/chip?
Often you need nomodeset.
From grub menu use e for edit, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

   [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by AyJJ7fd on 2013-10-08
> [COLOR=#000000]If that doesn't work, this may be an issues with how you computer is reading the HDD (doubtful, but still). You can try disabling UEFI/enabling legacy boot options and switching from IDE to AHCI or the reverse (odd, I know, but I've actually seen it work).[/COLOR]
Followed all your other steps, installing now and I will see if I can boot. Edit: Still got black screen, partitioned it like you said. I'm not sure how to disable UEFI or enable legacy boot options in my BIOS. I have an Intel P67 mobo. Also, not sure how to switch from IDE to AHCI. Any guidance with doing that?

oldfred: I have a Radeon HD6950, unfortunately I cannot even access the grub menu to enter nomodeset. I'm booting to a black screen, no grub at all.

---

### Post by oldfred on 2013-10-08
I am not sure if P67 had UEFI or not. Some vendors started with a limited UEFI, but all UEFI systems have BIOS/legacy mode often called CSM.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Somewhere in BIOS should be hard drive settings, may also have RAID, IDE & AHCI as hard drive options. I think with UEFI it is either AHCI or RAID, and you usually do not want RAID for a desktop.

If you only have Ubuntu installed you do not normally get grub menu as you only have one system to boot. If BIOS mode hold shift key from BIOS until menu appears. Some with UEFI use escape key to get menu?

I do not know AMD but have some links. Not sure all are even current.
      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)


 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by AyJJ7fd on 2013-10-08
Thanks for all the help guys, finally got it to work after about a week of messing with it.
My solution was to update my P6P67 BIOS to the most recent version, then repartition my drive with an EFI boot partition first, then /boot, swap space, and /. Such a relief to finally have Ubuntu up and running.

---

