---
title: "Ubuntu server installation - grub observation"
date: 2024-03-11
forum: Installation &amp; Upgrades
---

### Post by 1960webhosting on 2024-03-11
Dear sirs,

I made the following observation with my installation, and I would like to clarify if it Ubuntu-Server and grub is working correctly, or else, what am I doing wrongly.

**scene-1: **
- installed windows-10 on partition#1 of HD#1
- installed Ubuntu desktop on partition#2 (used remaining freespace of HD#1)
summary: dual boot of WIndows-10 and Ubuntu desktop runs ok, I can select either-OS via grub.

**scene-2:** 
- installed windows-10 on partition#1 of HD#1
- installed Ubuntu desktop on partition#2 (used remaining freespace of HD#1)
- installed Ubuntu-server on partition#1 of HD#2

summary: on server reboot, I observed that Ubuntu-server wasn't added to grub. 
I still get the same grub list in scene-1(windows-10 and ubuntu-desktop)
After some troubleshooting, I observed that if I selected HD#2 from BIOS as my default boot device, I get the full grub(with the 3-OSs listed)

**scene-3**
- installed windows-10 on partition#1 of HD#1
- installed Ubuntu-server on partition#1 of HD#2
summary: on server reboot, I dont get any grub menu, server boots directly into HD#1(Windows-10)
I did another reboot and selected HD#2 manually as boot device, I get a grub menu with 2-OSs, Windows-10 and Ubuntu-server

question: Is my Ubuntu-server working correctly, as in does grub always force default onto the HD where it is installed?

how do I get the grub-list for my 3-installs to be listed if HD#1 is my default boot-device.

Unlike Ubuntu-desktop, there is no option during installation of Ubuntu server where I want grub to be installed to.


regards
1960web

---

### Post by MAFoElffen on 2024-03-11
Sort of yes and no, right?

Different partitioner, but look the the attachment screenshot of when you go into the manual partitioner and go to edit/look at an existing EFI partition...

Yes, it doesn't let you edit/change it, but it does identify which is the UEFI boot partition that it is working with. I can tell you that DEV Noble Server is still the same there.

Understanding how the installers work, and how intricate my own system is with what is installed already, if I am installing something that involves a boot loader... I often disconnect the non-related other drives, so only the drives "I want involved are present. That prevents many surprises.

My questions and curiosity involves trying to figure out what your plan is:
[LIST=1]
[*]Why are you installing Ubuntu Server as a dual boot?
[*]Why are you installing multiple versions of Ubuntu Server?
[*]If so (all the possibilities that come to mind), why not as VM Guests instead of as a dual boot?
[/LIST]

---

### Post by yancek on 2024-03-11
You neglected to indicate whether your installs were UEFI or Legacy installs.  Seems like pretty standard behavior.  

> summary: on server reboot, I observed that Ubuntu-server wasn't added to grub.  

You indicate that when you reboot, apparently to the Ubuntu desktop, you see the Ubuntu desktop and windows menu.  Did you first update Grub from the Desktop?  If not, there would be no way for the bootloader to be aware of the install on another drive?

Could you clarify something, do you still have the Ubuntu desktop install on the first hard drive?  If these are UEFI installs, the Ubuntu installer may have overwritten the Ubuntu files for the Desktop install.  You could try updating grub while booted into the server and see if the Ubuntu desktop is added.  If not, check the /etc/default/grub file to make sure that os-prober is not disabled.

> does grub always force default onto the HD where it is installed? 

No, particularly with UEFI installs on a dual boot with an already existing EFI partition.

[QUOTEhow do I get the grub-list for my 3-installs to be listed if HD#1 is my default boot-device.
] [/QUOTE]

You would need to take a look at the EFI partition(s) and contents.  Which drive has an EFI partition?  Both, only one?  Look on the EFI partition in the ubuntu directory for a grub.cfg file and check the UUID in that file and compare it to the output of the blkid command to find which partition it is pointing to.

---

### Post by ActionParsnip on 2024-03-11
Why dual boot Ubuntu Server? While the other OSes are booted, the Ubuntu Server service will not be available....

---

### Post by MAFoElffen on 2024-03-11
NOTE: He never mentioned "Ubuntu Desktop. Only "Ubuntu Server".

> **ActionParsnip said:**
> Why dual boot Ubuntu Server? While the other OSes are booted, the Ubuntu Server service will not be available....
That was my question also... Server Services (of any platform) are only available if it is running. 

