---
title: "Live-USB via unetbootin doesn't show bootloader on external monitor"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by Chowlz on 2014-03-07
I have a laptop that has a broken screen. Luckily, when I boot up, I was able to see grub still through my external monitor (VGA). I wanted to create a live-USB to play with the beta via unetbootin, but when I did, the bootloader doesn't show up on my external monitor and waiting doesn't do anything (I tried waiting and then increasing the brightness, but it didn't do anything). My monitor doesn't pick up a signal from my laptop. Is there a way to create a live-USB with or without unetbootin so it'll work and show on my external monitor?

---

### Post by sudodus on 2014-03-08
Welcome to the Ubuntu Forums :-)

You can create an 'installed system' on your USB drive and make your computer boot from that instead of the internal drive. If you have problems modifying the boot order in BIOS, you can disconnect your internal drive. Then the computer will probably find your USB drive and boot from it.

It is probably easiest to create and test the installed system on the USB drive in another computer (if you have one). But it should work using the external monitor too.

What operating system and version is there in the laptop (Ubuntu or Windows or Mac OS)? And what computer is it? Please specify the details, it makes it easier for us to help.

- Computer brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Current operating system and version

---

### Post by Chowlz on 2014-03-09
I currrently have Gnome Ubuntu 13.10 installed. Grub shows on my external monitor even though my laptop screen is broken. Before, my laptop would boot Ubuntu using both screens, using the laptop screen as the primary monitor. I was able to fix it by adding "video=LVDS-1:d". 

Using a live-USB via unetbootin doesn't show anything on my external monitor, not even the bootloader. So I can't edit any parameters.

I don't think my computer details will help but here's what I know:
-HP dm4
-i5-2430M
-8gb
-intel integrated graphics

---

### Post by sudodus on 2014-03-09
So the installed Ubuntu Gnome displays the grub menu, but the live-USB does not. I think Unetbootin uses grub, but probably another version. That might be the problem.

Does it work if you use the Ubuntu Gnome install desktop iso file (the same version as you have installed)? In that case the problem depends on the Trusty beta version.

Is there old style BIOS or UEFI in the computer? Depending on your reply, I would suggest different things.

-o-

Be aware that the version being developed is working rather well, but the daily build might break anytime and several times until the release date. You can download the daily build instead of the beta and hope it works better. If you have problems, you can report them at the testing tracker. See this link

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

write a bug report at Launchpad

[https://launchpad.net/](https://launchpad.net/)

or ask for this thread to be moved to the forum Ubuntu +1, where the version being developed is discussed, and you will find other people who are interested in similar things.

---

