---
title: "Ubuntu doesn't detect hard drives"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by pickslide03 on 2013-02-18
Hey, I've searched all over for this problem and so far everything I've come across and tried hasn't helped at all. 

I'm trying to dual boot Windows8 and Ubuntu but when I attempt to install Ubuntu either with USB and with a CD none of my hard drives show up. I have a F1A55-M LX Plus motherboard with 3 hard drives plugged into 3 of the lower 4 SATA ports and my optical drive plugged into one of the two separate SATA ports. As far as I know all of my SATA ports are SATA3G none are 2G. Currently they are all in IDE mode but I've tried in AHCI mode as well and it's the same problem. The only way I've gotten a hard drive to show up in the installation is by moving it from one of the lower 4 SATA ports to the upper SATA port along with the DVD drive. I've tried plugging the DVD drive into the remaining empty lower port along with all of my hard drives and the CD won't boot that way.

If anyone has any idea why this would be happening and a suggestion for a fix, please let me know.

---

### Post by darkod on 2013-02-18
If you boot the cd in live mode and open Gparted for example, does it see the disks?

In terminal if you run:
sudo parted -l (small L)

can it see them?

One reason for the installer to ignore disks is if they have been used in raid earlier, they still have meta data remains. In that case Gparted and parted can see them, only the installer ignores them thinking they are members of raid array.

If Gparted/parted also don't see them, it seems ubuntu can't recognize the controller for those 4 ports. You said the DVD also doesn't work in those ports, so this might not be only ubuntu problem.

---

### Post by pickslide03 on 2013-02-18
Gparted doesn't see them and sudo fdisk-l doesn't see them either

---

### Post by darkod on 2013-02-18
Then it's a hardware issue. Maybe a driver for that specific chipset, some option in the bios, etc.

Try setting the sata mode in AHCI, it should usually be AHCI, although if you installed windows while it was IDE, it will not boot if you change it now. Ubuntu can handle that change after the OS is already installed, windows not. There seem to be ways to do it touching the registry, but by default it stops booting if you change the sata mode now.

I don't know what to say, you will have to google around and investigate if your board/chipset has issues with ubuntu.

---

### Post by pickslide03 on 2013-02-18
If it helps to clarify the problem I'm having, I tried putting the DVD drive on the bottom set of 4 SATA plugs and I get the following error both in AHCI and IDE trying it both standard and UEFI

BusyBox V1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

---

### Post by oldfred on 2013-02-20
Some have reported these as issues with some Asus systems, not sure if your model or not.

       Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
    
Was Windows pre-installed? Then you have secure boot issues also.

---

