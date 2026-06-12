---
title: "Try to install"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by crazy bird on 2011-10-31
Hi all,
 
Yesterday i tried to install Xubuntu 11.10 on 1 of my systems. The installation itself went smoothly but after rebooting the problem started.
 
After rebooting, the bootscreen appears and then my screen blinked a few times and some lines appears. And at that moment, the startup procedure stops. Just a few lines nothing more.
 
Rebooting my system doesn't help either, the boot procudere stops rigth after when i see the bootscreen. 
 
Does anyone knows what the problem migth be?
Many thanks!

---

### Post by Quackers on 2011-10-31
Which graphics card are you using? 
You may need to use a boot option such as nomodeset until the proper video driver is installed.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by crazy bird on 2011-10-31
This is my videocard:
> VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

My system:

> 
CPU: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz

Motherboard: Asus P5KPL-AM SE

System memory: [FONT=monospace]4 Gib

[/FONT]   	 	 	 	pre { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }


---

### Post by Quackers on 2011-10-31
Try the nomodeset option as described in that link.

---

### Post by crazy bird on 2011-10-31
> **Quackers said:**
> Try the nomodeset option as described in that link.

Where can i set that? Is it at the beginning when i have to choose my language?

---

### Post by Quackers on 2011-10-31
When booting from the hard drive tap the Esc key. This should bring up a grub menu. The top item shown should be your Xubuntu system. If that entry is highlighted press the "e" key.
On the next screen using the arrow keys navigate to the end of the Linux line which currently ends with "quiet splash". Using the back space key erase those two words then type in "nomodeset" (but without the quotes).
Then press ctrl + x to boot.
Please report what happens then.

---

