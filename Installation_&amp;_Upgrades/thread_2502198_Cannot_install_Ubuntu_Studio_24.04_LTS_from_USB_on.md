---
title: "Cannot install Ubuntu Studio 24.04 LTS from USB on ASUS Vivo AiO V221IC"
date: 2024-11-05
forum: Installation &amp; Upgrades
---

### Post by massimiliano-polito on 2024-11-05
Hi all,

I downloaded [https://cdimage.ubuntu.com/ubuntustudio/releases/noble/release/ubuntustudio-24.04.1-dvd-amd64.iso](https://cdimage.ubuntu.com/ubuntustudio/releases/noble/release/ubuntustudio-24.04.1-dvd-amd64.iso), checked the checksum was correct and created a bootable USB stick using Rufus.

 I modified the BIOS of my PC (ASUS Vivo AiO V221IC-UKBA020D, BIOS  version updated with the last version, dating back to 2018) to boot from  USB.

 The PC boots from USB and shows the bootloader options. I chose the  first one, something like "run and install Ubuntu". I can see the splash  screen with both ASUS and Ubuntu Studio logos and the rolling wheel.

After some minutes of that, the screen gets completely black with one line saying:
> [FAILED] Failed to start snapd.service - Snap Daemon.  

I made some searches and apparently Ubuntu 24.04 installer is a new one and it's still quite unstable.

Do you know how to solve the problem?

Is there another way of installing Ubuntu Studio?

Would it be possible to install an older release (not using the new  installer) and then upgrading to 24.04? If so, which one would you  suggest?

 Thanks.

Ciao,
Max

---

### Post by ajgreeny on 2024-11-05
It is always worth chosing the option to "Run Ubuntu without installing" rather than going straight to the install option.
That may give you more clues to problems related to any hardware incompatibilities with the OS itself; I always run the install medium live first anyway just to check it's a good USB.

You will find an icon either on the desktop or in the menu to install the OS from this live system so you do not need to boot again just to get to the installation.

Did you check that the downloaded .ISO file was good and not corrupted in any way? Always worth doing that unless you downloaded using a torrent client which checks as it downloads.

---

### Post by grahammechanical on 2024-11-05
You could try Ubuntu Studio 22.04 LTS. Supported until April 2025.

[https://ubuntustudio.org/support/](https://ubuntustudio.org/support/)

[https://cdimage.ubuntu.com/ubuntustudio/jammy/dvd/current/](https://cdimage.ubuntu.com/ubuntustudio/jammy/dvd/current/)

Ignore the dvd label in that address you will get a standard ISO image that can be put on a USB memory stick or DVD-ROM. It seems to be small enough to fit on a DVD-ROM

And then do an online upgrade to 24.04 LTS

Regards

---

### Post by massimiliano-polito on 2024-11-05
Thanks for your reply.

In the boot menu there isn't any bare "install option", there are only two options to run Ubuntu (both something like "Try and install" and another option to run it in some kind of "safe mode", I tried both with the same result).

The problem is that it doesn't start... it's blocked on the error i reported, so there is no way to check if something could be wrong in my HW. I can't access any log file either so I wonder why that daemon complains.

I checked the checksum of the ISO I downloaded and it was OK (well... as usual I checked the first three characters and the last three not all the characters).

Ciao,
Max

---

### Post by massimiliano-polito on 2024-11-05
Deleted.

---

### Post by massimiliano-polito on 2024-11-05
To grahammechanical.

I'll give it a try, thanks.

Ciao,
Max

---

### Post by massimiliano-polito on 2024-11-05
> **grahammechanical said:**
> You could try Ubuntu Studio 22.04 LTS. Supported until April 2025.


Do you think this release uses a different installer?

---

### Post by massimiliano-polito on 2024-11-06
Yesterday I prepared a USB bootable stick starting from Ubuntu Studio 22.04.05 instead of 24.04 and everything worked perfectly. I can now start my PC in Ubuntu and see the shortcut on the desktop to install it.

I'll install it, try to update it from 22.04.05 to 24.04 and see what happens.

Apparently there is something in 24.04 installer that's not compatible with my PC/BIOS/I-wonder-what.

I'll update this post in case I run into something interesting.

Thanks for your support.

UPDATE: after 4-5 nights of attempts I finally had the idea of trying with a different USB stick. I made this new USB stick bootable, ran the installer and installed 24.04 LTS without any problem. Maybe there was something wrong with the first USB stick I used but strange enough I wasn't reported any problem neither when I created it with Rufus nor when I used it.

Ciao,
Max

---

