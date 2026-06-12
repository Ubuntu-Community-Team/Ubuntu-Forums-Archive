---
title: "Trying To Install Ubuntu On My Laptop"
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2016-01-09
I got this new Dell Inspirion 5558 laptop with Windows 10 and 1TB hard drive on it and I wanted to keep it so I went into Disk Management and shrunk the partition to 300 GB.  I then installed Ubuntu with Universal USB Installer.  I then changed to Legacy mode in BIOS and booted onto my flash drive.  The problem is when I get to where I pick Something else and it shows you all the partitions I do not see Install Ubuntu alongside Windows 10!  I don't understand what is going on!  I should tell you I thought I could install Ubuntu with a disk like I did my desktop and I could see Windows and just overwrote it.  :confused:

---

### Post by grahammechanical on 2016-01-09
> I then changed to Legacy mode in BIOS and booted onto my flash drive.

Why did you do that? When a machine has Windows 10 pre-installed then Windows 10 will be installed in EFI mode. And that means that we must run the Ubuntu installer in EFI mode and Install Ubuntu in EFI mode as well.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

once we select the Something Else option we are past the point where we can choose to install Ubuntu alongside Windows. The option to install alongside should be present on the same window that offers Something Else. If it is not then it is most likely because Windows has been installed in EFI mode and the Ubuntu installer is running in Legacy mode. 

Regards

---

### Post by shane_faulkinbury2 on 2016-01-09
BIOS originally was in UEFI with only Windows Boot Manager available.  Do you mean I should have it on UEFI and then press F12 to get to boot options and boot to USB will be there?

Never mind, I just tried it and pressed F12 and the only option available for UEFI was Windows Boot Manager!  :sad:

Well I've got to sat I'm a total idiot!  I was thinking last night something has to be wrong xso I got on my cell and typed in "if on UEFI how do I boot to usb first" and there it was, "make sure usb is plugged in"!  So I plugged it in, fired it up, pressed F12 and low and behold there was usb in UEFI!  So everything is fine now with Windows 10 and Ubuntu 15.10 on my laptop.  :D

---

### Post by shane_faulkinbury2 on 2016-01-10
Now I'm really stumped!  I was on Ubuntu and wanted to make sure everything was okay on Windows so I restarted and picked Windows Boot Manager and Windows booted up fine.  After checking things out I wanted to go back to Ubuntu so I restarted and Windows came back up!  I restarted again and  the same thing.  So I booted into BIOS and tried Legacy and just got an error when booting.  I know Ubuntu is still on my machine, what could be wrong?  :confused:

---

### Post by Dennis N on 2016-01-10
I think Windows may have changed the boot order in UEFI boot menu to put itself first. That way, the system skips grub.

Try the one-time boot key to access UEFI boot menu and see if Ubuntu is listed, probably as second choice? If so, boot into Ubuntu, and use the efibootmgr tool to restore boot order to what you want.

---

### Post by shane_faulkinbury2 on 2016-01-10
Okay, I'll give it a try!

---

### Post by shane_faulkinbury2 on 2016-01-10
This is really starting to tick me off.  I found Ubuntu after pressing F12 on startup.  I press it and it says this, "No bootable devices found!  Possible cause's could be a corrupt OS image or a boot device is not enabled in BIOS setup."  So I guess it's back to BIOS!  :mad:

---

### Post by Dennis N on 2016-01-10
You might give the Boot Repair tool a try, and post the boot info summary as it directs (don't o.k. any repairs, until one of the experts here looks it over). Boot Repair is in the Ubuntu repositories.

OR

If you cannot boot Ubuntu to install it, you can obtain Boot Repair on a CD

[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

General Boot Repair Information:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

