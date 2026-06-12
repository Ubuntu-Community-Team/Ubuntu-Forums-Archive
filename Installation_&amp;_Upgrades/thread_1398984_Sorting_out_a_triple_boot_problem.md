---
title: "Sorting out a triple boot problem"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by varangian on 2010-02-05
For completeness here's the history that got me to this point:

Stage 1

/dev/sda - disk with XP OS, set to be first boot disk in BIOS
/dev/sdb - a small data disk to supplement sda
/dev/sdc - disk with Ubuntu 7.10

This setup worked find, GRUB dual booting as you'd expect.

Stage 2

Disks setup as 1 but /dev/sdc now re-partitioned somewhat better than before and with Ubuntu 9.10 clean installed onto it.

This still dual booted but, as covered in numerous other threads here, GRUB2 was very slow to load the menu as it was not located on the boot disk.

Stage 3

/dev/sdb removed and replaced by a larger disk that was setup with a couple of NTFS partitions and the rest EXT4 as a data partition for Karmic. Windows 7 was then installed onto /dev/sdb.

W7's boot loader, as expected, noticed the earlier Windows version and ignored Ubuntu. It offered the option of booting XP which I assumed would have worked though I never actually tested that. However, as Ubuntu is my working OS and I only have the Windows OS's for playing games, I swiftly grabbed the Karmic live CD and re-installed GRUB2. I took this opportunity to put GRUB2 onto /dev/sdc and then set this disk to be the first boot HD in the BIOS.

At first glance this all seemed to be working fine. GRUB2 had noticed the W7 boot loader on /dev/sda and the delay loading the GRUB menu had vanished. Windows 7 would boot OK and its loader offered the option to boot XP if I wanted it, or so it seemed. However, once I'd finished setting up W7 and had some reason to boot XP I ran into what is, I assume, a failure in the way Microsoft do boot loaders. Following their usual tendency to re-boot at every possible opportunity selecting that option just took me back into the GRUB menu.

The ideal would to have both XP and W7 as options to boot from in the GRUB menu, though if I had to get to XP via a W7 boot loader (if such a thing is possible) that would OK. Eventually I'll phase out XP but for the moment it would be handy to have it around. I've got one method in mind to get there:

- use the XP install disk to put its own loader back onto /dev/sda.
- re-install W7 on /dev/sdb but this time have /dev/sda temporarily disconnected and set sdb as the first boot disk so that W7 won't see the XP installation. I've no investment in W7 or vital data on /dev/sdb so I can mess around with these areas as much as I like.
- reconnect /dev/sda, set /dev/sdc as the first boot disk again and, once Karmic has been booted, get GRUB to rescan and refresh its menu.

However I'm no expert when it comes to multi-boot setups so if there's anyone who can tell me:

a) Will the above approach work?
b) If there's a better way of doing it in the first place?

I'll be grateful for any advice.

---

### Post by markbuntu on 2010-02-06
I usually leave boot loaders with their respective systems and set the boot drive to the one with grub on it and let it figure it out. That way no matter if drives or boot loaders fail everything else will boot.

Probably the best thing would be to reinstall the boot loader for XP, which you can do with a supergrub disk and then run update-grub so grub can find it.

I would guess that the original grub was on sda so it replaced whe xp bootloader which 7 failed to notice of course.

---

### Post by Mark Phelps on 2010-02-08
If you want to be able to use GRUB to choose individual OS's (without an MS Windows menu selection), you will have to setup each MS Windows drive to boot by itself.

If you don't want to fiddle around with CDs, an easier way to do this would be to download and install EasyBCD from NeoSmart Technology forums -- and use that to mess with the boot settings.

If you go to their forums, you will see instructions on how to:
1) move the Win 7 boot to its own drive
2) reset the XP drive to boot only XP.

After that, if you boot from the Ubuntu drive and run "sudo update-grub", you SHOULD be able to see two entries -- one for XP and one for Win7.

---

### Post by oldfred on 2010-02-08
More info on windows multiboot


To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by varangian on 2010-02-09
Thanks for the advice guys. Haven't heard of EasyBCD so I'll check it out and give it a whirl. Using Windows install disks to fix MBR's is pretty tedious so this sounds like a good option to try.

---

