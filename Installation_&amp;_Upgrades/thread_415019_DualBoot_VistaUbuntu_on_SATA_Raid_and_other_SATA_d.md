---
title: "DualBoot Vista/Ubuntu on SATA Raid and other SATA disk"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Trubbel on 2007-04-20
Hi

I have downloaded Ubuntu 7.04 AMD64 and I'm excited to try it out. However I've run into quite a bit of a problem. After attempting to search for a solution I haven't found something that matches my exact problem.

My current setup:
- Vista 32bit installed on a RAID of 2 Raptor SATA disks (connected to the first and second SATA spots)
- Clean 400GB SATA disk (previously NTFS) on slot 3 that I'm trying to install Ubuntu on.
- An extra SATA NTFS 500GB disk for media on SATA slot 4.
- There are 2 slots for IDE hard drives, but both are unused. I think they are drive 1 and 2, and the SATA goes from 3 to 6.

All on a nForce 4 motherboard with the nVidia Raid controller.

After booting from the Live CD I selected to install Ubuntu. On the drive select screen, it shows the Raptor raid as 2 single disks (which it cannot mount of course). I choose the "number 3" 400GB drive for Ubuntu (something called Guided install or similar) and I change nothing else. Ubuntu does not recognize my Vista install. The install finishes nicely and asks to reboot, which I do.

Reboot and it goes straight into Vista, so I figure I need to change the boot device in the BIOS. There I change it to drive 3 (400GB). However, when booting on this third drive, I get a scary error message saying something like "Cannot find any Operating System" and I have to do a hard reboot. If I set BIOS back to the Raid drive, Vista still works fine.

Can you please help me? I very much want to use Ubuntu, but I cannot uninstall Vista (just yet anyway). Help is greatly appreciated.

Please ask anything that might be unclear!

---

### Post by Trubbel on 2007-04-20
No? Just bumping because I really want to get Ubuntu installed.

Hope someone can give me a helpful hint.

---

### Post by galego on 2007-04-20
are you using RAID 1?

if you are stripping i would make a new partition form the Vista GUI in you r RAID. so as far as Vista is concerned you would have a NEW unformatted logical drive. the nForce RAID controller should allow this. (sorry i use a Rosewill card) any way... once you have an empty partition reboot and install Ubuntu this time it will see the emty space and you will install there.

if you are Mirroring.... im not sure what to do exactly.

another option would be using "The Google" and search for grub install and try to re-install Grub in what you have, but i dont think that would work???!!! MAYBE? 

sorry i dont think im helping!

what does Disk Manger say in Vista BTW?

---

### Post by Trubbel on 2007-04-20
I'm using Striping Raid on the harddrives I use for Vista. The other's are not RAID.

I do _not_ want to install Ubuntu on the same drive as Vista (not enough space), but on the third drive that is empty already.

I tried searching for grub-install and even tried using that command in terminal, but I can't even boot into my installed Ubuntu, so everything like that is from the Live CD. Didn't get that to work, and didn't really understand it.

Disk Manager in Vista doesn't say much. I mean, it finds all the drives properly as it should. Not much to say about it.

---

### Post by hawa on 2007-04-20
similar problem here,

one solution I found was [https://wiki.ubuntu.com/FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy")

but had no time yet to try it

the point is that you let the installer see the raid partition so it can modify the boot menu for dual boot, no matter where you want to install ubuntu to.

---

### Post by Trubbel on 2007-04-20
Thank you hawa.

Hmm. That Howto is quite extensive huh? A looot of work it seems to me. Perhaps this is just too advanced for me >.<

But, if you wanted to install the bootloader on the raid array and have it find Ubuntu on the "third" sata drive, how would you modify that guide? I mean, since it's intended for Ubuntu on the *same* drive, the first drive.

NB: And sorry if I sound whiny. It's just that I was told Ubuntu was really easy to install/setup.

---

### Post by hawa on 2007-04-20
as I said, I think it is all about for ubuntu to see the raid, change the boot menu to have dual boot.

where you then install ubuntu is unimportant, because the boot menu points the the way

so I would say the HowTo is not to be changed except for the place where ubuntu to install to.


Besides Ubuntu like most linux systems is very easy , except it comes to raid or extreme new components

---

### Post by reiki on 2007-04-20
If you change the BIOS boot order so that it wants to boot the 400GB drive first, then you GRUB menu may be incorrectly pointing toward (what is now) the wrong partition. Let me see if I can explain that better...

Your original install:
BIOS has raid set as first boot
You install Ubuntu and the installer sees the raid as 2 drives (probably like /dev/sda and /dev/sdb ...or... hd0 and hd1)... 
You tell installer to install ubuntu to THIRD drive (probably /dev/sdc ...or... hd2)

NOW... you change BIOS to use the THIRD DRIVE as first boot.
Now grub starts and looks for an operating system on /dev/sdc (because that's where the 400GB drive was when you installed ubuntu) but it doesn't find an operating system

TRY THIS:

Keep that 400GB drive as first boot in BIOS. When grub starts hit Escape to stop the timer and give you a chance to look at the menu. Highlight the line that would make it boot ubuntu and hit the letter "E" on your keyboard. This will let you edit that entry. I am almost certain that you will find it pointing to the wrong place as I have done that same thing myself more than once. :)  So edit the line to correct it and then hit the "B" key to boot.

NOTES: editing grub on boot this way does NOT change anything permanently. So even if you get it to boot, you'll then have to edit the /boot/grub/menu.lst file to permanently change it.

NOTES#2:
Ideally, you'll want to get this booting from whatever drive you use the most.... if that's the raid, then you will have more work to do, but I think this may help you get to ubuntu. And once you do that, you may not want Vista any more anyways :)

---

### Post by hawa on 2007-04-20
sure thing, 

he could change the bios boot order to boot 3rd disk first, install ubuntu and the raid would stay as it is

then he choose the os to boot by setting the boot order (raid or 3rd hdd)

but always going to the bios to change boot order to get the os you want, is not such a comfortable workaround ....

and he will have problems getting the work from windows to ubuntu and other way ....

---

### Post by Trubbel on 2007-04-21
Yeah hawa, that is what I was thinking to.

Well, at least now I have that (huge) guide. Maybe someday I'll muster the courage to actually try it out. For now it does seem a bit risky and quite over my head. Thank you though.
Seems it's still Vista for a while >.<

---

