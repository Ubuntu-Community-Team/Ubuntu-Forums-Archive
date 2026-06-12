---
title: "Install Ubuntu on second hard disk"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by weigheyeman on 2007-04-02
Hi,

I am looking for some advice.

I am new to Linux (but not to PCs). I am about to install Ubuntu Linux on a second hard disk on my PC I already have XP running on the first hard disk and want to run Ubuntu OR XP. I reckon that it will be "cleaner" to keep the two OSs on different disks. I have the installation CD for Ubuntu 6.06.

Obviously I will follow the installation instructions but I would like to know if there's anything I need to watch out for? Any Gotchas? Any advice based on experience doing the same thing yourselves?

Thanks,

Charlie

---

### Post by Edho on 2007-04-02
Did that.

Put a second hd as slave.

Install Ubuntu (dapper for me).on that disk. = hdb
Follow obvis, instructions.

Qeustions about keyboard, resolution screen, size of swap,.....

Maybe attention on question.... where to install the bootloader GRUB.

>>>> ON MBR of masterdisk.

For me it was a succes on the first time.
Without knowledge from Ubuntu.


Later i did a repartition of my masterdisk.(was fully ntfs with os win on it)
A part with Fat32 format.
For data, reachable by win and lin.
I think with Qparted program (linux)

---

### Post by Bob Burd on 2007-04-02
I have a related question.

I installed Ubuntu on a secondary SATA drive since I wanted to have an older Ubuntu version left installed on the primary PATA drive. I was hoping to be able to use the BIOS settings to boot one or the other, but in my second install the IPL or GRUB is pointing to the MBR of the primary drive. This give me the option of changing boot at GRUB load time, but that's not what I want (and I might want to swap out the primary disk in the future). Is there a way to move/copy/reload GRUB to the SATA drive without having to reinstall Ubuntu (yet) again? 

Sorry if I have some of the terms wrong or confusing. I'm fairly new at this, and any help would be most appreciated.

thanks,

bob

---

### Post by psusi on 2007-04-02
Is there a reason you don't want to just use grub to choose which version to boot, instead of switching your bios boot drive?

---

### Post by bulldog on 2007-04-02
> **Bob Burd said:**
> I have a related question.

I installed Ubuntu on a secondary SATA drive since I wanted to have an older Ubuntu version left installed on the primary PATA drive. I was hoping to be able to use the BIOS settings to boot one or the other, but in my second install the IPL or GRUB is pointing to the MBR of the primary drive. This give me the option of changing boot at GRUB load time, but that's not what I want (and I might want to swap out the primary disk in the future). Is there a way to move/copy/reload GRUB to the SATA drive without having to reinstall Ubuntu (yet) again? 

Sorry if I have some of the terms wrong or confusing. I'm fairly new at this, and any help would be most appreciated.

thanks,

bob

You can reinstall GRUB from the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Be sure to use in the setup command the number of the hdd which is provided by the find command.
If the find command returns (hd1,?) use setup (hd1) the partition isn't important.

---

### Post by Bob Burd on 2007-04-03
Bulldog,

Thanks for the prompt reply. Sorry I couldn't try it sooner.

It almost worked. I went through the GRUB procedure you outlined, using hd2 (hd0 & hd1 are two other drives on my system). I set the BIOS to boot on this drive, but after attempting to load GRUB it came back with "File not found" and sent me to the GRUB menu, where I was unsuccessful on reattempts to load the proper kernel. At least I was able to reset the BIOS to boot to hd0 and get it back alive again, so it didn't kill the system. :-)

Any further suggestions, or am I not providing enough info?

thanks,

bob

---

### Post by confused57 on 2007-04-03
> **Bob Burd said:**
> Bulldog,

Thanks for the prompt reply. Sorry I couldn't try it sooner.

It almost worked. I went through the GRUB procedure you outlined, using hd2 (hd0 & hd1 are two other drives on my system). I set the BIOS to boot on this drive, but after attempting to load GRUB it came back with "File not found" and sent me to the GRUB menu, where I was unsuccessful on reattempts to load the proper kernel. At least I was able to reset the BIOS to boot to hd0 and get it back alive again, so it didn't kill the system. :-)

Any further suggestions, or am I not providing enough info?

thanks,

bob
Can you boot the Window's drive independent of grub?

You might want to boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

See the 3rd link in my signature for how I have my system set up for dual boot.

---

### Post by psusi on 2007-04-05
If you set the bios to boot from the 3rd drive in the system, then it IS hd0 to the boot loader.  The problem is that when you install grub, it assumes that hd0 is /dev/hda, not /dev/hdc, so you will have to correct it by issuing a device (hd0) /dev/hdc command to the grub installer.  

Give that command first when installing grub, then use hd0 in the config files to refer to the boot drive, even though it is actually the third disk in the system.

---

