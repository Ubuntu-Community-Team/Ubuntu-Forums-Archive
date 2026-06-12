---
title: "Ubuntu won't install or run LiveCD..Help plz"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by barrym07 on 2007-08-29
I'm new to Linux and decided to use Linux instead of Windows. I built a a new system:
MSI K9N Platinum mobo
AMD Athlon 64x2 6000+
nvidia 8600GTS 256mb PCI EXP.16
4 Gigs Ram
500 GB HDD

When ever I try and install from the bios screen I loose my video so I can't tell if its doing anything. I tried several times and no luck, so I just installed Windows XP from a disk that I had. Does anyone know how I can fix this or have any suggestion would be great.

---

### Post by Pumalite on 2007-08-29
When ever I try and install from the bios screen
Can you explain this better?
Have you tried Alternate CD?: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below 'Start Download'

---

### Post by barrym07 on 2007-08-29
When you first start the computer up, on my board I push F11 to select where to boot from if i want to change it. No I haven't tried to alternative CD, also which version should i get x86 or x64? I want to take full advantage of my computer's capabilities.

---

### Post by Pumalite on 2007-08-29
Go for x64 if you want, but there are certain limitations. I'm not a x64 user, but you could search the forum. Your card might be a problem too. Do a search on it.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by barrym07 on 2007-08-29
Thank you for the help, I will try those.


I looked at the graphics cards that are on the list from tht link, I didn't see mine, my mobo doesnt have onboard video is that bad??

---

### Post by Pumalite on 2007-08-29
NO, that's good, Good luck.

---

### Post by barrym07 on 2007-08-29
Okay, so i installed with alt cd, and i starting step 2(reboot) so i rebooted and now i lost video again.

---

### Post by Pumalite on 2007-08-29
At the command line ( Ctrl+Alt+F1):
sudo dpkg-reconfigure xserver-xorg. Choose most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by barrym07 on 2007-08-30
Thank you so much for your help. You don't know how much I appreciate that information. It works now!!!!!

---

### Post by merlinus on 2007-08-30
Choose Recovery Mode from the install cd menu.  It should get you to a command line where you can enter what Pumalite suggested.

-merlin

---

