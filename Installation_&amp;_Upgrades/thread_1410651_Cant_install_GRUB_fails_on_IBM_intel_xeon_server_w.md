---
title: "Cant install GRUB fails on IBM intel xeon server with scsiraid"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by gareth40 on 2010-02-19
Im trying to install ubuntu on an IBM server with intel xeon processor and scsi raid, the server was previously running MS Win Server 2003 (I never use that MS rubbush just crashes 20 times a day) anyway problem is when it comes to installing the GRUB bootloader, it just failes and keeps reverting back to the install menu, I tried several times to install GRUB but failed each time.  Anyway I can get around this? im not experienced too much with this, so wouldnt know what could be causing it, im assuming its possible the boot record is somehow write protected?  Ubuntu doesnt support intel Xeon processors? I have tried both the i386 and amd64 install ISO's of Ubuntu server without success, any help would be appreciated.

Im currently running Ubuntu server amd64 on an old amd machine and is running very stable unlike windows which used to be on the same machine

---

### Post by gareth40 on 2010-02-19
anyone?

it would be much appreciated if someone could help

The server model im trying to install on is: MT-M 8648-5BM, and its an IBM server with scsi hdd's setup as raid mirroring.

Im now assuming I need some kind of raid drivers to load with Ubuntu, is this correct?

Can someone please help me, I will pay $ to someone to help me get this thing up and running, if thats what it takes to get help on here.

I do not have very much experience on this

---

### Post by darkod on 2010-02-19
It doesn't take $ but because of time zones etc, it might take some time until the "right" person sees this. I know it looks long when waiting, but be little patient.

I don't know anything about server install otherwise I would be glad to help. But you probably know more than me. :)

I'll try to dig out something meanwhile.

---

### Post by gareth40 on 2010-02-19
thanks darkod
I managed to get ubuntu server to install by selecting NO when it found a serial ata raid controller during the initial part of setup shortly after auto dhcp.

Only trouble is it detected both hdd's as primary and secondary, not as one mirror, hence only installed ubuntu to one drive, the other remains unused as a second drive, thats no good I need them setup as raid mirroring.

I have been to the IBM support website and downloaded the servraid arcconf linux config utility but cant get it to run, i get the following error:

"error while loading shared libraries libstdc++.so.5"

I have tried the following:

"sudo apt-get install libstdc++5"

but get the following error:

E: Package libstdc++5 has no installation candidate

---

### Post by darkod on 2010-02-19
Because you obviously don't plan to dual boot a server OS, would you consider Software RAID? You disable your hardware raid, leave the disks as two separate, make mirror partitions on them (if you plan to use LVM no need for this, it can be one large partition), and the OS is creating the RAID1 on a software level.

People have reported better performance compared to fakeraid, but I don't know about proper hardware raid.

Also, if planning to use LVM then you do need separate /boot partition outside the LVM/RAID.

---

### Post by darkod on 2010-02-19
If you decide to go the software raid + lvm way, this has a step by step:
[http://forums.techarena.in/guides-tutorials/1204944.htm](http://forums.techarena.in/guides-tutorials/1204944.htm)

---

### Post by gareth40 on 2010-02-21
thanks, I decided to go with software raid, I disabled raid in bios and then installed software raid with manual partitioning, working no problems so far.

---

### Post by ivikas on 2010-08-09
Hello,
       I have an IBM X3400 M2  Server.Sorry i don't know about raid.This server has hardware suport for raid.All i did is installed Ubuntu 10.04 LTS Server i386 Version and the installation went smoothly.I was on a commandline,from here i installed the updates and then the ubuntu desktop GNOME.Then i searched in synaptic for IBM,some package came up that did say about drivers or IBM compatible bootloader(i don't exactly remember).My requirements was a LAMP Server and it's up and running Fine.The partition scheme used was LVM.

                     As i told i knew nothing of raid,i called the ibm support people and asked them to set up the hardware raid,which they came and setup.I heared that harware raid is betten than software raid because the mirroring work will be done by the hardware without much processing load  that require on the software raid.(Please correct if iam wrong)

And about grub failing to install.I had a PC that  already had  Ubuntu 8.04 installed.I tried three times to install the ubuntu 10.04 LTS Desktop,but the [COLOR="Red"]grub fails to install[/COLOR].Then i just remembered that the in Ubuntu 10.04 LTS grub has an new version(like grub  2.0 or so (not too sure but definitely new version of grub than on Ubuntu 8.04 LTS.)So MBR has  old version of grub and this is preventing the installation of 10.04 LTS Grub.I had windows 7 Ultimate  as dual boot with ubuntu.All i did is downloaded MBRfix.exe and from windows run this program which put windows 7 loader into the MBR,removing ubuntu 8.04 LTS Grub from MBR(MASTER BOOT RECORD).Then i installed the Ubuntu 10.04 LTS Desktop and the grub installation went smoothly including the GRUB.

Please have a check with supported ubuntu hardwares that will show if your IBM server is supported or not.Anyway my machine is not in the list,still rocking...

Regards
Vikas Mohan

---

