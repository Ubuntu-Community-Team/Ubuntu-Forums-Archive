---
title: "Usplash/grub fail to set resolution"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by invictus on 2007-06-27
Hi

I have a dell inspiron 510m laptop with intel extreme graphics 2. The max screen resolution on this machine (which works as intended in gnome/xorg) is 1024x768. However, Usplash fail to set the resolution to this when displaying the splash screen on start. Because of this Usplash falls back to 640x480 and everything looks butt-ugly and out of place. Any idea how I can fix this? I tried setting the vga parameter in grub's menu.lst with the same result.

Once I pressed ctrl-alt-del during boot to reboot the machine (was going into the bios config, but forgot to press in time) and then usplash died and showed me a message saying exactly this: that Usplash failed to set the resolution to 1024x768, 800x600, and therefore fell back to 640x480.

Not sure whether or not I had this problem with earlier releases.



When trying to pass the vga=0x317 parameter in grub.conf I get the following screen after the grub screen has finished:

You passed an undefined mode number.
Press <RETURN> to see video available. <SPACE> to continue or wait 30 secs

Video adapter: VESA VGA
Mode: COLSxROWS
0 0F00 80x25
1 0F01 80x50
2 0F02 80x43
3 0F03 80x28
4 0F05 80x30
5 0F06 80x34
6 0F07 80x60

Enter mode number or 'scan':



----

UPDATE: used the hwinfo --framebuffer to find out what modes my machine supports...0x317 was listed there...so obviously someone are lying.

---

### Post by dabl on 2007-06-27
As far as I know, both the Grub menu and usplash are 640 x 480 screens, regardless of your graphics chip/card -- they are presented prior to running the x server, and must assume the lowest possible resolution, I guess.  Here's more, if you're interested:

[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

:)

---

### Post by invictus on 2007-06-28
Well, several other machines I have used running Ubuntu does not seem to have the same problem. It should be possible to run higher resolution usplash screen, but it is not on my machine apparently.

---

### Post by invictus on 2007-06-29
Sorry for the bump, but I would really like to know this. I am showcasing ubuntu for some friends and need it too look good...

---

