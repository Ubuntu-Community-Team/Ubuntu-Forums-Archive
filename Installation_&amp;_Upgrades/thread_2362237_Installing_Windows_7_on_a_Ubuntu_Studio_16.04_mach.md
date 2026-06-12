---
title: "Installing Windows 7 on a Ubuntu Studio 16.04 machine 64 bit"
date: 2017-05-25
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2017-05-25
Hello All, 

I am having difficulty in setting up a dual boot machine.  I am trying to get Windows 7 and Ubuntu Studio 16.04 to cooperate on one machine on a dual boot setup.   All attempts at trying to install Windows 7 first and then Ubuntu Studio 16.04 have failed.   Boot repair disk doesn't work anymore.  It worked fine up until version Ubuntu Studio 14.04.  But it could be that now I am using 64 bit operating systems.

In my frustration and need to get a working computer, I have installed only Ubuntu Studio on the said computer.   However, a need has arisen where I need to finally put Windows back on the machine.   I know that if I do this, the Windows boot loader will override grub and thus the machine will boot into Windows and not acknowledge Ubuntu Studio anymore.   In the past, again Boot Repair was the answer, but as I said above, it no longer works.

So my question is how can I set up a  dual boot system using the two operating systems mentioned above.

Thank You,

Geo

---

### Post by yancek on 2017-05-25
When I installed windows 10, it had an option "Custom" install.  I would boot the windows 7 install DVD and see if there is a similar option to give you a little control.  Have you created a primary ntfs partition on which to install windows or are you using unallocated space?  If you have a primary partition, be sure you mark it as active or boot partition which you can do from GParted which should be on the Ubuntu install DVD.

If you have a working Ubuntu installed, after installing windows all you need to do is reinstall Grub to the MBR (you are using MBR rather than UEFI??) and you can do that from the Ubuntu install DVD:  sudo grub-install /dev/sda  (that would be if the  drive with Ubuntu/windows is on sda.

Boot repiar "doesn't work" isn't very descriptive either.  Some specifics would be helpful but in your situation you should not need it if you have the Ubuntu install DVD.

---

### Post by gordintoronto on 2017-05-26
"All attempts .... have failed." What worked, how did you recognize failure?

You need to install Windows 7 first. Give it more or less half the hard drive. Shut it down, boot it up to check that it works. Shut it down, install Ubuntu Studio with "something else." Tell it to put Grub on /dev/sda.

---

### Post by oldfred on 2017-05-26
UEFI or BIOS?
Windows 7 default install from DVD is BIOS only. But it can be copied to flash drive and some files moved & renamed to make it UEFI bootable.
If drive is gpt partitioned Windows can only be installed in UEFI mode.
If drive is MBR partitioned Windows can only be installed in BIOS boot mode. And must be in a primary NTFS partition with the boot flag.

Details are very important to get Windows to install. Many complain about difficulty installing Ubuntu, but Windows is probably more difficult. It just that most never install an operating system at all.

---

### Post by jukingeo on 2017-05-29
> **gordintoronto said:**
> "All attempts .... have failed." What worked, how did you recognize failure?

You need to install Windows 7 first. Give it more or less half the hard drive. Shut it down, boot it up to check that it works. Shut it down, install Ubuntu Studio with "something else." Tell it to put Grub on /dev/sda.

That is what I meant.  Usually on Ubuntu / Windows machines, I install Windows first.  However, this time, the machine I am installing to isn't having it.  If I install Ubuntu 16.04 AFTER Windows, it doesn't boot into either operating system at all.

> **oldfred said:**
> UEFI or BIOS?

Don't know.  But I have seen UEFI before on that machine...so it is a safe bet to say it is UEFI


> Windows 7 default install from DVD is BIOS only. But it can be copied to flash drive and some files moved & renamed to make it UEFI bootable.

I can install it on that machine on it's own and it will work, but if I put Ubuntu on it, it will not work as I said above.


> If drive is gpt partitioned Windows can only be installed in UEFI mode.
If drive is MBR partitioned Windows can only be installed in BIOS boot mode. And must be in a primary NTFS partition with the boot flag.

How can I check for sure?

> Details are very important to get Windows to install. Many complain about difficulty installing Ubuntu, but Windows is probably more difficult. It just that most never install an operating system at all.

Naw, neither is that difficult on their own.  Just setting up machines to dual boot is a pain in the ass.

---

### Post by SeijiSensei on 2017-05-30
One alternative to consider is installing VirtualBox on Linux.  Then you can create a virtual machine and install Win7 into it.  The machine I'm on now has a Win7 VM if I need one.  Lot more convenient than dual booting unless you need to have Windows talk directly to the hardware for gaming.

---

### Post by oldfred on 2017-05-30
If you have UEFI hardware meaning within last 5 years, but install Windows in BIOS mode and Ubuntu in UEFI mode you probably break both boots. You can do that, but may have to go into UEFI and turn on BIOS to boot Windows and turn on UEFI to boot Ubuntu. And partitions may not be totally standard.

This shows current partitioning.
sudo parted -l

How you boot install media, is then how it installs for both Windows & Ubuntu.
If UEFI Secure boot is off, you should see two boot options for installer. UEFI:flash and flash where flash is a label or brand of flash drive.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

BIOS with MBR partitioning has been the standard since original PC or about 35 years. But now UEFI with gpt partitioning has advantages.
       
 Only 64 bit supported for UEFI boot, Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx) 
      How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

