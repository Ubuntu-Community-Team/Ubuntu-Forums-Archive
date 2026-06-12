---
title: "URGENT: Unable to boot Windows 7 aft installing Ubuntu 14 (Dual hard disk)"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by rowena2 on 2015-05-28
This is my first time trying to install Ubuntu; I am more familiar with using Macs.


  I had my Windows 7 pre-installed upon receiving a new desktop (Acer  Veriton with Intel i7 Processor, 32GB, 1TB HDD and 256GB SSD). Windows 7  was installed on the SSD, so I went ahead with installing Ubuntu onto  the HDD. I used a DVD with Ubuntu written on it and booted from the  removable disk drive (by changing the option on BIOS option page). I  mostly followed instructions I found from several threads here such as  creating "/, /home, /swap" (I am planning to do some intensive data  processing). I then selected the option of booting from 'sdb' which was  the HDD that I was installing Ubuntu on. 'sda' is the SSD with Windows. 


  However when I restarted my computer, I was able to successfully boot  to Ubuntu, but when I tried to change back to booting from Windows  (located on the SSD), I could not do so. I was brought to a black screen  with 'Windows Error Recovery' indicating that Windows files were  'damaged or configured incorrectly'. I tried to Launch Startup Repair  (recommended), but would be brought back repeatedly to this screen i.e.  it did not work. So I tried to Start Windows Normally, but was brought  to a second page stating 'Reboot and Select Proper Boot Device or Insert  Boot Media in selected device and press a key'. 


  **Picture links:** [http://i.imgur.com/Q6419fd.jpg](http://i.imgur.com/Q6419fd.jpg) 

  [URL="http://i.imgur.com/iNwBSZ5.jpg"]http://i.imgur.com/iNwBSZ5.jpg
[/URL]

  I am not sure what exactly I did wrong. In addition, I tried to use boot-repair but  it told me to boot into EFI mode as I was in  Legacy mode. Could the problem be because I have installed Ubuntu in  Legacy mode whereas Windows was installed in EFI mode? Windows was  installed upon arrival so I can't be sure. However, I did a print  summary from boot-repair that may be helpful: [paste.ubuntu.com/11422788]("http://paste.ubuntu.com/11422788/")

Any help would be greatly appreciated as I am of course, able to reformat everything from scratch including Windows but doing so without knowing the root cause would be really akin to a guessing game and hitting around in the dark.

---

### Post by Geoffrey_Arndt on 2015-05-29
Here's a good place to start re understanding uefi installs.   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also, you're right about legacy vs uefi . . . if windows installed in uefi firmware mode, then ubuntu needs install in uefi mode also.   Also, it's recommended to disable fast-startup or fast  boot in windows prior to doing install of ubuntu.    IF you shrunk windows partition (using windows disk mgmt tool), then it's also recommended to reboot windows once or sometimes twice immediately after the reduction so windows can run file checks & corrections if needed.

I also found this youtube video series informative:  [https://www.youtube.com/watch?v=C88g3p5l5l8](https://www.youtube.com/watch?v=C88g3p5l5l8)

---

### Post by Bucky Ball on 2015-05-29
> **rowena2 said:**
> Could the problem be because I have installed Ubuntu in  Legacy mode whereas Windows was installed in EFI mode?

Got it in one. If you have Win in UEFI, Ubuntu must be to. I suggest you reboot, get to the BIOS and switch off fast boot then reinstall Ubuntu in EFI mode. There's a good chance this is all it is. Ubuntu has installed grub and Win is now confused.

If you choose 'Something Else' when you get to the partitioning section, it will allow you to select partitions manually. Select the Ubuntu partitions that are already there ( / , which will be EXT4 filesystem, and /swap) and don't touch the rest (NTFS filesystem Win partitions). That's about all you have to do. Ubuntu should install it's entry into the Win EFI partition (FAT32) and all should be correct.

---

### Post by oldfred on 2015-05-30
You will need to reparition sdb which erases it. It is currently MBR, and the default is gpt partitioning like your sda for use with UEFI. Boot-Repair has created unusual configurations of Ubuntu on a MBR partitioned drive using the efi partition on the gpt drive to boot in UEFI mode. 
But once you have UEFI and gpt partitioning which your Windows is. You should only use UEFI and only use gpt partitioning.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I suggest an efi partition on sdb of 300MB or so, but it will not be used. I installed a second Ubuntu to sdb, told it to install boot loader to sdb, even monitored install closely and saw it say it was installing to sdb, but it overwrote my grub in sda. Since you have Windows, it will just write a new ubuntu folder in the efi partition on your sda.
You can and should copy ubuntu efi folder to sdb's efi, but that would only be a backup or if you wanted to use drive on another system.

Acer also seem to require you to specifically authorize another boot loader.
       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI

[/URL]
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]
[/URL]

---

