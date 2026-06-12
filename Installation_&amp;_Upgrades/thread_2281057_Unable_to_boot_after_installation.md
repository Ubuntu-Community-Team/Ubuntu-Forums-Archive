---
title: "Unable to boot after installation"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by CFoxess on 2015-06-04
Hello!

Basically I've been using windows for the longest time, and decided to dual boot my ultrabook.

Did installation with USB and it's all good until i've decided to wipe everything out and go for a clean install cos for reason my Windows 7 had issue loading up in dual boot after awhile. Which also affected my Ubuntu.

That's when the issue arised, I tried installing Ubuntu and subsequently many other Linux distros, now my disk is clean, reformatted multiple times, clean installations, after installation, it just doesn't boot and show a blinking underscore on the top left corner of a black screen.

Does anyone has any idea how this can be fixed? Any help at all would be great!

Thanks so much in advanced!

Some information on what i might have done to screw things up.
1. EasyBCD on Windows 7 to adjust the bootloader/Grub Menu(?)
2. Wiping out Ubuntu while the settings of EasyBCD was still in effect
3. I have formatted my disc a few times with.. the Disk Utility Function that return all data to 0
4. I have been adding partition table in gpt/msdos (Trial and error)
5. I have tried installing windows again and it works. At this point i am wondering if theres anything abt my SSD that only works w a NTFS environment.

Basically I just want a clean install of ubuntu to get my PC working again.

Live USB of Ubuntu works like a charm.

---

### Post by RobGoss on 2015-06-04
Hello and welcome, well I'm not sure what the specs are for your machine but if I were you I would make sure you're using 32 bit or 64 bit, depending on your computer.

---

### Post by grahammechanical on 2015-06-04
Can you get a live session to run? If not that is the first issue to get fixed. If you can run a live session what is stopping you from selecting Erase Disk and install Ubuntu? Let the installer carry the load.

You have an SDD drive but do you also have another hard drive? Is Ubuntu being installed to the SSD? Are you allowing the installation of a boot loader (Grub) and it is to the MBR of the SSD?

Regards.

---

### Post by oldfred on 2015-06-04
What brand/ model system? Probably UEFI with CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

How large is SSD?

Ultrabooks add a bit of complication. It used to be that Ubuntu would not install at all unless you turned off the Intel SRT and removed the RAID metadata. Now it seems to install, but grub wants to install in RAID mode but desktop version does not have its RAID drivers so fails.

If not still running Windows, many have just installed / (root) into SSD, and had /home or /mnt/data partition(s) for all user data. 

You do need to turn off the Intel SRT and change to AHCI.

You must be consistent with partitioning method and boot method.
If booting in UEFI mode, you need gpt partitioning and an efi partition.
If booting in BIOS mode with only Ubuntu you can use gpt but must have bios_grub partition.
If dual booting in BIOS mode, you must have MBR(msdos) partitioning as Windows only boots in BIOS mode from MBR partitioned drives.

       [http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Now older, so 14.04 or 15.04 should work better. If very new system, use the newest Ubuntu version.
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

### Post by CFoxess on 2015-06-05
Thank you so much for all the amazing answers. It's going to be hard to pinpoint the brand and model system cos I took over this laptop that's Anonymously made in China.

Size of SSD 120GB, Live session totally works. Is it possible to take my time to understand and try out the mentioned methods before marking it as solved? I have very little idea how things work around here. Though I am really impressed with all your help once again. Thank you so much!

---

### Post by oldfred on 2015-06-05
If a 120GB SSD that is not the typical Ultraboot which had 16 to 32 GB SSD. Those were just used as cache for RAM on restart for fast startup.

Just to see what it shows, run Boot-Repair and post link to summary report. It runs many commands which help us figure out issues.
Many UltraBooks also have dual video. Do you have dual video and can you control which it boots with or is it automatic?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

