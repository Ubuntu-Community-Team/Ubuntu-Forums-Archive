---
title: "Ubuntu 14.04 does not boot in AHCI mode"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by amgeddis on 2014-11-26
Behavior:
Gateway All-in-one with Windows 8 would boot to Windows 8 with AHCI enabled but would not boot DVD.  Setting AHCI-> Native IDE in BIOS allowed the computer to boot to DVD.  Secureboot is disabled and legacy mode enabled.

After wiping the hard drive with DBAN and installing Ubuntu 14.04 and changing Native IDE-> AHCI the computer always just gives the message

> Reboot and select proper boot device
or insert boot media in selected boot device and press a key

Pressing a key just causes a duplicate of the message to appear beneath it.

Message is there regardless of if I have boot order set as HDD>DVD or DVD>HDD.  Setting boot order as DVD>HDD and rebooting with the DVD ISO loaded still just shows that screen.

It boots fine with it set to Native IDE but I would really prefer it to be set to AHCI.  The Hard Drive does show up in the BIOS options menu with AHCI enabled.

System is a Gateway ZX4250 with bios P11-A0.

Any ideas what is wrong?

If it matters it seems that the HDD is using SATA port 2 and the DVD drive is using SATA port 1.

If it could boot to Windows 8 with AHCI enabled it should be able to boot into Ubuntu with it right?

This is a machine with an underpowered CPU and from what I've read CPU usage is much higher with systems using IDE mode and lower on systems using AHCI mode so I would really prefer if this could be booted with AHCI enabled.

I've tried installing and running boot-repair but nothing changed.

Edit:

Solved.  Problem was that for some reason AHCI SATA mode only works with UEFI bios enabled.  The first time I did the installation I used a bootable DVD which would not boot in AHCI mode and hence installed with UEFI bios disabled.  I did a re-install using a bootable flash drive in AHCI mode with UEFI and that solved the problem.

---

### Post by oldfred on 2014-11-26
Post link to summary report from Boot-Repair.

Is UEFI/BIOS updated to current version from Gateway?

Perhaps their definition of legacy is IDE?
Normally Legacy is just BIOS/CSM mode, not UEFI.
And some boot in first mode found, or they look for an efi partition and boot files, if not found, look for MBR and then if not found, post error on no operating system. Others only look for system installed in mode that boot settings in UEFI/BIOS specify.

Some also require you to set a password to open up more settings in UEFI. But never ever lose that password.

---

### Post by amgeddis on 2014-11-26
> **oldfred said:**
> Post link to summary report from Boot-Repair.

Is UEFI/BIOS updated to current version from Gateway?

Perhaps their definition of legacy is IDE?
Normally Legacy is just BIOS/CSM mode, not UEFI.
And some boot in first mode found, or they look for an efi partition and boot files, if not found, look for MBR and then if not found, post error on no operating system. Others only look for system installed in mode that boot settings in UEFI/BIOS specify.

Some also require you to set a password to open up more settings in UEFI. But never ever lose that password.

Thanks for the reply this has been driving me nuts.

I wasn't clear in my first post, by legacy mode I meant CSM is enabled.  The setting is "Launch CSM Always" and I have it set to enabled.

More weirdness.  I've gone to the gateway site and when it actually works it lists the latest BIOS as P01-B1 and is dated 05/07/2012.  But the BIOS I currently have isn't even listed, P11-A0, and is dated as 09/04/2012 making it newer?

I downloaded that P01-B1 bios and made a FREEDOS bootable flash drive and this is where it gets really weird.  When I tried to boot into the flash drive with the boot order changed to "REMOVABLE DEVICES" first and it STILL set to "Native IDE" it would not boot to the flash drive and just went right back to booting Ubuntu.  I decided to go ahead and see if I could boot to the flash drive with it set to AHCI and _it worked_ but when I tried to run the flashing program from DOS by navigating to the DOS folder and running FBB it just shut down and did nothing.  I checked BIOS and it was still the same version as before but when I tried to boot to the flash drive again all I got was that message again: "Reboot and select proper boot device". 

 I decided to change the AHCI mode back to Native IDE and tried booting from the flash drive again and it worked and has been working that way since.  However, when I tried to flash the bios again from FREEDOS I got the error message:

> Update BIOS Fail!
error: problem getting flash information

I haven't tried flashing the bios again since that because now I'm super afraid of it screwing something up if I force it.

Here is the boot-repair log: [http://paste2.org/8L82NLJa](http://paste2.org/8L82NLJa)

---

### Post by oldfred on 2014-11-26
I have not seen the far from start of drive issue with any new UEFI system. 
But if in BIOS/MBR mode and you have drive set for legacy IDE  it could be an issue. The far from start of drive was for old BIOS that were IDE and drives were not over 120GB.

I might try shrinking sda1 to less than 50GB and make the rest of the drive either /home (you have to move it) or a data partition. Or reinstall with / (root) of 25GB and separate /home or data partition(s).

I also hesitate to force a BIOS update. Versions should be clear and process relatively easy to do. Otherwise you may brick system.

---

