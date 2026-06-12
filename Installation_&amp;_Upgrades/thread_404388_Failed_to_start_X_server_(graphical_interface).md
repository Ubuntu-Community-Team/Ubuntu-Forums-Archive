---
title: "Failed to start X server (graphical interface)"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by ShamaJamms on 2007-04-08
I had Windows XP on an old machine, but just recently converted it to Ubuntu server edition. When I start it up, I'm given the Ubuntu boot menu screen, where I can choose to start it. However, when I start it up, the screen appears to be a terminal, where I can type. But then it goes blank. About a minute later I will get a message saying that my X server failed, and I get a Fatal server error: no screens found.

The text terminal allows me to type, but wont respond to any command.

---

### Post by zvacet on 2007-04-08
go to the recovery mode and type
```
dpkg-reconfigure xserver-xorg
```

---

### Post by I'm_pissed on 2007-04-08
also press alt+F1 to get to a prompt then type the 'sudo dpkg-reconfigure xserver-xorg'.

After the reconfigure window opens choose vesa as your driver, instead of ati of nvidia or whatever.

---

### Post by sdrawkcab on 2007-08-14
Ok. I'm having the same problem here but I have a slightly different case.

You see, I just recently started building a computer out of spare parts and whatnot. Well. The motherboard that I have installed had the VGA ripped out by an idiot. So, I got a PCI slot VGA graphics card. I tried just switching the video card to "vesa", but I got the part where I select the bit amount to display and it opens up a terminal on the bottom of the screen with the message:

"xserver-xorg postinst warning: overwriting possibly-customised configuration
        file; backup in /etc/X11/xorg.conf .20070815010623"

Now, I don't know what to type or anything. It just has the prompt sitting there after that, and I tried "sudo reboot", but no dice. I think that the problem must be with the PCI settings or something...

---

### Post by merlinus on 2007-08-14
Have you tried Ctrl-Alt-F1 at that point?

-merlin

---

### Post by sdrawkcab on 2007-08-16
> **merlinus said:**
> Have you tried Ctrl-Alt-F1 at that point?

-merlin

Yep, I just tried it, and it just doesn't respond to it at all...

---

### Post by merlinus on 2007-08-16
What about Alt-F1?

-merlin

---

### Post by dabl on 2007-08-16
Try this: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)


Basically, you have to answer "NO" on that first screen where it asks about auto-detecting the card.

---

### Post by merlinus on 2007-08-16
What about Alt-F1, or Ctrl-Alt-Backspace?

-merlin

---

### Post by kraylus on 2007-08-16
> **sdrawkcab said:**
> Ok. I'm having the same problem here but I have a slightly different case.

You see, I just recently started building a computer out of spare parts and whatnot. Well. The motherboard that I have installed had the VGA ripped out by an idiot. So, I got a PCI slot VGA graphics card. I tried just switching the video card to "vesa", but I got the part where I select the bit amount to display and it opens up a terminal on the bottom of the screen with the message:

"xserver-xorg postinst warning: overwriting possibly-customised configuration
        file; backup in /etc/X11/xorg.conf .20070815010623"

Now, I don't know what to type or anything. It just has the prompt sitting there after that, and I tried "sudo reboot", but no dice. I think that the problem must be with the PCI settings or something...

ok, so you were the midst of an install, it started to config your xorg.conf and it looks like in the process of restarting it, it crashed everything

so? start back up in commandline mode and roll up your sleeves. open  up /etc/X11/xorg.conf and change the video driver from whatever it is (e.g. nvidia, ati) to vesa.

then do sudo /etc/init.d/gdm restart

that should get you on track.

if it already is set to vesa and still not working, change it to something else that better suits the generic pci card you have in there.

---

