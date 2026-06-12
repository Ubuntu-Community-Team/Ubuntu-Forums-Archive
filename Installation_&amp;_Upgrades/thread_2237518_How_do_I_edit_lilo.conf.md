---
title: "How do I edit lilo.conf?"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by bryan24 on 2014-08-02
Hello,

I am a super noob at all things Linux. I just downloaded the latest version of Ubuntu, and installed it last night. I keep getting an error when booting up --- LILO is looking for sdb1 as my root when I know it is sda1. I want to modify my lilo.conf file to point the root to sda1.

How do I edit my lilo.conf file from BusyBox? Literally, I need the actual command syntax, not just a high-level overview of how to do it (sorry, as I said, I am extremely new to Linux).

Thanks in advance!

---

### Post by oldfred on 2014-08-02
Lilo?
While Lilo is available, it used to be obsolete, but I believe they started development again. 

But grub2 is the standard boot loader with Ubuntu.

From live installer, install this and run the BootInfo report. It should show details. Post link it gives so we can review those details. It also can install grub2 if you want to use it.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bryan24 on 2014-08-02
I did try installing grub, but it gave me a fatal error, so I went with the other option (lilo). Please help --- just want to get into Ubuntu and play around. Thanks

---

### Post by bryan24 on 2014-08-02
btw, it doesn't appear that I have the "vi" command available --- that has been one of the commands I've seen other people using (through Google) to edit their lilo.conf file.

---

### Post by yancek on 2014-08-02
> While Lilo is available, it used to be obsolete, but I believe they started development again

The only major distribution I am aware of that still uses Lilo is Slackware, probably some of its derivatives also.  Slackware is the oldest Linux distribution still currently being developed and has used Lilo as its bootloader since the 1990's, still does.  It's never been out of development.  Grub became predominant in the 1990's and a few years ago Grub2 came into being and common use in a number of distribtions.

That being said, Grub2 is your best bet with Ubuntu and it would be easier to resolve your problems with Grub2.  Also, you neglected to post the 'fatal error' you got with Grub so there's no way to help.  vi is installed on practically any Linux.  You would need root privileges to edit the lilo.conf file in the /etc directory.  I'd suggest staying with Grub2, you'll get a lot more help with that here.

---

### Post by bryan24 on 2014-08-02
Alright, thanks all for the responses

---

### Post by Richard_Klancer on 2014-08-14
Quick answer: you can probably install Grub using [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") and boot correctly. 

Longer answer: I think I can provide some insight as to how @bryan24 ended up installing LILO in a new Ubuntu install in 2014, as I recently went down the same path, as follows.

First, I grabbed a random old laptop that I wanted to wipe and install Ubuntu onto (it was a Lenovo L512 ThinkPad running windows 7; I wanted it to work as a barcode scanner using a webcam and the zbar library, in order to prototype something I'm designing.). Note that I haven't actually administered a Linux system since literally the previous century, and never for work.

I created a bootable USB stick using the "Ubuntu 14.04 (Netinstall)" option in unetbootin on my regular computer (a Macbook Pro). I went through the guided steps to install Ubuntu.

The "install GRUB" step failed. No other error message is given in the installer UI. I happened to learn the magic keystroke to open the console, and the error was "error: embedding is not possible, but this is required for cross-disk install." I was relying on the installer to "just work", so I had no context for even thinking about how to fix the problem (I know what a bootloader is, roughly, and that's about it)

Fortunately, however, the installer UI presented two options for the step where you install a bootloader: install Grub, or install LILO. So I just chose the latter, since the first failed with the above mysterious error everytime I tried. Installation finished successfully.

(I bet this is the same reason @bryan24 installed LILO.)

Long story short, LILO would boot ... and dropped me down to BusyBox/initramfs because it couldn't find /dev/sdb1 (my main partition was /dev/sda1). Booting the Boot Repair image instead, and choosing the default repair, fixed the problem.

HTH, --Richard

---

