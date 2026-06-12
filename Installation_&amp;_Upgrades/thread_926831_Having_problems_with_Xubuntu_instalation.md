---
title: "Having problems with Xubuntu instalation"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Teh_Messiah on 2008-09-22
Hi, i am trying to build a file server and have an old system:
[MS-6390]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=307&maincat_no=1&cat2_no=&cat3_no=") mobo,
AMD Athlon XP 2200+ 1.8 ghz cpu,
ATi 9550 with 256mb,
SiI3114 SATA raid controller with 4x Samsung 250gb SATAs,
IDE Maxtor 40gb primary HDD,
512mb Ram.

I am having alot of troubles installing Xubuntu onto this system. 

I followed the install instructions from the Xubuntu website and it refused to go to the grub boot loader, it would continually go to windows XP instead.

I tried completely deleting windows and only install Xubuntu and once installed i got a bad MBR error and nothing would start.

I then realised that as soon as i clicked the <install link> on the cd menu i would get about 10 lines of:
(numbers) I/O error on device sda1 (more numbers)

After realising that i had the "Alternative" install disk i downloaded the xubuntu-8.04.1-desktop-i386.iso and burnt it to disk.

This installed alot better and i didn't get the "I/O error on device sda1", however after instal i still got the MBR error and nothing would start.

I have just completed the reinstal of windows XP on the other half of the HDD and also just completed reinstalling Xubuntu (for about the 6th time in the last 36 hours) and still it refused to load the boot loader GRUB.

I have never used any linux/unix based OS before and was sick of MS Windows and wanted to try something new, as well as it was sugested that i use a linux based system for security of my file server.

1. Please help?
2. What am i doing wrong?
3. Are there special bios settings i need to allow Xubuntu to boot?
4. Is there something special i am meant to do during install (like sticking my tongue out :P)

At least with the Desktop version i can now load the live cd and i liked what i saw but still it refuses to load on start up.

Edit. 
After instalation has completed and it promts me to remove the disk before restarting the machine there is some errors on screen that disappear before i can read them, something about bus but thats all i could catch before it restarted.

After restart it does the DHCP thing,
then, 

PXE-E53: No boot filename received 

PXE-M0F:Exiting PXE ROM.
Invalid partition table

---

### Post by Teh_Messiah on 2008-09-22
I have to admit, despite the fact that many people have told me how much better this is meant to be than any windows OS this is really starting to annoy me. 

At least windows will install and work despite it's many flaws.

Xubuntu-desktop installs but wont boot from the hard drive.
I can only get it to boot from the Live-cd.
Everytime i boot up it says there is an invalid partition table.

I am currently reinstalling windows XP....... again for the 3rd or 4th in 2 days, since Xubuntu wont run from the hard drive.

I have partitioned the 40Gb Maxtor in half so i can install Xubuntu on the other half and hopefully rectify the problems once i have received some help here. 

I tried running the command: 
"sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map"
and it said that it couldn't find the directory. i then tried to install the grub software but gave the same result on reboot,
"Invalid partition table" :confused:

Please save me from insanity and the never ending abuse of windows....!

---

### Post by Teh_Messiah on 2008-09-22
OK,

I seem to have got GRUB to instal and work, hopwever none of the operating systems want to load, not even windows.

I now get 

for 
"Ubuntu 8.04.1, kernel 2.6.24-19-generic"
"Error 21: Selected disk does not exist"

for 
"Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)"
"Error 21: Selected disk does not exist"

for 
"Ubuntu 8.04.1, memtest86+"
"Error 21: Selected disk does not exist"

for
"Other operating systems:" (i have no others installed)
"Error 11: Unrecognized device string"

for "Microsoft winXP"
"Error 21: Selected disk does not exist"

---

### Post by Teh_Messiah on 2008-09-23
Never mind, I took the computer to college and the lecturer suggested disconnecting the power from the raid set and we re-installed Xubuntu there and it worked fine!

It was obviously conflicting with the raid controller and the 4 hard drives on it.

anyone else who has a PCI raid controller should know this too incase they don't already.

---

