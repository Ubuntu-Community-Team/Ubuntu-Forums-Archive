---
title: "Many problems after installation"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by pbb on 2007-02-17
After playing around with Ubuntu in the past (and giving up after too many problems), I decided to give it a try again, this time on an old computer of ours.

Hardware config:
[LIST]
[*]HP Pavilion 414.no ([http://h10025.www1.hp.com/ewfrf/wc/product?product=306349&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=306349&lc=en&cc=us&dlc=en&lang=en&cc=us))
[*]Club-3D ATI Radeon 9700 All-In-Wonder Pro
[*]CNet CWP-854 Wireless adapter
[/LIST]

BIOS settings:
[LIST]
[*]Internal NIC disabled
[*](Unused) parrallel and serial port disabled
[*]I couldn't find any powersaving settings to disable
[/LIST]

Running the live CD went quite okay, except for two problems:
[LIST]
[*]Only once I was able to get the wireless network connected (though I did exactly the same every time I tried).
[*]The computer locked up on certain screensavers (I think it is the 3-D ones).
[/LIST]

So I decided to install on the harddisk. First boot went okay. Tried once more to get the wireless connected, without success. (I did not modify any config files, just tried to run wireless using the GUI config tool.) After that, I had the following problems:
[LIST]
[*]Boot stops on "Configuring network interfaces". After two minutes, the graphical brownish screen is exchanged for a white-on-black text interface with the same message. Nothing else happens after that.
[*]Pressing Ctrl+C on the line mentioned above, continues the bootup process. After that, I get a graphical login screen. After logging in, I get an empty desktop. The mouse moves, the harddisk light flashes once in a while, but no interface is shown, just a brownish desktop background.
[*]After a while the screensaver kicks in, locking up the computer if it is a 3-D one.
[*]The desktop reacts to me pressing the power button on the computer case. A shutdown process is started, switching a few times between text and graphical interface, to freeze again afterwards in text mode.
[*]Booting in Recovery mode, and breaking the network config with Ctrl+C, ends up in a command prompt in textmode (without need to logon). But I don't really know what to do here.
[/LIST]

Anyone who can help solving some or all of my problems? (Except of course the obvious one: Install MS Windows.) Or is this piece of hardware just to old, will it be more problems than it is worth trying to get Ubuntu to run on this?

Thanks, Peter

---

### Post by pbb on 2007-02-17
No ideas anybody?

---

### Post by eapache on 2007-02-17
Try downloading the Dapper or Edgy CD and reinstalling. The newer versions will probably work, and at least give a helpful error message.

---

### Post by pbb on 2007-02-18
I am using 6.06 (can't find info on if that is Dapper or Edgy, it doesn't say on the CD).

I have now removed both the AIW and the wireless, and Ubuntu didn't want to boot at all anymore, complaining something about missing files.

So I decided on re-installing. I get as far as the partition manager, where I select to re-use the existing swap and linux partitions, with the default of re-format those partitions selected. After confirming those choices, I see partition manager come up again for a short moment, and some CD activity, after which the computer freezes. Even the mouse doesn't move anymore.

I am used to quite some buggy software under Windows, but this really takes the crown...

---

### Post by eapache on 2007-02-18
OK, the thing beneath your bean count says you're still running breezy :) (6.06 is dapper)

Do you have another OS installed on which you can test your hardware? Otherwise, try reinstalling again, and move very slowly (wait for everything to finish working before clicking 'next'). It's quite possible that you just overloaded it.

What are your specs (processor and ram)? the website didn't seem to show them...

---

