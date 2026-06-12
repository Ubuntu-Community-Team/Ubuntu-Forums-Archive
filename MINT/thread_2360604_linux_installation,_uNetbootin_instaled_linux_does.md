---
title: "linux installation, uNetbootin instaled linux does not work, iso installation does no"
date: 2017-05-06
forum: MINT
---

### Post by statkute on 2017-05-06
The only software which works is Boot-Repair-Disk, which produce a message what
 =================== Suggested repair
The default repair of the Boot-Repair utility would not act on the boot.
=================== User settings
The settings chosen by the user will not act on the boot.


I have tried to use uNetbootin to install Linux mint from terminal - it worked, but after the installation, i was not offered to enter Linux os, i faced the message: "Reboot and Select proper boot device or Insert Boot Media and select Boot device and press a key".

How i should proceed. Is there a way to format the ssd disk totally, create partitions and install linux/windows?

The problems are:
  1) that windows 8, and Linux Mint 17 fresh iso disks does not boot.  Instead there is the message : "Reboot and Select proper boot device or  Insert Boot Media and select Boot device and press a key".
  2) the only software which boots is ubuntu Boot-repair-disk, which sayd he can not resolve problems.
  3) Using ubuntu boot-repair-disk i can install uNetbiotin and then  linux, but the linux does not appear after the computer reboot, i see  the message "Reboot and Select proper boot device or Insert Boot Media  and select Boot device and press a key" instead of screen offering to  enter the Linux.




***** below is the story from the beginning:

I have had a Grub, Linux Mint 14 and Win10.
After windows 10 update, there was an error with grub2:
error: no such partition.


I have tried online solutions, like 
[http://www.legendiary.at/2016/01/04/windows-10-update-changes-partition-table-and-breaks-grub/](http://www.legendiary.at/2016/01/04/windows-10-update-changes-partition-table-and-breaks-grub/)
but oculd not find any partition with /grub2 directory.

Then ,i decided to back-up data before trying any tool to fix grub. Looking to the disk i found that does not exists my username folder, with all documents, images and downloads, where i kept all my files. Additionally, the Program files forlders did not contain any programs i was using, mostly i wanted to bak-up mozilla-firefox. The only folder i could back-up was Bitnami wampstack. This is wierd, because usually if smth happens, the User folder, and Programms in Program folder exists and it is possible ot back-up the data.

When i put the disk back, there were no anymore grub2 error. There was an error  "Reboot and Select proper boot device or Insert Boot Media and select Boot device and press a key". 
My first boot option is CD, but nor Ubuntu iso , nor windows iso did not work, they did not start installation. The only software which was workign was Boot-Repair-Disk from Ubuntu, which terminal i used to instal uNetbootin and then Linux mint. Linux mint were intalled successfully, but after rebooting computer, they did not show up. 

How i should proceed. Is there a way to format the ssd disk totally, create partitions and install linux/windows?

---

### Post by howefield on 2017-05-06
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2017-05-06
> I have tried to use uNetbootin to install Linux mint from terminal

Unetbootin is used to create a bootable flash drive from which you can boot and then install Mint or some other Linux distribution.
You can also do a frugal install which basically puts the Mint (or other Linux) on the hard drive as an iso and you should have an entry in the boot menu named unetbootin.  Selecting that will get you to the system unetbootin created and you can then install from there.  Unetbootin doesn't install Mint or any Linux.  Which option did you use?

If you are being told to reboot and select a proper boot device, do you have a bootable CD/DVD in the drive when you reboot and the CD/DVD drive set to first boot priority in the BIOS?

---

