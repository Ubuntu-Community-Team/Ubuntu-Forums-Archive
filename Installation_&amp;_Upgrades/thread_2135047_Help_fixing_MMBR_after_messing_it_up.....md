---
title: "Help fixing MMBR after messing it up...."
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by audiofied on 2013-04-13
So I have had windows 8 and ubuntu 12.10 working fine together with my uefi preinstalled windows 8 system for couple of months with no problems, I was able to boot both os from the bootloader and never had an error or problem.. The other day i came home and tried to boot my sytem and windows was not wanting to turn on the screen, it was just gray after logging in windows. ubuntu side was still fine. I tried a few different things and finally got it to boot and everything was back to normal, however my wife was on the computer on windows 8 last night and saw a pop up message from HP's software saying there were errors on the hd, she hit fix not knowing, and it rebooted the system and caused it to fail boot.. so not having a boot disk or anything else on a disk at hand I tried the recover option.. so damage being done: the software tried to format the ubuntu partition.. the Win8 recover utility completed with no errors from bios, and now i'm left with a grub 2 recover every time i try to boot, in every way(turning bios back to defaults: legacy off secure boot on, and also the way i was booting before, legacy on and secure/fast off. so i cannot get windows to boot, and there is no ubuntu on the hd anymore. So how can i fix the mbr to boot the recovered install of win8 now? all i can get is a failed key signature error if things are on default, and a grub2 recover the other way.. Is there any image i can write or prog to boot from usb to fix windows? I did not create a win8 recovery disk, and do not have one.

---

### Post by audiofied on 2013-04-13
id like to find a way to fix the system without buying the win8 installation disk or buying a recovery disk from the OEM if possible. considering i cannot boot to make one or get to command promp im not sure what else i can do.. thanks

---

### Post by oldfred on 2013-04-13
If you have UEFI, you do not boot from MBR, but from efi partition.

Best to see details, even if recovery erased Ubuntu. If BIOS/MBR, you just may need a Windows boot loader in the MBR as often recovery does not reinstall the boot loader as it assumes it is ok.

If BIOS based and you only need MBR this will fix it, otherwise post link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by MAFoElffen on 2013-04-13
If you boot from the Ubuntu Secure Remix ISO and run testdisk... The Secure Remix disk can ID UEFI and has the testdisk script on it.

Windows keeps a backup copy of the MBR in it's partition if it is messed up. "testdisk" is usually pretty apt at finding that copy  and checking to see that it is not corrupted also. If it is good, it will ask if you want to copy it over... That disk also has a knack for finding and repairing UEFI abnormalities. You can also run and post results from the bootinfo script from that Live Image. This is what I use when the Windows Rescue disks can't handle what is going on...

Just a thought.

---

