---
title: "Upgraded to Saucy, now cannot start GUI interface"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by bswilson on 2013-10-29
Friends,

I recently performed an inline upgrade from 13.04 to 13.10. My Ubuntu desktop is one I built a couple of years ago. Usually that spells "sketchiness", but this computer has been running the last 3-4 Ubuntu releases with no major issues for some time. 

Anyway, I have an NVIDIA GeForce 8400 GS Rev 3 video card, as verified by the output of **lspci -vnn |grep VGA**. According to NVIDIA and to various Ubuntu PPA documents, that means I can run the NVIDIA 319 (stable) or 331 (beta) driver sets. However, I can't get either of these to work. I've also tried to install nvidia-current but that is showing me no love. Right this second, the output of **dpkg -i |grep -i nvidia** confirms that I only have the 331 driver installed and enabled. 

So my X server does start, but it seems to hang and stays on a black blank screen. Can someone recommend some next steps?

To clarify, when my system boots, I see the following:

1. POST/Grub, no problem
2. Grey screen that says "Ubuntu GNOME" and three dots underneath
3. Black screen
4. NVIDIA Graphics logo (this screen is full color, 24-bit, 1650x1080 so I know that my PCI graphics card is working correctly)
5. Black screen
6. Boot activity showing services and daemons starting
7. Black screen
8. Graphical X interface showing an error message with no Window borders "The system is running in low-graphics mode", then etc. etc. 

I can then click OK and I get back to step 6 above, which seems frozen. From there, I can Cntrl-Alt-F1 to get to a text only login screen. **Help?** 


***Note: **I have also tried installing the package xserver-xorg-video-nouveau, and when I do that I have the same problem but my tty1 session has a higher resolution...*
***Note: **I also attempted to purge and reinstall lightdm and ubuntu-desktop packages. Still no luck. *

---

### Post by sudodus on 2013-10-29
If you have backup, return to 13.04, with end of life is January 2014. So you have a couple of months to go, when you can test if there will be a working driver in 13.10 and also test 12.04 LTS which will be supported until April 2017.

You can test the built-in driver (nouveau) and proprietary drivers in a second drive (USB, SATA, eSATA) whatever is available.

---

### Post by bswilson on 2013-10-29
Thanks for your reply, **sudodus**, but I do not have that kind of backup in place. Yeah, I know, shame on me, but I've never had a display problem this serious with any Ubuntu release.

---

### Post by sudodus on 2013-10-29
Have you tried the built-in driver (nouveau) yet. It works quite well with my nvidia cards (of different age) for basic graphics. But there is no 3D and no VDPAU.

---

### Post by bswilson on 2013-10-30
Yes, I did try that and still no luck.

---

### Post by sudodus on 2013-10-30
Have you tried with ***nomodeset*** and several other boot options (you can have more than one at the same time)? See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

---

### Post by bswilson on 2013-10-30
Truthfully, I was hoping to avoid messing with grub if possible. But after reading the articles you shared, I gave it a shot. I added the following lines to my boot statement, but none of these have worked. I get some different results, but essentially I get back to the same black screen:

[LIST]
[*]vga=800x640
[*]vga=794
[*]nomodeset $vt_handoff
[/LIST]


Perhaps I don't have the combination of tricks right? The above grub commands were added while I was using the nvidia-304 driver. Let me go back to nouveau, and I'll try that with the grub commands, and if that doesn't work I'll try them with nvidia-319 or nvidia-331 (beta).

To be continued...

---

### Post by sudodus on 2013-10-30
Good luck :-)

---

### Post by bswilson on 2013-11-03
Well, I'm sorry to report that I tried every combination of default, binary, external, and experimental video display driver I could verify works with my NVIDIA card, each with multiple combinations of refresh rates and resolutions -- all with _absoluely no luck_. I got varying results but none allowed me to launch the Unity or Gnome 3 interfaces.

So, I decided to get crazy and reinstall Ubuntu 13.10 after backing up my home directory (and other critical files). I decided to **not** keep any of my dot files or evnrinmental/shell variables and start over clean.

I am up and running 13.10 and Unity now; I ended up with the **xserver-xorg-video-nouveau** (1:1.0.9-2ubuntu1) driver on my system and nothing proprietary. I still don't know what happened, but thanks to **sudodus** for attempting to help me. ;)

---

### Post by sudodus on 2013-11-04
Congratulations :-)

You did the right thing. Sometimes some inherited setting (in /etc or a dot file in the home directory) from the previous version will destroy it.

---

