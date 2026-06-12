---
title: "Install cd-rom couldn't be mounted"
date: 2004-12-09
forum: Installation &amp; Upgrades
---

### Post by nuttymango on 2004-12-09
Help! I'm excited about trying Ubuntu on my old eMachines Celeron 433 Mhz machine with an ATAPI CD-ROM. If I remember correctily this is different than the new IDE CD-ROMs. Or am I mistaken?

Anyway, I can' get past this error message during the hardware detection phase: "Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can try it again."

Trying again results in the same error message and searching these forums for the error message hasn't yielded any hits. Do I maybe need a boot floppy with an ATAPI driver? If so, how do I make one?

---

### Post by ayam on 2004-12-11
Is this during the 2nd stage of your installation? My recommendation is to pick YES to copying the remaining Ubuntu software to your harddrive. Ubuntu does did not detect my CD-ROM drives correctly during installation. It also was not detected correctly after my installation and I had to make some changes. Copying remaining Ubuntu software to the harddrive will at least take you to the end of installation. Try putting a CD into your CD-ROM drive and see if loads up. 

Double Click on Computer => Disks => CD-ROM [Icon] as well to double check. If that doesnt work you need to make changes as listed below



**Check where your CD-ROM drive is located**
1) Open Terminal and type _dmesg_ If there is an error try _sudo dmesg_

2) Scroll up and down and slowly look for information about yoru CD-ROM drive. My computer says

*Attached scsi CD-ROM sr0 at scsi1, channel 0, id 3, lun 0*


The thing I am interested in is the **sr0** 
Your CD-ROM drive is most likely hda, hdb, hdc or hdd


** Telling your computer of the changes **


1) First open terminal

2) We need to edit  the file fstab whihc is located in the /etc directory so we type 

_sudo gedit /etc/fstab_


3) Next find the line that has something about cd-rom

4) in the /dev section of the line it would prbably say /dev/hdX where X is a letter of the alphabet. It could also say /dev/cdrom but it doesnt matter you want to change /dev/<blah blah blah> where <blah blah blah> is where our cd-rom drive is located
according to dmesg

Now insert a CD and see how it goes

---

### Post by nuttymango on 2004-12-11
Thanks so much for replying. Sadly, I can't get past the first stage. I accept default English, then American English, then I get the error message: "Installation CD-ROM could not be mounted." Etc. 

So I can't get to a command line. I tried to run a Knoppix CD and it started to run then said Knoppix filesystem could not be found. So It seems like neither of these two CDs (Warty and Knoppix) had the correct driver for my old (eMachines Celeron 433Mhz with 32 MB RAM and a 4.2 GB HD) computer.

I tried a DSL CD (Damn Small Linux, includes Window Manager + Apps in 50 MB) and it ran fine. 

I just had an idea. Maybe the 32 MB of RAM in this machine is keeping the installation program from loading? Maybe DSL loaded properly because it's so small? Hmmm.

Anyway, thanks again.

---

