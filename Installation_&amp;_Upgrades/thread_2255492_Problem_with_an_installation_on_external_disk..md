---
title: "Problem with an installation on external disk."
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by davide97 on 2014-12-05
Hi, i these days i tried to install Ubuntu 14.10 64bit in my PC, that have a intel g3220 cpu, using the onboard card.
I'm trying to install Ubuntu in a Internal IDE Hard disk, using a **usb box**, but i'm having a lot of problem> i get that

[http://i.imgur.com/iQbFJqqh.jpg](http://i.imgur.com/iQbFJqqh.jpg)

Why am i getting that? I also tried to uncheck/check the legacy usb from the BIOS, but if they're disabled the computer doesn't see the hard disk.

The only way to use Ubuntu, is to enter in the "recovery mode" from the advanced section in the initial boot menu, type **exit**, than click enter on **return to normal mode**, than Ubuntu starts, but without the GPU drivers. 

Can you help me? Thank you, and sorry for my bad english. Bye :)

---

### Post by oldfred on 2014-12-05
Are you trying to install to an insternal drive or a USB drive. Or are you planning on moving drive to internal after installing?

If system is UEFI/BIOS then you may have to turn off secure boot and in setting somewhere turn on allowing UEFI boot from USB ports. With UEFI there seem to be a lot more settings. And a few only open up those extra settings if you put in a password, but if that is required never ever lose that password.

What brand/model computer and what video  card/chip? 
If using Intel video there is only one driver, but it often needs boot parameters to work. see post by ubfan1, add correct parameter the same way as nomodeset.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by davide97 on 2014-12-05
I installed ubuntu on an usb drive, and i used the password, but the only option that i can change is the secure boot, that's disabled. 
I tried to write the 'nomodeset', replacing quiet splash, but i didn't delete the other things, is right?
mh.. what else can i try?

---

### Post by oldfred on 2014-12-05
What brand/model computer.
Are you using Intel for video, then nomodeset does not work and you have to use one of the other settings.,

---

### Post by davide97 on 2014-12-05
Yes, im using the intel integrated gpu.
I read that i must use 

"Some new Intel may need above or this:
        i915.i915_enable_rc6=1
            Or Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60"

Right? But how? When have i to write that? Thank u very much for your help :)

---

### Post by oldfred on 2014-12-05
Instead of nomodeset use one of those settings on the Linux line in grub menu as instructions show for adding nomodeset.

Do not use 1280x1024 unless that happens to be your screen/monitor size, but use the actual size of your monitor.

Try one, if that does not work, try the other. When we find one that works we can add that to grub's configuration file as a permanent setting so you do not have to manually add it everytime you boot.

You also may need some other settings from the post by ubfan1. Some laptops may just have screen brightness set to 0 and you use f-key to change. Or need settings to enable brightness correctly.

What model computer?

---

### Post by davide97 on 2014-12-05
Ok, i tried "video=1280x1024-24@60" and it worked..but in a strange way, because i got the first post's error, but typing "exit" i directly went to the access page of ubuntu.. with the correct driver! It's a bit strange..

My Computer is not a laptop, it's an assembled one! (if it's important, with a asrock h81m dgs 2.0 and a g3220 processor)

---

### Post by oldfred on 2014-12-05
What is monitor?, only some older ones might use 1280x1024?

Some have issues with Asrock and its asmedia ports, do not use any asmedia port

UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

