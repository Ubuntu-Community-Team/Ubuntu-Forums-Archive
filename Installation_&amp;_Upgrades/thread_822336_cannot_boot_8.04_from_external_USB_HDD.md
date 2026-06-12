---
title: "cannot boot 8.04 from external USB HDD"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by StefanS42376868 on 2008-06-08
I tried to install Ubuntu 8.04 on an external hard disk, which is connected via USB2.0.
I did this exactly in the way described in 
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)
i.e.:
- disconnect internal HDD from IDE
- boot from Ubuntu Live CD, option "install ubuntu"
- check advanced option "install boot loader" to "/dev/sda"
The installation was "succesful", i.e. no errors nor warnings were reported until "restart computer" message box.
BTW: During shut down, some  warnings were displayed (very quickly, so that I could not read them, probably because I had no internet connection during install).
During reboot I set first boot device to "USB-HDD" in my bios (Phoenix-AwardBIOS W6570MS V3.3, AMD Athlon(tm) XP1800+, MS-6570 ATX).
But the system does NOT boot from the external HDD (after a timeout it reports "INSERT BOOT DISK" error.

So I thought, this might be a problem with my BIOS (maybe the boot from USB-HDD-feature does not work), and tried in a different way as described in 
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28BootFromUSB%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28BootFromUSB%29)

I booted again from the Ubuntu live CD and started "sudo grub" in a terminal window.
I entered "root hd(1,0)" and "find /[TAB]", and the content of the USB Drive (with some UBUNTU folders) is displayed, so the drive appears to have been formatted and installed correctly.
BTW: In addition I checked with the Ubuntu-Partitioner-program if the "boot" flag has been set in this drive, and yes, it is!
BUT: On entering "chainloader +1", I got the error message "Invalid or unsupported executable format".
BTW: There is also no "ldlinux.sys" on the USB-HDD like in the example, is this already an error?

So I have no more idea how to proceed!
Can anybody help me? Thanks a lot in advance!

---

### Post by quill3033 on 2008-07-03
hi, did you end up solving this problem?

I have now been able to boot from my external usb hdd using the original instructions in pendrive but when I take the usb drive to another computer (tried it on someone else's computer - this person has a different apparently more modern bios than mine- it doesn't work even though it is in the boot menu as a possible selection it goes nowhere) 
so it works on my computer but so far noone else's. I'm travelling soon and would like to be able to plug the external drive into other pc's and show friends how linux works... 
I'm thinking of installing the master boot record on the external drive and testing it again on my friends' computers...

---

### Post by Pumalite on 2008-07-03
First of all; make sure your BIOS allows booting from USB. Second: find out your USB /dev by running:
sudo fdisk -lu
Then get your USB menu.lst
gksudo gedit ???
Make 'groot' and 'root' (hd0,0)
Save and exit.
Boot your USB

---

### Post by StefanS42376868 on 2008-07-04
I could not solve the problem, although my bios should definitely be able to boot from USB devices (there is an option which I selected).

Meanwhile I bought a second internal HDD and installed Ubuntu there, that worked immediately.

> **quill3033 said:**
> hi, did you end up solving this problem?

I have now been able to boot from my external usb hdd using the original instructions in pendrive but when I take the usb drive to another computer (tried it on someone else's computer - this person has a different apparently more modern bios than mine- it doesn't work even though it is in the boot menu as a possible selection it goes nowhere) 
so it works on my computer but so far noone else's. I'm travelling soon and would like to be able to plug the external drive into other pc's and show friends how linux works... 
I'm thinking of installing the master boot record on the external drive and testing it again on my friends' computers...

---

