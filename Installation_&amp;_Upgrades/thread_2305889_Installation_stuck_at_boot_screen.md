---
title: "Installation stuck at boot screen"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by phil86 on 2015-12-10
[I](This was [posted on askubuntu]("http://askubuntu.com/questions/687029/ubuntu-15-04-installation-gets-stuck-at-loading-screen") and received no answers.)
[/I]
I'm trying to install Ubuntu 15.04 for a while now. I setup a bootable USB stick with [Rufus]("http://rufus.akeo.ie/") (also tried [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")). I verified the checksum of the iso file before that.

The issue is that after hitting install and after seeing the typical load animation (ubuntu on purple screen, five dots below) nothing happens. The installation doesn't even start. There is no error, nothing. I don't know what to do at this point.
[B]
Further information:[/B]
[LIST]
[*]**Operating system:** Windows 8.1 (64-bit) that was pre-installed on an Acer laptop (UEFI)
[*]**Boot Mode:** EFI / **Partition style:** GPT ([Identifying which boot mode the OS uses]("http://www.rodsbooks.com/refind/bootmode.html"))
[*]Fast Startup and Secure Boot are disabled
[*]There is free space on my hard drive which is not yet partitioned
[*]Windows 8.1 installation disk in case I need to repair something
[/LIST]

---

### Post by howefield on 2015-12-10
Any reason why you do not try 15.10 (or perhaps you have) ?

Main reason being that 15.04 is end of life next month so only a few weeks of support left.

---

### Post by phil86 on 2015-12-10
I've been trying to install this for a while now, maybe 15.10 wasn't released when I downloaded the ISO. Anyway, I downloaded 15.10, verified the checksum and tried again. The issue persists. Nothing has changes as far as I can tell.

What can I try now?

**Update:** In a desperate attempt to install another Linux distribution, I learned that this doesn't work either. Issue is the same. Fedora doesn't boot past the load screen either.

---

### Post by howefield on 2015-12-10
Booting in verbose mode might give you some clues. Press F6 at the Live boot screen and remove quiet splash from the boot line and press enter to continue the boot. YOu might also try the nomodeset option, again from the grub boot screen > F6.

---

### Post by phil86 on 2015-12-10
**1. DVD**

Tried booting again from a DVD this time which surprisingly got me to the installation dialogue. This froze at the partitioning screen and I had to leave due to a lecture anyway. I came back and tried again, but I had no luck.

I tried a couple of times with the install option but nothing. Tried booting Ubuntu live which resulted in a bunch of errors which I wasn't able to read. Then it told me that it was proceeding in low-graphics mode because it could not detect my graphics card (Nvidia GeForce GTX 850M). After that I saw more errors (something containing "mismatch in ips_enabled", related to "intel"). It did not finish booting into live Ubuntu and I had to reboot.

**2. Boot Options (no quiet, no splash)**

I tried your first suggestion (needed to hit 'e', not F6, removed the two words and hit F10 to boot). After a while I got to a grey screen but the system was not responsive. Couldn't move the mouse. Stayed like that. I rebooted.

[B]3. Boot Options (No quiet, no splash, nomodset)

[/B]This got me to the install dialogue finally. After clicking "continue" the first time which did load for 10 minutes after which I gave up. During this the system was responsive. Could access tty for example.

I rebooted again and tried the same boot settings. Now it didn't go to the install dialogue but threw a lot of SCHED_ERRORs. System resetted shortly after.
[B]
Additional Notes:[/B]

During the first attempt with the DVD I was able to go to the partitioning screen. I noticed that an old Ubuntu 14.04 partition was still present which I believed I had deleted.

**Update:**

I did it. After all the above and booting back into Windows I tried it one more time. With the default installation settings. And it worked. I installed Ubuntu and up until now everything works great.

I don't know what's wrong with my system but I can imagine that there is still something wrong with it. If someone has a hint as for what I can check my system for, I'd be grateful.

Anyway, thanks for helping me out.

---

