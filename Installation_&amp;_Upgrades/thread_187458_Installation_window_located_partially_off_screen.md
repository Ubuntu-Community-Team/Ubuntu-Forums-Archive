---
title: "Installation window located partially off screen"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by jago668 on 2006-06-03
Pardon if this has been covered elsewhere but I didn't see a thread with a similar problem.  I made the cd with Ubuntu on it, setup to boot from cd, restarted, and Ubuntu loads up and runs fine.  I am able to get internet connection just fine while running from the cd.  However when I try to use the install icon the installation window that opens is located off partially off screen.  So I cannot go forward in the installation process.  I tried setting the screen resolution to something else, but all that is available is 640 x 480, and the refresh rate is set to something stupid like -140784928.  I am using an ATI x800 card.

I tried following the instructions located at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

However that did not seem to help.  Advice?  Please.

---

### Post by johnc4510 on 2006-06-03
Is it so far off the screen that you can't adjust the actual monitor controls to center the picture? I have done some installs where it was slightly off, but adjusting the monitor controlls made it so I could finish the install.

---

### Post by jago668 on 2006-06-03
Aye, I tried messing with the actual monitor, I tried resizing the window itself, I tried dragging the window so that I could get to the selections.  That is why I was asking if maybe there was something else I could try, that would maybe allow me to change the screen resolution so maybe the window would better fit the screen.  Even if it just pused up to 800 x 600 I think it might be enough to allow me to do an install.

---

### Post by Bellerophon on 2006-06-03
I've got the same problem installing Xubuntu on an older laptop of mine. The installation window won't fit on a 640x480 screen, and I can't find a way to make the graphical desktop larger. I can set the graphics to 800x600 from the boot screen, and it'll be as such until it hits the desktop, for which it won't go larger than 640x480. I had a similar problem with 5.10, just needed to edit the monitor refresh rates into the xorg file, but I can't fix it on a live CD boot; I need to install. I can't install.

Is there no command-line installer like in the previous releases? It seems pretty silly to make the only option a graphical installer that won't work at lower resolutions.

---

### Post by rhoard on 2006-06-08
Hello All,

I am having the same issue.  I am using the ubuntu-6.06-desktop-i386.iso.  Is there a way to kick it into a text mode install?  I have tried Safe Mode, but get the same results.

While running the Beta I was running my display at 1600x1200 with no issues.

I have an AGP Maxtor G400/G450.  I think it is the G400, but I am not sure any more.

The monitor is a NEC MultiSync P1150:
Horizontal 31 kHz to 94 kHz (Automatically)
Vertical 55 Hz to 160 Hz (Automatically)
Resolutions Maximum 1600 x 1200 (75 Hz non interlaced)**
Recommended 1280 x 1024 (85 Hz non interlaced)*

Any ideas would be apprecated.

Best regards,
Richard

---

### Post by rhoard on 2006-06-08
Hi Everyone,

I seem to have figured it out.

On the CD boot menu there is an F option, I think it is F4 for VGA.  I set mine to 800x600x32.  I am now able to see the edge of the buttons and click them though I can not read the text on them.  The farthest right button is the 'next' button.  My system is now installing.

I hope this is helpful.

Best regards,
Richard

---

