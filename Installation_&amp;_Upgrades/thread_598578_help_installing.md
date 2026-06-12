---
title: "help installing"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Medec5 on 2007-10-31
hey, im running a old hp with a intel celeron with a ati radeon 9200 trying to install ubuntu, and i keep getting the server x fail error, i can run the setup utility for to set up my video card and it wants to use my intergrated video card instead of my ati even tho i tell it to use ati radeon 9200, how can i fix this, and after i finish the setup i need to know how to restart the gdm (if that is what its called im new to linux) so i can install it.. any help would be very apprecatied thank u

---

### Post by dabl on 2007-10-31
You need to get into BIOS (aka "Setup") and disable the onboard video, probably.

Then you may need to set up a VESA display first, if the installer doesn't correctly autodetect the ATI card. If you can get to a console prompt and log in,
```

sudo dpkg-reconfigure xserver-xorg
```

choose "NO" on the first question about autodetecting, then choose "VESA" for the display type, then mostly you can take the defaults the rest of the way through.  When you finish it will dump you back to the text prompt.  You can enter

```
startx
```

and you should get a GUI.  Then if it were me I would download the Envy installer.  You want this file:

envy_0.9.8-0ubuntu10_all.deb

from this web site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

When it is downloaded, right-click it and install it with Gdebi.  Then you can open a console and enter ```
sudo envy -t
``` to run it in text mode.  It gets pretty obvious what to do after that.

:)

---

### Post by Medec5 on 2007-10-31
cool thank u i will give that i try.. i know i went into the bios and there is no disable i can only set my on board to 1 or 8 meg video which i thoght was really strange but thank i will let u know if this works out

---

### Post by dabl on 2007-10-31
If you can find an online spec for that HP mobo, you might find that there is a jumper to enable/disable the onboard video.  :)

---

### Post by Medec5 on 2007-10-31
its telling me fatal server error no screens found 

XIO: fatal IO error 104

---

### Post by Medec5 on 2007-10-31
any ideas anyone??? thank u

---

