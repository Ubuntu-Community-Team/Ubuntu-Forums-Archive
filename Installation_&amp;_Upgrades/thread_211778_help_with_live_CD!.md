---
title: "help with live CD!"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by lee78221 on 2006-07-08
when I use the live cd I see  Xserver fails but I see this hread [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177) and does it have to do with anything I am doing with the live CD? 

it says to Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

I do not see GRUB menu(I do not even know what that is?!:confused: 


I am very new at this please help.

---

### Post by scxtt on 2006-07-08
that only pertains to an INSTALL of ubuntu - nothing to do w/ the liveCD ... have you tried "safe graphics" mode -- are you sure you have the "desktop" cd?

btw, grub is a 'boot loader' - so that you can start the OS from the HDD ...

---

### Post by lee78221 on 2006-07-08
> **scxtt said:**
> that only pertains to an INSTALL of ubuntu - nothing to do w/ the liveCD ... have you tried "safe graphics" mode -- are you sure you have the "desktop" cd?

btw, grub is a 'boot loader' - so that you can start the OS from the HDD ...

I got this cd from the order at Ubuntu(so I think I have the right one) and I have  tried "safe graphics" mode and still the same thing.

---

### Post by scxtt on 2006-07-08
what video card do you have? -- are you at least dropped to a command line? -- if so, can you type **startx** and post the errors?

---

### Post by lee78221 on 2006-07-08
> **scxtt said:**
> what video card do you have? -- are you at least dropped to a command line? -- if so, can you type **startx** and post the errors?

I have a Intel(R) 82845G/GL/GE/PE/GV, all I see is a window with error message: Unable to start X server,And next I see scatter text all over the screen.

---

### Post by lee78221 on 2006-07-09
anyone?

---

### Post by confused57 on 2006-07-09
Not sure if it'll work, but when you get to the error screen, try pressing Ctrl+Alt+F1...this hopefully will get you to a console prompt.  If it does, I think for the live cd you enter Ubuntu for the username, then just press "enter".

If by chance the above works, enter:
```
sudo dpkg-reconfigure xserver-xorg
```
I'm not sure if you need sudo using the live cd.

If this somehow works, you'll get a screen asking if you want to autodetect your monitor settings...select "no". You're probably safe to select the default settings for everything, until you get to the drivers section...you can try different drivers, starting with "vesa".  You might want to do a Google search, entering in your video controller and linux as keywords and see if there might be any info for which Linux driver to use. Did a search and saw someone tried "i810", which I suppose is a driver option.

At a console command prompt, enter   **startx**
press enter, if everything miraculously configured correctly,
this should start the GUI.

---

### Post by lee78221 on 2006-07-09
> **confused57 said:**
> Not sure if it'll work, but when you get to the error screen, try pressing Ctrl+Alt+F1...this hopefully will get you to a console prompt.  If it does, I think for the live cd you enter Ubuntu for the username, then just press "enter".

If by chance the above works, enter:
```
sudo dpkg-reconfigure xserver-xorg
```
I'm not sure if you need sudo using the live cd.

If this somehow works, you'll get a screen asking if you want to autodetect your monitor settings...select "no". You're probably safe to select the default settings for everything, until you get to the drivers section...you can try different drivers, starting with "vesa".  You might want to do a Google search, entering in your video controller and linux as keywords and see if there might be any info for which Linux driver to use. Did a search and saw someone tried "i810", which I suppose is a driver option.

At a console command prompt, enter   **startx**
press enter, if everything miraculously configured correctly,
this should start the GUI.
I look it up and it is the i915 is that driver in Ubuntu?

---

