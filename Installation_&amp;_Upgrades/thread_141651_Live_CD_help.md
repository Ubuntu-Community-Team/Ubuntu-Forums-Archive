---
title: "Live CD help"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by LostAngel on 2006-03-08
Hello, I just put the live cd in...and restarted my pc...the UBUNTU Splash screen appears, and says "Boot".  I hit enter, and it says the following:

LOADING/INSTALL/VMLINUZ..........
LOADING/INSTALL/INITRD.GZ........

Then the screen goes black...and a few seconds later it says:

Uncompressing.....OK Booting from Kernal....

Then my computer restarts....and goes back to the UBUNTU splash screen...this cycle happens every time I try this.  I have also noticed when I tried installing CentOS...it did the same thing....

---

### Post by Princey on 2006-03-08
Did you try checking to see if your Live CD's are burnt properly or the downloaded ISO file isn't corrupted? The ISO files do have a md5 check sum that you can use to verify that. Even if you may have a properly downloaded iso file, it could be a faulty burn.

---

### Post by LostAngel on 2006-03-08
I've burned a few copies of the iso's...they work on other computers...but not this one.

---

### Post by Princey on 2006-03-08
[QUOTE=LostAngel]I've burned a few copies of the iso's...they work on other computers...but not this one.[/QUOTE]


It could be then a faulty CD ROM drive. Got another that you can swap in it's place and try?

---

### Post by LostAngel on 2006-03-08
I have 2...an internal and external...they both do the same.  I have never had a problem booting windows from either of them...or installing anything...

---

### Post by Princey on 2006-03-08
[QUOTE=LostAngel]I have 2...an internal and external...they both do the same.  I have never had a problem booting windows from either of them...or installing anything...[/QUOTE]


What Video card are you using?And have you tried another boot cd besides the two you mentioned? It could be your video card that's causing this.

---

### Post by LostAngel on 2006-03-08
It's an integrated card on this pc:

Intel 82845G/GL/GE/PE/GV Graphics Controller

---

### Post by Princey on 2006-03-08
Not sure about the card but I'm out of ideas. Just trying to help. However, you didn't mention if you tried booting from the other CD Drive. H

---

### Post by LostAngel on 2006-03-08
I've tried with my various drives...and also various cd's...this is wierd...i really wanna try ubuntu lol

---

### Post by Princey on 2006-03-08
You said earlier that the CD's work on other computers. Can't you try using the live CD on another computer and see for yourself?

---

### Post by HokeyFry on 2006-03-08
I had the exact same problem. Just pass "live acpi=off" as a boot parameter. If you decide to run the installation CD, and you have the same problem, just change the word "live" to "linux".

---

### Post by LostAngel on 2006-03-09
Princey: Yes it works on other pc's (I have tried).
HokeyFry: I'm not at my home PC at the moment, but will try after work.  What exactly does that command do? I googled, and it said theres a chance my sound won't work?

---

### Post by LostAngel on 2006-03-10
Hey, I tried that boot paremeter and it worked great.  The only problem I found is...my modem doesn't work with Ubuntu as it's a win modem. :(

---

