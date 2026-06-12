---
title: "Lenovo Thinkcentre Edge 71 Ubuntu installs but disk is not bootable"
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by Peter_McNeill on 2020-03-15
I have been trying for about 24 hours now to install Ubuntu 18.04 Desktop on a Lenovo Thinkcentre Edge 71 (bios is the latest version - 9QKT39A  from August 2012)

I am installing Ubuntu 18.04 64bit only on a clean 500GB hard disk. This is not a dual boot system as this will (hopefully) become a software development and testing only system

Options are for a full clean install, erasing previous partitions, installing updates and 3rd party software, English UK with UK windows keyboard

boot options are hdd first. I use the f12 "temporary startuo device" route to boot the installation media and check it is trying to boot the hdd after installation

Ubuntu installs perfectly from either dvd or usb thumb drive or so all appears. 

I have tried downloading a new copy of the .iso file

I have tried using different tools on different machines and different operating systems (even resorting to using windows) to prepare my installation media the result is the same. I am running a mixed windows and linux (mostly Ubuntu) network with a few "oddities" hanging off the edges.

I have tried fixing the boot with Boot-Repair-Disk which tells me that it has reinstalled grub and that everything is now all right but guess what...

Whatever i do the result is always the same...

[B]This is not a bootable disk
Please insert a bootable floppy and
Press any key to try again
[/B]
!!! A bootable floppy - whatever next (sadly I have been around computers long enough to remember floppies from the days when they really were floppy and some of them 8" rather than 5.25" or 3.5" together 1/2" tape and even paper tape :-) )

This is driving me up the wall !!!!

I suspect it has something to do with UEFI (which lenovo claim to be in the bios?) but the "bios" has no helpful options like secure boot.
It has a "quick boot" option so I have tried installing and subsequently booting with it both enabled and disabled (all combinations)

You can tell that I am desperate enough to try anything - well nearly anything - I put my foot down at the idea of returning it to windows 10 as was suggested to me just now by a "friend"

Please someone tell me what I am missing before the men in the white coats come to take me away

Thank you kindly people

---

### Post by yancek on 2020-03-15
> I have tried downloading a new copy of the .iso file 

Did you do an md5 or shasum check to verify there were not problems in the download from the Ubuntu repositories to your computer?
Since you want only Ubuntu, did you use the Erase disk and install Ubuntu option or some other option?
How old is this computer if the latest BIOS firmware is 8 years old?
If you have boot repair, why did you not select the option to Create BootInfo Summary and post the link you get here?  That will give members detailed information and someone might be able to help.

> I suspect it has something to do with UEFI (which lenovo claim to be in the bios?) 

Does that mean you have contacted Lenovo support regarding this problem?  I doubt if the computer is 8 or more years old that it is UEFI capable.  When you access the BIOS firmware, do you see any reference to UEFI?

---

### Post by Peter_McNeill on 2020-03-15
Thank you yancek for your response.

I have verified the download and it is ok. I also verified the download I did on when I downloaded it again on the windows pc rather than copy it across the network. I could not do so when I used UNetBootin to make a boot disk from its own download. 

I did indeed use the "erase disk and install " option

I am not sure of the exact age of the computer but it has been around here for some years running windows until recently replaced making it available for repurposing

I too was doubtful about UEFi but the bios upgrade (I checked the Lenovo site) is described as "flash UEFI BIOS update". As I remember the early days of UEFI were difficult.

I have not contacted Lenovo support. As far as I am aware the computer was never offered with any version of linux and is now elderly as you point out. I would not expect any help from them.

As regards uefi content in bios I can add nothing to my first post. There is nothing obvious.

I have generated a boot info script from boot-repair (I am afraid that I did not keep the original reports - I also tried this several times) It can be found at [http://paste.ubuntu.com/p/Gcc7nXy6BT/](http://paste.ubuntu.com/p/Gcc7nXy6BT/)

Hope this answers your queries. 

Any thoughts what might be going on?

Peter

---

### Post by yancek on 2020-03-15
If your computer was UEFI capable it would be obvious by accessing the BIOS firmware on the motherboard.  If you see no mention of it in the BIOS, then it is not UEFI capable.  The problem is, you did an EFI install of Ubuntu as noted in the boot repair script.  sda1 clearly shows as an EFI partition and at the very top of the boot repair script, it shows no Grub code in the MBR which is necessary to boot a Legacy machine.  I'm surprised it installed EFI if the machine shows nothing EFI in the BIOS.  Probably simplest solution is to just reinstall but make sure it is Legacy and you install Grub to /dev/sda which will put boot code in the MBR.

You can tell if you are booted in Legacy mode.  Go to the site below to the section "identifying if the computer boots the Ubuntu DVD/USB in UEFI/Legacy mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Peter_McNeill on 2020-03-16
Once again thank you for your reply.

Following the advice on the link you gave me I have converted the install to legacy mode using boot repair and the system now boots properly. Thank you!

[QUOTE=yancek;13939144]
The problem is, you did an EFI install of Ubuntu as noted in the boot repair script.  sda1 clearly shows as an EFI partition and at the very top of the boot repair script, it shows no Grub code in the MBR which is necessary to boot a Legacy machine. 

However, I am not clear on what you mean. I simply did an install from the standard media. I did not choose to do a uefi install or not.

For future reference. How do I do or not do a efi install? 

Meanwhile I can start configuring the new system

With gratitude
Peter

---

