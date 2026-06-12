---
title: "Not able to install ubuntu"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by vickysodhi67 on 2013-09-12
As m hving a new machine sony vaio i5 after the complete installation of the ubuntu os the display starts blinking and os does not start...
Help me Please..

---

### Post by rencemc on 2013-09-12
I seen a couple instances where this happend. I just let it sit there (just leave it at least a half hour or so)
and it eventually booted and the issue never happened again. It's worth a shot. I too got impatient and kept
rebooting it. Then I just waited :)

---

### Post by Kirboosy on 2013-09-12
Hi, and let me be the first to say "Welcome to the forums!" (If no one has already)

First a couple of question need to be answered.

1. What version of Ubuntu are you trying to install?
2. What type of architecture are you trying to install. (32 Bit or 64 Bit)
3. Does the installation give any errors at any point?


Thanks!
~Caboose

---

### Post by vickysodhi67 on 2013-09-12
i have tried version 12.04 and 13.04
64 bit
No it does not give any error

---

### Post by Kirboosy on 2013-09-12
Can you provide the exact model/number on the laptop?

---

### Post by vickysodhi67 on 2013-09-14
sony vaio intel i5 processor model no SVE15116ENB

---

### Post by sudodus on 2013-09-14
More questions: Do you intend to run only Ubuntu, or do you want to dual boot with Windows 7 or Windows 8?

Windows 8 makes a big difference, because it is normally installed with UEFI, and it makes dual boot much more difficult.

---

### Post by Kirboosy on 2013-09-16
I was searching around and I was able to find this.

[Sony Vaio EFI will not boot into grub]("http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/150640#150640")

So I guess the UEFI and a couple settings need to be tweaked on the laptop in order for Ubuntu to run properly.

EDIT: I would recommend trying to boot into Ubuntu LiveCD and use the [BootRepair]("https://help.ubuntu.com/community/Boot-Repair") tool too see if that fixes it.

---

### Post by vickysodhi67 on 2013-09-18
Dual boot with windows 7

---

### Post by Bucky Ball on 2013-09-18
Does it work ok when you 'Try Ubuntu' from the disk? If so, that's a good sign.

Try this:

Boot from the installation media and when you get to the window that says 'Try Ubuntu' 'Install Ubuntu' and a few other options, hit F6. From the pop-up list choose 'nomodset'. Continue. Did that work?

UEFI could certainly have something to do with it. I presume you have Win installed already? If not, install that FIRST and leave free space for installing Ubuntu, then install Ubuntu.

And welcome to the forums. ;)

---

### Post by sudodus on 2013-09-18
> **Bucky Ball said:**
> Does it work ok when you 'Try Ubuntu' from the disk? If so, that's a good sign.

Try this:

Boot from the installation media and when you get to the window that says 'Try Ubuntu' 'Install Ubuntu' and a few other options, hit F6. From the pop-up list choose 'nomodset'. Continue. Did that work?

UEFI could certainly have something to do with it. I presume you have Win installed already? If not, install that FIRST and leave free space for installing Ubuntu, then install Ubuntu.

And welcome to the forums. ;)
+1
I confirm because I think you responded to my question, *vickysodhi67*

---

