---
title: "Problem with Installation and Secure Boot turning off"
date: 2018-03-30
forum: Installation &amp; Upgrades
---

### Post by rorocools on 2018-03-30
[CENTER]
[/CENTER]
I performed a dual boot of Ubuntu 16.04.4 LTS with my Windows 10 system. In the installation, I checked the box saying "install third party software" and entered a password twice to turn off secure boot. However, upon rebooting, my computer only showed a black screen with a blinking cursor, and some small text at the top left corner of the screen. I was able to type letters and hit enter, but it was not accepting any input (the function keys appeared as strange arrays of characters). I was never prompted to enter the secure boot password. I didn't know what to do, so I held the power button down to shut down the computer, and when I turned it on again, the GRUB menu showed up normally and I was able to boot into either operating system. However, I went into my system settings and found that secure boot was still enabled despite the fact that I set up the installation to disable it. I disabled it in BIOS manually, but re-enabled it again soon after as I worried it would mess up the way Ubuntu was installed with secure boot turned on.

So, I fear that when I turned the computer off using the power button, I messed something up that will affect future use of it. What was that black screen that showed up with text and a cursor. I have also read that leaving secure boot enabled can mess up the installation of third party drivers in the future, so I am not sure if I should leave it as it is, or disable it again. I am also curious if I will ever need that password I set for secure boot during installation ever again. Please offer any information that may be related to my situation, I am not very knowledgeable of OS's in general. I am not aware if secure boot is extremely important or if it is alright to disable it now. Thank you.

---

### Post by yancek on 2018-03-30
> [SIZE=3][COLOR=#111111][FONT=Ubuntu] In the installation, I checked the box saying "install third party software"[/FONT][/COLOR][/SIZE]

That just makes the installation process take 2-3 times longer than without that option.  You can install that software later with an update/upgrade but if you have a good connection and are not in a hurry to install, that works.

Some manufacturers require you to set Trust in the BIOIS to install another OS, Acer for example.  Who is the manufactuer of the computer?
It isn't necessary to disable secure boot to install, it can work with or without secure boot.

> [SIZE=3][COLOR=#111111][FONT=Ubuntu]read that leaving secure boot enabled can mess up the installation of third party drivers in the future[/FONT][/COLOR][/SIZE]

Don't know about that, what's your source of information?

---

### Post by rorocools on 2018-04-22
No specific source, I just read on a few posts that trying to load signed kernels with secure boot on made hardware on people's computer stop working. I'm just wondering if it is safe to leave secure boot on if I'm going to be downloading a variety of drivers/software in the future. I'm afraid that I may brick my computer.

---

### Post by oldfred on 2018-04-23
It is primarily proprietary drivers like nVidia or WiFi that vendors have not certified and Ubuntu cannot then certify, so UEFI Secure boot must be off.
But if system runs well without proprietary drivers, then whether you have UEFI Secure Boot on or off is just up to you.

---