---

### Post by jukingeo on 2017-06-20
Sorry I been away for a while, but life has its way of keeping me busy...

> **SeijiSensei said:**
> One alternative to consider is installing VirtualBox on Linux.  Then you can create a virtual machine and install Win7 into it.  The machine I'm on now has a Win7 VM if I need one.  Lot more convenient than dual booting unless you need to have Windows talk directly to the hardware for gaming.

Is there a performance hit by doing it this way?  And yes, the main reason I am keeping windows is because I do play games.  Often I do hook up a controller to the computer.  Would this be an issue?

> **oldfred said:**
> If you have UEFI hardware meaning within last 5 years, but install Windows in BIOS mode and Ubuntu in UEFI mode you probably break both boots. You can do that, but may have to go into UEFI and turn on BIOS to boot Windows and turn on UEFI to boot Ubuntu. And partitions may not be totally standard.

I had something weird happen to me when I bought a new machine (the machine I am having an issue with is my wife's).   Grub somehow got obliterated and the computer naturally boots into Ubuntu.  HOWEVER, if I shut the machine down for a cold start and hit the F12 key, one of the booting options says, "Windows Partition" and I am able to boot windows that way.   I tried to do this with my wife's machine, but it didn't work.

> This shows current partitioning.
sudo parted -l

Ok, will do...

That is funny, on her machine the partitioning table says it is set up for msdos and not UEFI.  If that is the case, then I do not know why I am having the problem.  

> 
How you boot install media, is then how it installs for both Windows & Ubuntu.
If UEFI Secure boot is off, you should see two boot options for installer. UEFI:flash and flash where flash is a label or brand of flash drive.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> BIOS with MBR partitioning has been the standard since original PC or about 35 years. But now UEFI with gpt partitioning has advantages.

Yes, I have noticed the UEFI with my newest machine too.  Sadly I do not know too much about it and probably that is half the issue there.  I am looking for the easiest way to get this to work on my wife's machine.  She isn't as much of a performance guru as I am and she only plays on-line games.
       
>  Only 64 bit supported for UEFI boot, Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx) 
      How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

So in what order would I do the install?  Can I keep Ubuntu on the machine already or with any of those procedures above, am I going to have to start all over?

So I see the big problem is then Ubuntu is probably installing in UEFI mode and that is causing the Win7 DVD not to work.

I have another question.  Would it be simpler to buy another PHYSICAL hard drive and put Windows 7 on one and Ubuntu Studio on the other?

Thank you all.

Geo

---

### Post by SeijiSensei on 2017-06-21
> **jukingeo said:**
> Is there a performance hit by doing it this way?  And yes, the main reason I am keeping windows is because I do play games.  Often I do hook up a controller to the computer.  Would this be an issue?
Then I would go the other route.  Install Windows on the hardware, then install the Windows version of VirtualBox.  Create a Linux virtual machine and install Ubuntu into that.  If your reason for keeping Windows is gaming, then you'll want to have Windows be the primary OS.  If your use of Linux is primarily other activities like web browsing, reading mail, etc., running Ubuntu in a virtual machine won't interfere with anything like that.

---

