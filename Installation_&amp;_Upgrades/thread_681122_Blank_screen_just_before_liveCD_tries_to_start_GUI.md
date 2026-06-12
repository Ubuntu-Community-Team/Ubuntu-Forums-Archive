---
title: "Blank screen just before liveCD tries to start GUI. AMD, nVidia"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Tulainas on 2008-01-28
Hi there!

I´ve been trying to install  U-7.10 on my PC. 
1) I load the installation cd on the cdrom
2) I choose "start or install" with the "noapic" option enabled
3) I hit enter....

 and it starts to load the installer

                   - appears the Ubuntu´s loading bar
                   - the progress bar finishes loading and tries to start GUI and ....

                   - I GET AN ANNOYING BLANK SCREEN!!!!! 
                       * monitor just enters into power-save mode
                       * terminals tty1 - tty8 ( ctrl+alt+F1...F8 ) work correctly; 

The point is, that I cannot see anything (as you may suppose). So, I cannot install U7.10.

I had previously U7.04 and had no problem at all.

DOES ANYBODY HAVE ANY SUGGESTIONS?

Thanks!!

My PC specs are:
AMD athlon X2 4600+ (2.4 Ghz dual core)
1 Gb  DDR2 RAM
MOBO asus M2N-MX SE with integrated video nVidia 6150SE

---

### Post by Rocket2DMn on 2008-01-28
There should be a safe graphics mode (hit F6 or something like that).  If that doesn't work, you can use the alternate install cd which doesn't have a live session - it's just a text based installer which works really well.  Just go to the website and check the box at the bottom for Alternate Install CD - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
If you have problems with the GUI after install, let us know and we'll troubleshoot that (it's not a tough fix).

---

### Post by Tulainas on 2008-02-01
Thanks!, but I'm sure there should be another way to solve it. I've got a slow internet connection, it may take some time, but, I will try anyway. 

Please if you know about some other solution please give me a call.., thx

---

### Post by Partyboi2 on 2008-02-01
what happens if you change to a terminal and type
```
startx
```

---

