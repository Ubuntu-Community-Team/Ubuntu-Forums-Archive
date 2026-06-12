---
title: "Windows 7 won't show up in GRUB after installing Ubuntu 14.04.2 LTS"
date: 2015-05-16
forum: Installation &amp; Upgrades
---

### Post by juri4 on 2015-05-16
Hey
I am running a Windows 7 setup and i've recently installed Ubuntu 14.04.2 64bit on my system.
I wanted to archieve a dual boot constellation with Windows 7 64bit and Ubuntu.
Both systems are installed on different SolidStateDrives.
Sadly i couldn't choose between the OS while booting (after the installation of Ubuntu)
So i tried to boot-repair by following the instructions given on this website (i've chosen recomended repair)
[https://help.ubuntu.com/community/Boot-Repair#A1st_option_%3a_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_%3a_get_a_CD_including_Boot-Repair)
As a result i was finaly confronted with the GRUB user interface and i've been able to choose between "Ubuntu" and "Advanced Ubuntu options" when booting into GRUB.
**But still Windows 7 is missing inside the Boot Dialogue.**
I already tried to update-grub. It didn't change anything.
This is my Boot Repair info file
[http://paste.ubuntu.com/11167522/](http://paste.ubuntu.com/11167522/)
Thanks for any help in advance :)

---

### Post by Vladlenin5000 on 2015-05-16
Hi and welcome.

The first thing that pops out of your boot-repair info is the sheer amount of NTFS partitions in more than one drive. Is it really intended? It's just out of curiosity, I think it's unrelated.
Assuming you installed both OSs in the same mode (applicable only to newer, UEFI based systems) - legacy - as it seems to be, then, before *update-grub* you should install Grub to the first boot device (ex: /dev/sda) with
```
sudo grub-install /dev/sdX
sudo update-grub
```

That not working, ie, not finding Windows as it should, probably means Windows wasn't properly shutdown before install Ubuntu. You should NEVER make changes to your drives (installing an OS, etc.) without a) a backup, and in case of a dual boot scenario where you had to shrink Windows partintion, b) always use Windows tools for that task and reboot twice to let it run the checkdisk.

---

### Post by Geoffrey_Arndt on 2015-05-16
Assumption:   this only applies to newer PC's (2010 & later) that have efi/uefi firmware instead of traditional BIOS.   Applicable to Windows 7 & 8 (as the Windows version is only a minor consideration).  

There's a LOT of information at this ubuntu forum and similar sites about how to successfully setup a dual boot for Ubuntu & Windows,  BUT,  a well done video is worth several thousand words.

This set of 4 instructional videos from youtube is one of the best I've seen yet . . . because it deals with the basic steps that need to be done to Windows & the UEFI firmware before install.  Need to watch all 4 videos, paying special attention to "disabling" fast boot in windows (as windows hibernation will ruin an otherwise good install).

[https://www.youtube.com/watch?v=C88g3p5l5l8](https://www.youtube.com/watch?v=C88g3p5l5l8)

ps:  this info may not help your current situation - but may help understand how/where problems may have occurred.   One other thing you might try is using a live media to run gparted and see where boot flag is at.

---

### Post by juri4 on 2015-05-17
@Vladlenin5000
 Thanks for your response.
 The vast amount of NTFS Partitions and disks are actually intentionaly created.
 Although some of them may be a result of some former windows installations (recovery and/or boot partitions)  But i am really concerned about all the partitions claiming to have "no filesystems".
  I can't really explain why they where not being detected.
 Before i've read your post, i've reinstalled Windows 7.
 Your post may have been the solution to my problem :) As you've mentioned, it seems like i've installed GRUB into the wrong disk/partition.  

@Geoffrey_Arndt 
 I tried to install ubuntu again after this odyssey. 
This time i used this Tutorial. [URL="http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/"]
http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/[/URL] 
I watched your suggested video as well, but i couldn't recreate the part when the tutor was assigning the "BIOS Bootable" Partition. 
But anyways, thank you. 
Now i can boot into Windows and Ubuntu. :)

---

