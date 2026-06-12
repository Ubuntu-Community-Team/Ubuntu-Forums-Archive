---
title: "Empty Grub menu after dual boot install of 20.10"
date: 2021-04-21
forum: Installation &amp; Upgrades
---

### Post by mknbl56 on 2021-04-21
I have been trying to do a dual boot  install of ubuntu desktop 20.10 on my laptop but having issues with brub being blank on completion and reboot. My setup is as follow

Dell Lattitude laptop with windows 10 installed as EFI boot on internal hard disk
A second hard drive on external ESATA port which I wish to install Ubuntu on
I have create a ubuntu install usb stick with it set to EFI boot type.

I have tried a couple of different install method

1. install long side windows, and 
2 something else  (Linux boot, root and EFI partitions created on second disk)  (Also tried setting the EFI one to be on the first disk.)

In all cases the install seems to go OK and I get to the point where it wants to reboot after install

On reboot it asks to remove installation media which I do 
the reboot ends up on a grub menu  but it  is empty with no OS listed to boot

If reboot and go into my bios setting / or boot selection options I can see there is now an ubuntu  entry added, and when I try and boot from it I get to grub  but grub is empty with nothing listed to boot.

examining the boot entry that has been created it shows

Filesystem: HD (4, GPT, -uuid - )
Filename: \EFI\ubuntu\shimx64.efi

Any ideas as to what might be going wrong or how best to investigate further ?
I am wondering if it is the case that the ESATA drive isn't being started up early enough in the boot process ?  
or any other ways of installation to try

---

### Post by yancek on 2021-04-21
The Ubuntu Ubiquity installer will install to the EFI partition on the first drive whether you select/set it to the 2nd drive.  Mount the EFI partition on the first (windows) drive and check to see if there is an ubuntu directory there.  If there is, copy that directory and its contents to the EFI partition you have created on the 2nd (Ubuntu) drive and try to boot..  Or, if you have an ubuntu directory in the EFI partition on the 1st drive, set the Ubuntu entry in the BIOS firmware to first boot priority.

---

### Post by mknbl56 on 2021-04-23
so yes it looks like it is installing to EFI on first drive, but I don't think that the issue.  On further investigation it looks like on my laptop the second drive on the esata port isn't made bootable. i.e. the esata device isn't bootable. at boot option bios stage the esata drive doesn't show on the list.   Other dell latitude laptops do seem to have bootable esata, but looks like it needs a firmware update that not available on my laptop, so looks like I need to do a bit of a rethink.

So it boots as far as grub, but can't see the files grub points to as they are on the 2nd drive so it just presents an empty grub prompt with nothing to boot

I think I will create a fat32 partition on 2nd drive  and copy some of my larger data files etc from main disk there and have it mounted under windows on a drive letter.   I can then shrink the partition on the 1st drive and create a Linux boot partition there. I can then create the other linux partitions on the 2nd drive
so both OSs will actually boot from first drive.   Does this sound like it should work.

The other thing I might check is to see if the esata drive is bootable in legacy bios mode, if so I may be able to do an MBR boot install for Linux, and I will have to switch between Linux and Windows by pressing F12 at boot time and changing the option there to select how I want to boot

anything else I might be able to try ?

---

### Post by oldfred on 2021-04-23
If grub installed to internal drive, it then usually does not matter if system boots from another drive as grub is just loading files from that other drive. So that may be a drive not coming up to speed in time.

A full boot partition on internal drive should also work and then eSATA should have time to come up to speed, if that is really the issue.

I always like to see details but do not know if this will show anything or not.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

