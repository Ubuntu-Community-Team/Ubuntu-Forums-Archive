---
title: "Grub2 Will not load after Install of Ubuntu Server 12.04 LTS on Raid 0"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by wGT7XAr on 2013-08-22
So I finally decided to break down an join the forums. Mostly because this issue may be way beyond my understanding at this current time. 

I'll give a quick bullet list here about what the hardware is that i'm working with, and as well what i've attempted so far to solve the problem.


[LIST]
[*]HP Proliant DL380 G4 Server. 6 HD's  2 Raid-0 Arrays(4hd's in1, 2hd's in1) Setup within the HP Smart Array 6i Controller 149GB available in Each Array
[*]Array drivers are cciss, The drives are identified as '/dev/cciss/c0d0' and '/dev/cciss/c0d1' during the installation process
[*]ext4 setup as root partition on /dev/cciss/c0d0p1, set as bootable
[*]swap setup /dev/cciss/c0d0p5, *i'm guessing because this is placed near the end of the disk*
[*]Using Ubuntu 12.04 LTS amd64 on DVD as installation media
[/LIST]


Everything goes as normal during loading of the installer. No issues during any of the install, no error messages of any sort.
The system reboots, and i'm left with a prompt telling me that it's attempting to boot off of C: and just hangs. *of course I have removed my installation media when I was prompted to*

No Grub Prompt or Grub failure message, nothing, Just sits there. Super.

So I say to myself. Grub isn't being recognized. Grub was chosen to be installed to the MBR of /dev/cciss/c0d0, no error message generated during normal and even expert install modes.

At this point, I decided to reboot the system into Rescue Mode. Re-install grub manually via command line. Spent a good chunk of the last two days reading pretty much anything I can that about grub and installation of it that I can find on the internet. I haven't had much success. Its as though grub cannot be properly written to the MBR for this system it seems like.

I do know the person whom I have obtained this server from it was in working condition, previously running CentOS.(version unknown) To my understanding it had no trouble trying to install grub(unknown if it was legacy or 2) and booted with no issues. He also had issues trying to install other flavors of Linux, CentOS was the only one he found that worked.

I'm running out of ideas to try and pin-point what is causing the problem. I'm pretty sure i'm on the right track, I just don't know what steps to take from here. I've looked up many articles about HP Smart Array installs, with many other users reporting the same types of problems of the system not being able to be bootable. 

I can provide the grub.cfg if determined it needs to be seen or any other part of the configuration. I can still read and write to the ext4 partition and access it from rescue mode.

---

### Post by oldfred on 2013-08-22
I do not know RAID, but with RAID you do not install grub to MBR but to root of the RAID.

Boot-Repair often works on RAID systems, but sometimes has issues knowing RAID from LVM as both may use /mapper. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

