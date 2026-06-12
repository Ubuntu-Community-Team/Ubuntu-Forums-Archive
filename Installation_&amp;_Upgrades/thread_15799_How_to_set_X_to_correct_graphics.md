---
title: "How to set X to correct graphics?"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by Imagist on 2005-02-16
I finally got my install to work.  But I accidentally set the graphics to a higher screen size (1024 by 800) than I actually have (1024 by 768).  Now it won't let me access the graphical user interface.  How do I reset the graphics to the correct values from the text console version?

---

### Post by Buffalo Soldier on 2005-02-16
Are you using Warty or Hoary? If Warty you can try **sudo dpkg-reconfigure xserver-xfree86**.

---

### Post by Imagist on 2005-02-16
I'm using hoary.  But I'll give that a try.

---

### Post by slackerj on 2005-02-16
Another way to do it would be like the following:

sudo nano /etc/X11/XF86Config-4
Password: (enter in your password)

Nano will start. Scroll down (using the directional keys) till you get to:

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

Now scroll further down till you get to each screen depths subsection and change "1024x800" to "1024x768".

Once you have done that press "ctrl" and then "x" and then "y" to save the changes. 

When nano exits, type:

startx

Things should now work (I hope :D )

---

### Post by Imagist on 2005-02-17
Buffalo's advice didn't work, so I reinstalled Linux, this time choosing the correct settings at install.

However, it still didn't work.  I got the same error.

I just followed slackerj's advice.  I opened the file successfully with nano, but it was empty.

Is there something I should call to generate the file, or should I type in some info?  It seems to be attempting to load X at startup, so if I can populate the file correctly that would probably fix my problem.

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=Imagist]Buffalo's advice didn't work, so I reinstalled Linux, this time choosing the correct settings at install.

However, it still didn't work.  I got the same error.

I just followed slackerj's advice.  I opened the file successfully with nano, but it was empty.

Is there something I should call to generate the file, or should I type in some info?  It seems to be attempting to load X at startup, so if I can populate the file correctly that would probably fix my problem.[/QUOTE]

I saw you are using Hoary, so this is not XF86Config but /etc/X11/xorg.conf you have to edit. 

Try that.

---

### Post by Imagist on 2005-02-19
I finally got into the GUI by upgrading my BIOS, but I still need to get into the XConfig to set my screen to the correct resolution.  I went to Desktop>Administration>Screen Resolution, but it doesn't show my true screen resolution as one of the options.  How do I get into the settings from the GUI?

---

