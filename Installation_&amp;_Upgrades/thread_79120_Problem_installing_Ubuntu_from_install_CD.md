---
title: "Problem installing Ubuntu from install CD"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by Timmeh on 2005-10-19
Well, I've decided to give Ubuntu a try. I have made all the necessary changes in my system's BIOS (making the CD-ROM drive to boot first before anything else), defraged my Windows drive, backed up my data, etc. 

But when I load the Ubuntu install CD, I get the main splash page (press 'Enter' to begin the install) and then it just restarts. Anyone know what I may have done wrong?

---

### Post by manicka on 2005-10-19
you may have a faulty cd. Try burning new one on a slower speed

---

### Post by Timmeh on 2005-10-19
I didn't burn this CD, I ordered it.

---

### Post by Timmeh on 2005-10-20
I'm guessing I can't fix this?

---

### Post by manicka on 2005-10-20
Try it with the acpi=off option

---

### Post by Timmeh on 2005-10-20
[QUOTE=manicka]Try it with the acpi=off option[/QUOTE]
Where do I turn that off?

---

### Post by Timmeh on 2005-10-21
Nevermind, I'll just stick to Windows.

---

### Post by aLc on 2005-10-22
try this ,write "linux noapic" before press "enter" to begin installation

---

### Post by Timmeh on 2005-10-24
Thanks, I tried that and it works!

Now I have a screen resolution problem. It seems to be stuck at 600x480 (I want it to be set to 1024x768 ). I have tried several solutions (like the dpkg script) but it just messed up my Ubuntu installation (I had to reinstall Ubuntu to get it working normal again). Any suggestions?

---

### Post by taurus on 2005-10-24
What kind of monitor and video card do you have???  Perhaps you need to install a driver for your video card or modify your /etc/X11/xorg.conf...

---

### Post by gamesmad on 2005-10-24
LOL, Im downloading Ubuntu now, I hope its not gonna be like this on my PC....  Good luck with changing your screen res.

Will

---

### Post by Timmeh on 2005-10-24
I have a Compaq 7550, and I have already tried modifying that file...

---

