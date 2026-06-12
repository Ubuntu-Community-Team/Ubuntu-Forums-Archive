---
title: "Gigabyte motherboard - Award Bios, can't boot from a usb disk."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by svendbenno on 2010-04-08
Hi. I've finally decided to stop using windows 100%, and make Ubuntu my primary os.

I've had Ubuntu installed on my computer using the wubi-installer, but now i want to boot from my usb-disk and install Ubuntu that way. 

I've made a bootable usb-disk with Ubuntu 9.10, using unetbootin. This method have always worked when i wanted to install ubuntu onto my netbook, but for some reason my workstation-computer can't boot from the usb disk. 

When i select the disk to boot from, my "Sandisk Cruzer"-disk doesn't show up. 

My motherboard is a Gigabyte GA-MA78GM-UD2h with Award Bios installed.

How do i make it boot from the usb-disk?

---

### Post by oldfred on 2010-04-08
Welcome to the forums.

For the longest time I thought I could not boot from a USB key I made. It worked on my portable but not my desktop. I tried all the USB settings. USB floppy, USB, USB CD etc. 

One day I had the key plugged in but wanted to select a different Hard drive and there it was. It was not a USB device but a hard drive.

---

### Post by svendbenno on 2010-04-08
> **oldfred said:**
> Welcome to the forums.  
Thanks :-D

The usb-drive isn't showing up there either. 
Though when i start up my computer, after the first screen(were i open the bootmenu, bios etc.), it shows up as a "usb storage device". :confused:

---

### Post by svendbenno on 2010-04-08
I just found out that my BIOS wasn't the latest version, so i updated it through Gigabytes @BIOS software. 

The drive is showing up now. 
Cheers, and thanks for the reply! :P

---

### Post by peertop on 2012-09-07
I solved it with formate the usb from win7 cmd in admin mode,

diskpart
list disks
select disk <your usb drive number>
clean
create partition primary
select partition 1
active
format fs=fat32 quick
assign
exit

download or use your win7 installation dvd and
navigate to the /dvd/boot directory and run the command: 

bootsect /nt60 h:  (use your usb driver letter)

transfer ubuntu from unetbootin into the usb. dont formate the drive. 


Next time when you reboot your computer, press f12, then you will find your usb-device listed under +hardrive. if not, enable usb-storage and leagacy in bios.

This was taken from a win7 usb install tutorial, but do work with linux as well..

Its a shame, spent a day to figure out what was wrong with the motherboards bios, and it has probably something to do with mbr.

The motherboard is a gigabyte 990fxa-ud3.
I also needed to disable acpi with acpi=off when the liveusb booted up. (press tab to edit the options)

This is not a linux way.. sorry for that.

---

### Post by oldfred on 2012-09-08
Closed, necromancy.

Actually you have used Windows to create a Windows 7 or Vista bootable flash drive. That will not normally boot Ubuntu. The partition will try to use bootmgr to boot which is for Vista or 7.

bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

