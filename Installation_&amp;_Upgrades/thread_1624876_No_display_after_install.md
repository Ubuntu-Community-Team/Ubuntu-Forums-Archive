---
title: "No display after install"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by ash369 on 2010-11-18
I just installed Ubuntu using wubi. The installtion went well but when i select to load Ubuntu nothing shows up on the screen. All that happens is my monitor switches from digital to analogue and then to hdmi, it just keeps doing that.

How can i fix this?

---

### Post by bcbc on 2010-11-18
what graphics card do you have? Some require a workaround to get ubuntu to boot. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ash369 on 2010-11-18
I have an ATI Radeon HD 5700.

Should i add the nomodeset option to the kernal boot?

---

### Post by bcbc on 2010-11-18
You could try that... then once booted, go to System, Adminstration, Hardware drivers and see if there is a custom driver available.

---

### Post by sikander3786 on 2010-11-18
> **ash369 said:**
> .....
Should i add the nomodeset option to the kernal boot?
And if **nomodeset** doesn't work, try **radeon.modeset=0** instead.

---

### Post by ash369 on 2010-11-18
Neither of them worked.

All that happens is a splash screen comes up for a few seconds, a sound plays, and then the screen goes blank and it does the same as before. Switches from analogue to digital and then to hdmi.

---

### Post by bcbc on 2010-11-18
There've been problems with certain graphics cards since Lucid introduced Plymouth. Nomodeset worked for me, but I have an older ati card.

What computer brand/model is it? Sometimes you can find solutions easier that way...

---

### Post by freshmeatz on 2010-11-18
might wanna check this post see if it offers some information for  you.

[http://ubuntuforums.org/showthread.php?t=1467809](http://ubuntuforums.org/showthread.php?t=1467809)

check post #10

---

### Post by bcbc on 2010-11-18
> **freshmeatz said:**
> might wanna check this post see if it offers some information for  you.

[http://ubuntuforums.org/showthread.php?t=1467809](http://ubuntuforums.org/showthread.php?t=1467809)

check post #10

I thought of that but unfortunately doesn't work for wubi installs. 

However, it might be the best approach if you want to get Ubuntu working. 
(Also Wubi is good for trying out ubuntu but if you end up using it long term a direct install is better)

---

### Post by ash369 on 2010-11-18
Ok, got it working. I had to start it in recovery mode using the **nomodeset** option in the command line. Then i had to boot in low-graphics mode and install a more updated driver. Only problem i have now is that the desktop does not fill the screen.

The resolution is set to 1920 x 1080 which is what i use in windows 7. I actually had the same problem in Windows and had to use the ati catalyst control center to fix it. What should i do?

---

### Post by freshmeatz on 2010-11-18
Good tip on Wubi installs, seems it works best as a test run or temporary solution, but very unstable for long term.

---

### Post by ash369 on 2010-11-18
Fixed the display now.

Went to System -> Preferences and found Catalyst Control Center, then went on the display manager and to adjustments and turned overscan to 0%.

---

### Post by freshmeatz on 2010-11-18
grats I can say this is probably solved . more like a glitch and not a bug, but got squashed either rate,,

---

### Post by raymondvillain on 2010-11-19
I upgraded from 10.04 to 10.10 and have lots of graphics problems.  I have ATI Radeon 3200 HD graphics built into the motherboard.

How does one use the "nomodeset"?

Originally had no display, then booted to recovery mode and used low graphics, installed the "ati-driver-installer-11-x86.x86_64.run" using the sh command line from a terminal window.

But now when I try to launch the catalyst control center I get an error message,

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.


Now Google Earth won't function at all, and I cannot logout or switch user, I have to reboot.
Any ideas?

---

