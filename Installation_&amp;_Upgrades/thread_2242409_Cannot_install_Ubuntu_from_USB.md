---
title: "Cannot install Ubuntu from USB"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by luka4 on 2014-09-01
Hello everyone, I have a problem that I can't seem to find a solution for.

I used the Universal USB installer to create a bootable USB with Ubuntu 14.04, changed the boot order in BIOS to removable disk, and everything worked fine. While I was in the Ubutnu setup, I decided to cancel and return to Windows so I can copy over some files I forgot to another place so I can format the partition with Windows on it. However, when I copied the files over, and tried rebooting, the computer goes straight to Windows. I have checked the boot priority, even tried removing HDD and only keeping the USB on the boot list, but all I get is an error message saying that a boot media is not found. I have also tried making the bootable USB again with the USB installer, but the same thing happens. Any idea what to do?

---

### Post by yancek on 2014-09-01
Could you have accidentally have copied the files from windows to the usb you were using for the Ubuntu install?  Might explain the first problem but not the failure to re-create the bootable flash from windows again.  Is the usb plugged into the same port you used the first time?

---

### Post by luka4 on 2014-09-01
The files were copied to a different partition, triple checked. I tired plugging the USB into all the ports, went trough all the settings in BIOS I could think of, same situation every time.

EDIT: the annoying part is that it worked the first time.

---

### Post by grahammechanical on 2014-09-01
I experience something similar when I first started to use a USB memory stick. Then I noticed that the BIOS was seeing the USB stick as an external USB drive and changing the boot priority did not work but I entered another menu option where I could select the drive to boot from and it was there that I could move the USB external drive to the top of the list.

Regards.

---

### Post by luka4 on 2014-09-01
I've tried all the possible boot priority combinations, still nothing

---

### Post by yancek on 2014-09-01
The only logical conclusion that then come to mind would be that the flash drive went bad for whatever reason.  If you have another computer you can test it on that would discount that option.  Otherwise, another flash drive?

---

### Post by luka4 on 2014-09-02
I've managed to get the computer to recognize the USB on the boot menu by formating the USB as FAT32 using BOOTICE and then using the Universal USB Installer, but without the format disk option enabled. However, when attempting to boot from the USB, I now get a message saying "ERROR: No configuration file found. No DEFAULT or UI configuration directive found!".

I have tried renaming the isolinux folder and files to syslinux, but to no effect.

EDIT: Tried putting an older version of Ubuntu on a different USB drive, but the same thing happens. I suppose for some reason USB installation is out of the question.

---

