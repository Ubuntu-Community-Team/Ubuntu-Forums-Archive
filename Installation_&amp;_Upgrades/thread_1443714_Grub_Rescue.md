---
title: "Grub Rescue"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Ignorance Isnt Bliss on 2010-03-31
Hello Can anyone help an imbacile correct the problems he has caused with his wifes computer?
 
The sequence of my incompetant actions have been
 
1st to try to load Ubuntu 9.10 on her windows XP home machine as a dual boot system. This all seemed to have gone well being abable to run Ubuntu after the installation and also being able to re boot into windows. The problems started when I tried to reboot Ubuntu. I got a log in screen with a vastly over sized font which wouldn't allow me to log in and an error message which told me power options hadn't been installed properly.
 
At this stage I was still able to reboot windows and a live cd version of Ubuntu.
 
After consulting many threads on getting rid of my partition to enable me to to reinstall ubuntu I reolved to back my ignorant understanding of computing and I delete two partitions in windows computer manager.
 
I expected to get the grub boot menu back and then be able to use windows or reinstall ubuntu over writting the now vacant partitions left by my earlier action.
 
I also expected that at worst I would be able to reload windows or Ubuntu froma disc.
 
Needless to say that isn't what happened.
 
Now when try to boot from a disc it says no bootable device found.
 
When I try to boot from the hard drive I get the following message/prompt
 
GRUB Loading
error: no such partition
grub resue>
 
 
I have tried using a few of the comands I have picked up from other threads and none of the commands seem to be recognised like fdisk -1 or sudo
 
Just make life a little harder although I have a ubuntu disc and a windows xp disc I am not sure of the administrator passwords I guess the ubuntu password will be the same as the user password I used when I set it up but the chances of my wife remembering the XP one is slim! 
 
Any help would be appreciated but it will need to be aimed at a fairly low competancy level as you may have noticed from the above sequence of events!:confused:

---

### Post by ajgreeny on 2010-03-31
I think you either need to reinstall ubuntu and hope that this time the screen resolution is better, or you need to restore the windows MBR, for now at least, which you can do with the Windows XP disk and recovery module - fixmbr.

Alternately get a copy of supergrub, which will let you do almost anything regarding booting an OS, and will certainly allow you to restore the windows MBR. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Ignorance Isnt Bliss on 2010-04-02
Thank you  AJGreeny 
 
Super grub has allowed me to delete Grub and log into windows again. I'll have another go at installing Ubuntu and hopefully the initial problem won't occur again

---

