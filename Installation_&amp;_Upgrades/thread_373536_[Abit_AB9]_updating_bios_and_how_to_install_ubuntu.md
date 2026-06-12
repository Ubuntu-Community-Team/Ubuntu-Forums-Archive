---
title: "[Abit AB9] updating bios? and how to install ubuntu"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by Gehaktbal on 2007-03-01
Is there anyone out there who can help me get ubuntu on my setup plz!
Iam stuck with windows now for about 4 months or so and it is really anoying.
I have tried several distro's and none works.

The first step would probably be update my bios to 1.6 but i do not have a floppy drive.
So i would need a dos boot cd with cdrom support.

I can make a boot cd with nero. This would boot dos nicely but then i can't get to my files on the disk anymore.

Then the next big problem.

Wich cd of ubuntu do i need? what parameters should i gave it when booting it and what settings should i make in my bios to get it to work?

Till now i have had no luck at all. I even tried a net install with a different network card that works perfectly in my server. But again no go.

Could anybody plz plz plz give me some info on how they did it on a ab9 bord or even tell me a gnome distro that does work?

---

### Post by Gehaktbal on 2007-03-02
Kick? Noone on the forum has succeeded in installing ubuntu on a AB9 board?

---

### Post by chewearn on 2007-03-02
Here is a post from someone who successfully install ubuntu:
[http://ubuntuforums.org/showthread.php?t=321005](http://ubuntuforums.org/showthread.php?t=321005)
From reading the thread, the generic 32-bit version works just fine.

About the other problem of updating your BIOS, can your motherboard boot from a flashdrive?  How about using a spare harddisk?

---

### Post by Gehaktbal on 2007-03-04
I don't know for him but it is save to say i tried almost every ubuntu version out there and i stil can't get it to work.
The bord can boot from usb disk but i have no idea how to make a bootable flash drive.

the complete setup is:

ab9
1gB memmory
nvidia 9700GS
1 sata 160gB sata disk
1 ide cdrom

Pretty basic machine and no exotic hardware.

---

### Post by chewearn on 2007-03-04
I have not find any need to boot from the USB drive, so have not tried it.  But, there are a many sites that can guide you:
[http://www.google.com/search?hl=en&q=making+boot+flash+drive&btnG=Search&meta=](http://www.google.com/search?hl=en&q=making+boot+flash+drive&btnG=Search&meta=)

Now, that's about BIOS upgrade.  I am not sure how that relates to not able to install ubuntu, since you have an IDE CD-ROM.  How about if you post an exact description of your problem; like when you install ubuntu (pick one version; I suggest Ubuntu Edgy Eft 6.10); so we can look specifically to the problem you are facing?

---

### Post by Gehaktbal on 2007-03-06
Ok.

At right this moment i tried to install Ubuntu via tftp.

Edgy eft stopped during install because it could not find my network drivers for the realtek chip.

So i tried Feisty.
This worked pretty good and it connects nicely to the internet and downloads the packages needed for the installation.
But this install hangs because it can not find my harddisk which is connected to the jmicron via Sata.

How the * to continue :(.

Iam really sorry but al these problems are so irritating beceause they are still not fixed in feisty.

Problems -> no cdrom detected -> solved by tftp server and disconnecting my cdrom drive
-> not detecting realtek network chip -> solved by using feisty
-> problem not detecting my hard drive -> how to solve??????


Concerning the netwerk chip i found this:
> Playing around with my new media center PC at the moment.
Ubuntu 6.10 Edgy (daily build from Oct 13th) installed without too many problems yesterday, most of the hardware on my Abit AB9 pro motherboard was detected out of the box.
However the ethernet controller, a Realtek 8111B, card was not detected.
From lspci I got Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01) and after a quick look in google I found this article on how to get the card working. Worked great, just download, change the three MODULE_PARM lines in the src to MODULE_PARM_DESC and it compiles ok.But this is not a problem anymore in feisty.

So the only thing that remains is why does it not detect my disk and i hope that i don't get any grub errors after installing cause i read about those too.

---

### Post by Gehaktbal on 2007-03-07
kick

---

### Post by chewearn on 2007-03-08
Sorry, I was hoping somebody who actually own the same motherboard as you do might chip in.  Anyway...

> **Gehaktbal said:**
> At right this moment i tried to install Ubuntu via tftp.

You did not mention why you are not using the CD-ROM, pop in the Desktop LiveCD, to install ubuntu.  From previous post, your problem with CD-ROM has only to do with BIOS update.  But there shouldn't be any problem booting up the liveCD and install ubuntu.


> Edgy eft stopped during install because it could not find my network drivers for the realtek chip.

I'm not familiar with the Realtek issue you mentioned.  That's part of the reason, I was waiting for someone who has the AB9 motherboard.

---

### Post by Gehaktbal on 2007-03-08
I did not use the live cd because in my former experiance there were 2 issues with kernel 2.6.17:

1. The install would hang as soon as it tried to load the kernel.
2. During the install, when it wants to load the drivers etc, it would say that it can't find the ide cd-rom.

I tried to solve issue 2 by using a netinstall cd. But this the Edgy cd does not have or finds the correct network drivers for my realtek chip.
This is solved by using the Feisty install cd.

The only problem that cd has during install is that it does not find my hard disk. It just hangs at 2% when it is trying to find my hard disks.

---

### Post by Gehaktbal on 2007-03-09
Little kick again.

---

### Post by daninca on 2008-03-15
I have a different Abit motherboard, but the same flash update problem.  The instructions on creating a bootable flash drive under linux aren't easy to find.

I did find one approach that works.  Take a dd image of a bootable floppy (dd if=/dev/floppy of=MyImage bs=8k).  Mount that on Linux (or use mtools), and copy the updater and image to it.  Unmount.  Now dd that image to a USB flash drive raw device.

Congratulations, you should now have a 1.44MB USB drive.  The Abit should boot from that just like a floppy and then you can do the bios upgrade.

There are supposed to be other ways to do this that preserve more capacity, but I couldn't get them to work.

-Dan

---

### Post by wolfchri on 2008-03-18
Hello,

if you have a DOS program for your motherboard, then BIOS updating from CD or even USB stick is simple and quick.

Read this little guide, I hope it helps you: 

[http://vale.homelinux.net/wordpress/?p=238](http://vale.homelinux.net/wordpress/?p=238)

:guitar:

---

