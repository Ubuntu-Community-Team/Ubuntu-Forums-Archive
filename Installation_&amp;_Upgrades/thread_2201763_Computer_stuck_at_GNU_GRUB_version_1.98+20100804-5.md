---
title: "Computer stuck at GNU GRUB version 1.98+20100804-5ubuntu3"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by jack39 on 2014-01-25
Hi all, I'm new here (joined like 10 min ago), and I am in dire need of a solution. My computer ran out of batteries (left charger unplugged :oops:), and I had to charge it back up. When I turned the computer on, it brought me to this GNU GRUB verison 1.98+20100804-5ubuntu3
below it was:
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

No matter what I try, I cannot get to the normal log in screen. The version of Ubuntu is either 3 or 4, very ancient...

I also tried to download the latest version of Ubuntu by copying the download onto a USB stick (had 7GB so I know it fully downloaded) and inserting it into the port when the computer started. This probably sounds ridiculously stupid to you pro Ubuntu guys out there, but I have no idea how to use this OS/command line. Please help me either get past the GRUB thing or just directly downloading a new version without having to get past GRUB. Thank you very much in advance!

---

### Post by Bashing-om on 2014-01-25
jack39; Hi ! My Welcome to the forum .

Firstly let's determine if the installed version is worth investing any time in fixing. We want to know what version you are running.
Going to get you a command line interface to get that info.
Reboot, and when you get to that grub boot menu ( the list of kernels); press the 'e' key for edit mode ->
boot options screen; arrow down and across to the terms "quiet splash" and just before enter the term "text" -with out the quotes - remove the terms "quiet splash" and all after;
key combo ctl+x to continue the boot process to a text terminal (TTY1);
login with user name and your password (there will be NO response to the screen for password entry).
Tell us what the response is from this terminal command:
```

lsb_release -a

```

We will be more than happy to assist you in making a new install. if it is deemed the thing to do by you.

[INDENT][INDENT]it's ubuntu
[INDENT][INDENT][INDENT]it's all doable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jack39 on 2014-01-26
after a bunch of code/words pop up it does the normal error message thing: No init found. Try passing init= bootary. It then brings me to BusyBox v1.15.3 (Ubuntu 1:.15.3-1ubuntu5) built in shell (ash) Enter 'help' for a list of built-in commands. (initramfs)
I couldn't log in and when I tried doing the lsb_release -a, it said: /bin/sh: lsb_release: not found

It's not worth fixing, I'd much rather just download a new version. Nothing important was saved on that computer, it's much too bugged for me to risk it.
Thanks for the help though!

---

### Post by Shadius on 2014-01-26
If you're not worried about losing anything on that computer, then you can do a clean install of Ubuntu. 

Here's a helpful [link]("http://www.ubuntu.com/download/desktop/install-desktop-long-term-support")

Read the instructions for which method you prefer. If you're using a USB drive, then you'll need to make it bootable. Follow the instructions provided there.

---

### Post by jack39 on 2014-01-26
Won't work, even with the USB stick in, the GRUB menu thing shows up and won't let me get past

---

### Post by Shadius on 2014-01-26
Have you made the USB bootable and have you configured your BIOS to boot from the USB device?

---

