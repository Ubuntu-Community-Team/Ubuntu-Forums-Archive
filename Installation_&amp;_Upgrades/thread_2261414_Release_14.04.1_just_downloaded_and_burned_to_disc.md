---
title: "Release 14.04.1 just downloaded and burned to disc. can't install."
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by Stephen_Irvan on 2015-01-18
I am apparently too stupid for this. I decided I'd give linux a try. so I went to ubuntu.com, and downloaded 14.04.1 LTS 64-bit edition. I burned the iso. I started to install it, and it wouldn't let me do anything with my C: only giving me an option to install Ubuntu on my portable hard drive. I cancelled out, and it rebooted. I logged back into windows, downloaded Debian 7.8 and installed that. That installed fine, but it's giving me all sorts of errors, and some of the people i've talked to has said to give Ubuntu another try. When i put the disc in, the screen flickers for a second, and then loads up Ubuntu, i have mouse control for about 60 seconds before the "desktop" loads, i get a top-bar, with a couple of icons, and the mouse stops working, and well...nothing happens. I thought maybe it was downloading something, or installing something, so i left it alone for 30 minutes and still nothing. Now of course, I can't figure out how to remove debian either. I've got half a mind to just format the drive and start over. Please help me figure out what I need to do to install Ubuntu.

---

### Post by grahammechanical on 2015-01-18
Well, it would help if you gave us some details about the hardware of that machine and any other operating system on it. And more detail on what you see when you try to load the Ubuntu Try session. Saying: "It wouldn't let me do anything" does not help us to help you. At what point does the installer stop being cooperative?

We should get a purple screen with two icons on the bottom of the screen, of a keyboard and a human. At some point the screen may go black for several seconds and the installer investigates the hardware to enable drivers for the hardware. We should also get another purple screen with the word Ubuntu and five or four dots that change colour. Then we should get a screen that gives us the options to Try Ubuntu or Install Ubuntu. If we select Try Ubuntu we should get to the Ubuntu live session desktop with a launcher with icons on the left of the screen and a top panel with application indicators. There should also be an overlay giving information about keyboard shortcuts.

At what point does the session stop letting you do anything?

Regards.

---

### Post by Stephen_Irvan on 2015-01-18
AMD FX-4150 (Quad Core, x64) @ 3.7Ghz, 8GB HyperX DDR3-1866 ram, 300GB Sata2 HDD, 200GB paritioned for Windows 7, and 100GB free (well, currently it's debian, but that's a different ball of wax.) 

As to what happens.... the screen flashes black, and then starts loading drivers. I get the keyboard/human guy thing at the bottom. After a bit, it pops up with this rather cool looking Ubuntu screen. After a few minutes. there's a bar that pops up on top, and it populates with a couple of icons. at this point, I lose mouse control. I'm still active. i'm still running. I was looking for keyboard shortcuts, and I can drop to command line no problem (but I have no idea what i'm doing so I didn't do anything. lol.) but the screen just...sits there. as soon as the icons in the top right corner load, *bloop* the installation hangs. I've redownloaded a fresh copy of Ubuntu, and burned it to a fresh disc, and it still runs into the same problem. 

The problem is, the first I ran it, it *did* pop up the try/install window, and i selected install, and got to picking my partition and it only gave me my portable USB drive as an installable partition, and not the hard drive, so I cancelled the installation, the process shut down, the system turned off. I logged back in, and downloaded debian 7.8 and it installs fine, but other than browsing the internet through iceweasel, everything else gives me errors. 

Now I can't "uninstall" Debian, and I can't get Ubuntu to install. This isn't turning out to be a good idea it seems. (laughs)

---

### Post by efflandt on 2015-01-20
One of the most important things is what video card/chip do you have? In some cases you might need to initially do something while booting the live/install. For example for nvidia you may to press any key during the initil screen (icon of keyboard/mouse at bottome) of the live/install boot and after selecting language, using F6 to set **nomodeset** (by highlighting it and hitting Space bar to select it) then **Esc** back to boot menu. But I am not familiar with whether anything might be required for AMD/ATI video. Someone else would likely know that once we know what video you have.

---

