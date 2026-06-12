---
title: "New 7.10 Install Now XP won't boot"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by thisishard on 2007-12-02
I installed 7.10 today on my Win XP (NTFS) computer and now XP won't boot. It won't boot with my "Last Known Good Configuration" or in either of the "Safe Modes."

I get this error message on a blue screen while booting: "A problem has been detected and windows has been shutdown to prevent damage to your computer"  It flashed on/off quickly enough that I had to use a camera to figure out what it said. 

My first install of Ubuntu wouldn't boot (Grub Error 18).  I had installed 7.10  above 137G and my bios couldn't boot it.  I used the Partition Editor to create a small /boot partition at the beginning of the drive and then I re-installed Ubuntu.  This allowed me to boot Ubuntu successfully.  

I'm not sure where I lost my Win XP boot in this process.

I do have my Win XP / system recovery disks ... I really don't want to do a system recovery.

All my critical data is on my backup hard drive.

How can I get Win XP to boot?  Where can I go from here?

Thanks!

---

### Post by curtis1552 on 2007-12-02
Sadly for you it dosn't seem like the problem is based in the actual bootrecord or in GRUB.
If you get the prompt for safe/normal/etc it meas that windows has started to boot, but the problem  is with windows itself. You will probably have to do a reinstall - try to run the repair off the CD before you do a complete reinstall.

---

### Post by Multi-Booter on 2007-12-02
Yes... it sounds like a windows problem to me.

I would say that if anything other that windows itself is to blame... it's likely the partition editor you used. 

What I mean is that it could be that some critical windows stuff other than the bootloader was present in the area where you created the partition. 

I am very good at repairing windows... but without it in front of me I can't devise much of a course of action other than repairing... which will in turn make your linux unable to boot.

That is to say... understand that both systems 'assume control' over the master boot record of the drive.

This means that you will have to do a repair on Windows and then do a rescue on linux I guess in order to get windows back able to boot AND get grub back in control of booting so you can access both.

---

### Post by thisishard on 2007-12-02
Nuts! I'm not sure of the best course of action for me.  I'm leaning towards a windows repair.  If that works, how do I get started with a linux rescue?

Oh, and thanks for the help.

[edit]  I'm worried about the windows repair facility.  The OEM disks with the repair are Pre-SP1 disks, and, of course, I'm currently running SP2.  I'm worried this might add to my problems.

---

### Post by Multi-Booter on 2007-12-02
Yeah... that's a real aggrivation with the service pack thing.

It would be nice if you could slipstream SP2 into your copy of XP... which can be done.

As I'm thinking right now... you might could just do a 'Fdisk /MBR' or whatever (more than one way to fix MBR). This would also bring back your XP MBR and not mess with your install. 

Still same deal though about Linux... but you could just use XP's bootloader to boot Linux because the OS would still be there. This would be adding the info to XP's boot.ini file so it would know where to go get and load linux.

Research those ideas some... think about them... and see if you feel more comfortable with this possibility. If so, I'm around to explain and help...


As for the Linux Rescue thing... I think I have had to try to do 'one' ever. Linux just is not as flaky as windows, so... Anyways, you'll need to boot your install disk and work from there to get grub back after working on XP, which will mess it up. 

This is all 'nutshell' information... research them and decide which direction you might want to go.

---

### Post by emilew on 2007-12-02
Hi, A couple of days ago I had the same problem, on a system with removable disks.The Ubuntu disk worked ok but NO XP disks would boot (reboot permanent) I could not even reinstall XP. I tried to reinstall the standard HAL files instead the ACPI, no way. At  last I did a reset to factory setting of the BIOS.
Problem gone, both Ubuntu and XP are booting again

---

### Post by thisishard on 2007-12-03
OK, thanks for the info.  I'll do some research.

I can attest to windows being flaky.  If I remember correctly, this is the third or fourth time I've had windows boot issues with this computer (I bought it in 2001 or 2002).  With my limited knowledge each instance required a system restore.

Also, I just realized I do not have a copy of XP.  I only have the system restore disks.  It seems like I remember that I couldn't repair the OS by itself.  I'll have to dig up a copy of XP.

[edit]  With regard to resetting the BIOS to factory defaults, I do have another questions.  During the install, I didn't specifically change BIOS settings.  Did the install do this somehow?

---

### Post by drw123 on 2007-12-03
I had a problem similar, could not find NTLDR for XP. Was ready to reinstall but tried this. Reinstalled Ubuntu, it made the corrections in the menu.lst, now all works.

---

### Post by kevinatkins on 2007-12-03
Hi,

Windows can be a pig but I have had issues in the past with resizing partions using Linux installers, which don't always do a spectacular job... it might not be the fault of Windows...

What I'd suggest first off is to grab hold of a proper XP disk - it doesn't matter whether it's SP1, 1A or SP2... The main thing is having the XP disk. Then boot from that disk and start up the recovery console. Once you're in the recovery console, try using chkdsk to repair your windows filesystem (you'll need to add some switches - try chkdsk /? for a brief resume of options - I can never remember them off the top of my head..) - it's possible this might rescue things. Note that it normally takes a *long time* to run!

 If you use your original system restore disks, it's more than likely that they'll wipe your hard drive (including Ubuntu) and just put your system back to what it was like when new...

---

### Post by babygirl on 2007-12-08
> **curtis1552 said:**
> Sadly for you it dosn't seem like the problem is based in the actual bootrecord or in GRUB.
If you get the prompt for safe/normal/etc it meas that windows has started to boot, but the problem  is with windows itself. You will probably have to do a reinstall - try to run the repair off the CD before you do a complete reinstall.

Thats not the problem at all. It IS the MBR. I have delt with this exact issue MANY time. When I was running windows I was so dissatisfied that I was constantly playing with Linux. As a side effect if GRUB is installed incorrectly, it will also write files to the Windows MBR. This is VERY easy to fix. Insert yer windows disc and boot from it. Repair windows in the repair console, and type "fixboot" or "fixmbr" depending on yer setup. If those don't work, then type "help" and look for the command you need. This will fix windows, but has a habit of messing with GRUB sometimes. But Linux is free so install away!!  :)  Just don't get nuts and burn out yer HDD..... :rolleyes:

---