Then why 2 instances of the same version of Server? If he wants to learn and play, or if mulitple versions, then why not installed as VM Guests, where he could have access to all and have all running at the same time?

---

### Post by oldfred on 2024-03-11
Different versions of Ubuntu use different installers.
Ubuntu though 22.04 & flavors (except Lubuntu) though 22.04 used Ubiquity installer.
That has this bug for multiple drive installs or external drives, where you may not want boot files on first drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Lubuntu and Kubuntu starting in 24.04 use Calamares installer.

Server & newer desktops use uses subiquity & flutter for gui for installer.
That supposed has fixed Ubiquity bug.

All installs must be in UEFI mode and should be on gpt partitioned drives.
But you only get one Ubuntu entry in UEFI and one default grub which will boot all installs, if updated after any additional installs.
You can create an ESP on every drive and have different boot loaders in each drive. But they all may say "ubuntu".

---

### Post by yancek on 2024-03-11
> NOTE: He never mentioned "Ubuntu Desktop. Only "Ubuntu Server".
 

Yes s/he did as it is indicated in the first and only post that Ubuntu Desktop was installed on partition 2 in both 'scene-1' and 'scene-2'.

---

### Post by grahammechanical on 2024-03-11
Regarding scene 2 - Ubuntu desktop does not know about Ubuntu server on partition #1 of HDD #2. 
Solution: Load into Ubuntu desktop and in a terminal run

```
sudo update-grub
```

Watch the printout and you will notice that 3 OS are being detected. 

> After some troubleshooting, I observed that if I selected HD#2 from BIOS  as my default boot device, I get the full grub(with the 3-OSs listed)

When you installed Ubuntu server it installed Grub in partition #1 of HHD #2. That is what it was supposed to do. As Grub was being installed on partition #1 on HDD #2 it detected the other 2 OS on HDD #1 and listed them in its own particular Grub menu.

If Ubuntu desktop gets an update to the Linux kernel Grub will be updated so that Ubuntu desktop will load on that new kernel. Ubuntu server will not know that there is a new kernel in Ubuntu desktop unless you load Ubuntu server and run the update-grub command.

Likewise, when Ubuntu server gets a new Linux kernel Grub menu in Ubuntu server will be updated but the Grub menu in Ubuntu desktop will not load the new kernel when you select Ubuntu Server. Load Ubuntu desktop and run the update-grub command.

We have to use this procedure when we multi boot two or more Linux distributions.

What happens when Windows 10 updates and you do not get a Grub menu? You can at least use the UEFI/BIOS to load the OS on HHD #2 and you should get a Grub menu with the option to load either Ubuntu server or Desktop.

Regards

---

### Post by 1960webhosting on 2024-03-13
Dear all,

thanks for the many responses.

I wiped both HDisks and sorted things out like this:
scene4:
a) installed windows-10 on partition#1 of HD#1
b) installed Ubuntu-server on partition#1 of HD#2
c) installed Ubuntu desktop on partition#2 of HD#1 (used remaining freespace of HD#1)

I followed the above a,b,c then I got grub correctly listing the 3-OSs on HD#1

To provide some answers to your clarifications:
@MafoElffen: I have a laptop and a desktop(which I use as my server) and with which I play around. I prefer to have 1-OS at a time.

@yancek,
its MBR not UEFI
$ sudo fdisk -l /dev/sda | grep Disklabel 
Disklabel type: dos 

when next I wipe the HDs, I try to update-grub

@ActionParsnip
Yes, I just want 1-OS at a time

@oldfred
Im using Ubuntu-20. 
Thanks for your comments. Next time, I'll try the installs with UEFI mode

@grahammechanical
thanks

regards
1960webhosting

---

### Post by oldfred on 2024-03-13
I do not recommend old, very old MBR(msdos). Use gpt.

I started converting new or totally reformatted drives to gpt in 2010 with my BIOS boot system.
Ubuntu will use gpt for either old BIOS or UEFI, but UEFI strongly suggests using gpt.
Microsoft requires gpt for UEFI install and requires msdos for BIOS install.

Ubuntu will let you install in UEFI mode to MBR(msdos) drive, but probably should not. But that is probably as conversion to gpt totally erases a drive and if drive has NTFS partitions on MBR, user may want to save those.

Since conversion from MBR to gpt totally erases a drive, be sure to have good backups.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

