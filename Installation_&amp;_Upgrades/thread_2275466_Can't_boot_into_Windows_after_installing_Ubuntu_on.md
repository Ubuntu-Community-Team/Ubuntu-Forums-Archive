---
title: "Can't boot into Windows after installing Ubuntu on usb drive"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by Arthur_Shapiro on 2015-04-26
I did a full install on an usb drive following the instructions here: [http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/).  Now getting "Operating system not found" message when try to start my Windows 7 laptop (Sony Vaio Series S).  Can't boot into the recovery partition on my internal drive either (don't have external recovery media).  Tried to reset BIOS settings to default, but didn't help.  Don't think there are any hardware issues, as everything works fine from the Ubuntu LiveUSB and I can see all the files on my internal drive.

Any suggestions on how to fix?  I found something called Boot-Repair.  Should I try that?

---

### Post by oldfred on 2015-04-26
Is system UEFI or BIOS?

 Post link to Summary report from Live installer with full install flash drive also plugged in.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I just did a full install to a flash drive on a UEFI system and getting grub correct is not easy.

And with BIOS installs I often had issues with drive numbers. Boot drive is always hd0 by BIOS & then grub, but install will think it is hd2 or hd1.

---

### Post by Arthur_Shapiro on 2015-04-26
It's UEFI.  Here is the link to summary report:  [http://paste.ubuntu.com/10899768/](http://paste.ubuntu.com/10899768/)

---

### Post by oldfred on 2015-04-26
You also have Sony and you have RAID which both are issues.
I did not think Ubuntu loaded the RAID drivers, so not sure if this was after Boot-Repair ran?

Your install on sdd used this for its efi boot loader, which is the Windows ESP - efi system partition inside the RAID.
 /dev/mapper/isw_jefgdbfdi_Volume0p3 /boot/efi       vfat    defaults        0       1

And Boot-Repair is suggesting just to reinstall to that. But with Sony you probably cannot boot the ubuntu entry in UEFI boot menu. Every Sony we have seen has modified UEFI to only allow Windows to boot. But they still allow the hard drive entry or /EFI/Boot/bootx64 entry to work, so with Sony we copy grub to be bootx64.efi. That alone may get you to boot ubuntu on flash drive.

You really want efi boot files on the flash drive. And no matter how many times I have tried to get grub to install/reinstall to any drive other than sda with UEFI, it always defaults to sda drive.
But UEFI is ok with files copied, if you copy the full ubuntu folder, or you do not have to use a command to do an install.

I would copy into the efi partition on the flash drive all of the ubuntu folder on the sda drive inside the RAID. But flash drives only boot from /EFI/Boot/bootx64.efi, so you have to also copy grub to be that file. It will still expect to find the rest of grub's files in /EFI/ubuntu so you need all of that.

My system has Ubuntu installed on sda, sdb & flash drive. Each install copied grub into the efi partition on sda. But only real difference was the UUID and partition in the grub.cfg in /EFI/ubuntu. 
My flash drive has booted directly from the efi partition on sda as a hard drive. I have not moved boot files to flash drive yet. I did move boot files to sdb drive, but my UEFI does not like the UEFI entry I created.


 From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. # Often sda1 or sda2 but varies. See below for RAID example.
sudo mount /dev/sda1 /mnt
# only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip backup command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

But in your case, I think the mount command would be something like this, you will have to verify. And you have to have RAID driver to allow mount to work.
      
 sudo mount /dev/mapper/isw_jefgdbfdi_Volume0p3 /mnt

If then you can boot from the hard drive entry in UEFI boot menu, we can copy /EFI/Boot & /EFI/ubuntu to flash drive and see if UEFI will let you directly boot flash drive.

---

### Post by Arthur_Shapiro on 2015-04-26
Oldfred, thanks for the detailed response.  At this point I really only care about booting back into Windows and don't need the Ubuntu flash drive boot.  Is there something simple I can do to  restore the boot settings to pre-ubuntu install state?

---

### Post by oldfred on 2015-04-26
You should be just able to go into UEFI boot menu and choose the Windows entry.
If that does not work then you need the Windows repair/recovery flash drive that Microsoft recommends you make.
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

If you can get to recovery screen in current install:
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

Often if you left hibernation or fast startup on, the only way to boot is directly from UEFI menu. And some systems have a fast boot setting in UEFI, so you can only get to UEFI from Windows. So if Windows does not boot you cannot fix it. Sometimes then a full cold boot will let you into UEFI. Unplug from wall and if battery powered remove battery also and hold power switch for 10 sec to drain remaining power.

---

### Post by Arthur_Shapiro on 2015-04-26
"You should be just able to go into UEFI boot menu and choose the Windows entry."  Can I do this from Ubuntu?

Is it worth trying to run boot-repair in standard mode?  Boot repair provides option to place boot flag on ...volume0p5 (Windows).  Is that worth trying?

---

### Post by oldfred on 2015-04-26
No.
If system is UEFI, the boot flag should only be on the efi partition. 
But because of the RAID, the report does not show all the details.
Only with BIOS would the boot flag be on the Windows partition with boot files, but that usually is a 100MB Boot partition, not main install.

UEFI is what BIOS used to be. You have to press some key often del or f2 but varies greatly before Windows starts to boot. And if fast boot in UEFI is on you have very little or no time to press that key. You have to look in manual for correct key to press. Full cold boot may give more time, but you must press correct key.
Back in BIOS days you had lots of time, and sometimes with odd computers I just started pressing keys. But that does not work with UEFI.

Grub menu has an entry that should boot you into UEFI.

```
 ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup

 }
### END /etc/grub.d/30_uefi-firmware ###
```

---

### Post by Vladlenin5000 on 2015-04-27
> **oldfred said:**
> Back in BIOS days you had lots of time, and sometimes with odd computers I just started pressing keys. But that does not work with UEFI.

For most UEFI implementations all you need to do is press ESC immediately after (or during) POST. Granted, you have a very limited time frame to act but it is doable. I'm doing it all the time now and I always have access both to UEFI settings and one-time boot menu (and a few other menu entries) regardless of what is or isn't installed.
No, Windows isn't required just for that. It may still be useful for certain updates if the manufacturer decides to package those as Windows executables but even in that scenario there are usually some way to "unpack" it and load the update from the UEFI settings.

---

