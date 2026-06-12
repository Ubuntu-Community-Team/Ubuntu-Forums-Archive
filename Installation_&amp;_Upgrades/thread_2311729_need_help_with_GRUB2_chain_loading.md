---
title: "need help with GRUB2 chain loading"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by dmikulec on 2016-01-29
Hi! Need some help with chain loading with GRUB2. Bear with me because I wanted to give as much background as possible.

I've been using a Western Digital hard drive with 12.04 loaded. I've added a Samsung SSD with Windows, 14.04, and 15.03. Now when I boot, there is a black and white screen that flashes by so quickly I cannot read more than "WDC". After that is a faded purple screen with all the OS's listed, 14.04 on top. I can boot all os's.

I've read lots of advice and instructions on line about GRUB2 chain loading and decided to compare the GRUB files on both drives, side by side. From gedit (not gksudo gedit) I opened 30_os-prober on the 12.04 drive and got the challenge screen about executing or editing the file. Chose edit. (the Nautilus default action on 12.04 is to challenge) In the same gedit session I tried to open corresponding file on the 14.04 drive. There was no challenge and the script began executing with an error screen in gedit, then gedit crashed. Now when I look at the files  /etc/grub.d/30_ | 40_  | 41_ on 12.04, they have not been modified. When I look at the same files on the 14.04 drive, they have all been modified as of today but at a time earlier than my gedit session. (Oh, another point: I was booted last night in 12.04 and put it to sleep overnight.) 

Finally, the questions. Do I have to do anything on either drive (e.g, update-grub)? Will chain loading still work and 12.04 and 14.04 still boot? I'm on 12.04 as I write.

---

### Post by oldfred on 2016-01-29
You normally chain load to Windows as it is a different boot loader.
But for Linux now you normally do not chain load to another grub, but just directly boot from which ever version of grub is in control of boot process.

You do not edit grub.cfg but that is the file used to boot. It is created by the scripts and configuration settings for grub. I do add manual boot stanzas to 40_custom, but do not attempt to edit scripts.

I used to even add chain loads to my MBR on another drive with a totally different version of grub or to other partitions. With old grub legacy you could install grub to a partition's boot sector, but with grub2 that is highly not recommended (even thought that is how EasyBCD works).

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by dmikulec on 2016-01-29
Thanks oldfred. Considering the history I described, do I need to do anything to ensure future boot to any of the os's?

---

### Post by dmikulec on 2016-01-29
I found that everything is OK. I've over reacted.

---

