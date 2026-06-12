---
title: "Vital Edgy eft dual boot question (probably never discussed before)"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by naser on 2007-03-20
Hi everyone, I'm a dazed and confused PC user still unable to decide between a single OS (Win XP or Ubuntu) for both of them lack specs the other can satisfy flawlessly. I've installed Ubuntu before and used it with easy and fun. But all of the time, I had to install Ubuntu in such a way that it altered the** mbr** (yes, it comes down to the same damn mbr). As usually, I had to load XP from the grub boot-loader, and if somehow that got corrupted..I had no other choice but to restore XP's boot record with the fixmbr command. All this time I have longed for a single solution to my problem, how to install Ubuntu without damaging the actual windows mbr. I had found ample solutions, but each one of them had needs I was unable to meet. For example, here are some stuff I can't do:

* I don't have the internet connection to download a Linux system rescue disk which as [per some suggestions]("http://www.linuxdevcenter.com/lpt/a/6554") on different forums, can be used to do what I talked about in the above.

* I have tried various Windows based grub installers like WinGrub, but all of them had extremely complicated GUI. I haven't found any tutorials which discusses a simple way of using WinGrub. Can anyone suggest/post a simpler step-by-step instruction? (would be best if there are some screenshots included)

* I don't have a floppy drive, so installing grub on the floppy drive is a useless solution.

* I can't use the [experimental Ubuntu Installer]("http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html") called "Wubi" because I requires the user to download the whole ubuntu installation cd from the internet, which again is an impossible task from my perspective

So here's what I need " **[SIZE="4"]A simple solution that would allow me to install Ubuntu 6.10 Edgy Eft without damaging Win XP MBR record[/SIZE]**" . Usage of WinGrub or any other windows based grub modders/installers is acceptable as long as there are proper documentation available.

So, can anyone really help me out?

---

### Post by Ambimom on 2007-03-20
Have you considered virtualization.  Either Parallels for Windows or VMWare Server will allow you to keep your Windows MBR intact.

I've tried both.  I can run both operating systems simultaneously which for me solves the problem of having to reboot all the time.  The only drawback is that my microphone and disk drives are only available to XP; but that has not proved much of an inconvenience.

---

### Post by naser on 2007-03-20
> **Ambimom said:**
> Have you considered virtualization.  Either Parallels for Windows or VMWare Server will allow you to keep your Windows MBR intact.

I've tried both.  I can run both operating systems simultaneously which for me solves the problem of having to reboot all the time.  The only drawback is that my microphone and disk drives are only available to XP; but that has not proved much of an inconvenience.

Thanks for the suggestion. I have tried out VMware, but actually I was trying to install and run Ubuntu as a real OS, not a virtual one. VMware still has compability issues :(

---

### Post by alex77 on 2007-03-20
If you have the spare cash, you could buy a second hard drive. Unplug your windows hard drive when you want to install ubuntu, then install ubuntu onto your shiny new hard drive. This way, neither OS has any knowledge of the other existing, and your mbr is untouched. Instead of using grub to decide what hard disk to boot from, use your bios. (probably press F8 at boot to choose boot device)

---

### Post by bulldog on 2007-03-20
Or read this and make a GRUB bootdisk or what ever you prefer,

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mvoorberg on 2007-03-20
Similar to the above suggestion of installing a second disk, I've got removable drive trays in my machine.  To switch OS's, I power down, swap HD's and bring it back up.  Only risk is dropping a disk but that's minimal 'cause of the handles on the trays.

-Mark Voorberg
[www.objectclarity.com](www.objectclarity.com)

---

