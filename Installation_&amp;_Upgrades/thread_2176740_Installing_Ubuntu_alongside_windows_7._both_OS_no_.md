---
title: "Installing Ubuntu alongside windows 7. both OS no longer work (bootinfoscript)"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by thomas_wood2 on 2013-09-25
Hi all,

This is my first experience with ubuntu and linux in general. 
I am installing ubuntu so that i may use 'octave' as, i need it for my intro to programming course.
Yesterday I had ubuntu functioning properly and was able to switch between it and windows seemlessly upon rebooting my system. This morning though, ubuntu failed to load. no error messages, no nothing, just two completely blank, black screens in front of me. frustrated by this and well aware of the impending deadline for the course, i attempted to get it working again. all my atempts so far have failed. Now my windows 7 won't boot either.

I've formatted the HDD I want to use as the boot drive for ubuntu and tried  to load ubuntu again (in excess of 5 times), while leaving my windows 7 boot SSD untouched for fear of loosing irreplacable data, and continually get one of the following errors:

ERROR: no such device (name of my boot drive)
grub rescue >

ERROR: invalid arch idependant ELF magic
grub rescue >

I realise that this is probably a partition related problem and want to know if it is posible to fix it without loosing everything and if so, how?

Any help or feedback would be epic!

---

### Post by Bashing-om on 2013-09-25
thomas_wood2; Hi !

Regretful that you are having these difficulties. Not to add to your woes, but.
The output you provided is the actual program to generate the "boot info" .. Please (re)read the instructions for executing the script and ask here if additional guidance is required.

[INDENT]My bit to help
[/INDENT]

---

### Post by thomas_wood2 on 2013-09-25
Thanks for that, Bashing-om.

i ran boot info and was given the url:
[http://paste.ubuntu.com/6156873/](http://paste.ubuntu.com/6156873/)

Cheers again,
thomas_wood2

---

### Post by oldfred on 2013-09-25
I am not sure what the errors Boot-Repair is showing are.

I would try using the repair, but not auto repair. Uncheck auto repair and check update MBR. Then in advanced options choose to put the Windows type boot loader in sda and then reinstall grub2 to sdc. Then set BIOS to boot sdc.

Often the ELF error is related to incompatible versions of grub. Or you may have an older grub in the MBR of sda and changed to boot from that? Or sda was old default an some updates reinstalled to it but you  are booting from sdc.

If you get back into system, run these:
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Bashing-om on 2013-09-25
thomas_wood2; Hey,
Due to the expediency of your situation I will try and help. I am not conversant with Windows !
Nor am I the sharpest tack in this box of sharp tacks (the forum).
First I do see some problems .
a)Unknown BootLoader on sdc2 -> data disk so may have no impact;
b)ls: cannot access /home/usr/.config: No such file or directory -> maybe ouch .. I am not on standard install ATT and can not check;
c)Windows not detected by os-prober on sda2. OUCH !
d)Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
line #748 (again) Partition outside the disk detected. -> speaks for itself .. not good !

OK, looks like there is a booting set up for ubuntu on the SDC drive.
In bios set the boot priority to boot from that 3rd hard drive, and if the file system (see item b) is intact ... should boot into ubuntu.

Please try that and advise asap for additional guidance.

[INDENT][INDENT]I hope you can
[/INDENT][/INDENT]

---

