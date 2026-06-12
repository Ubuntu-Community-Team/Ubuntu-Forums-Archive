---
title: "bcm43xx error"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by NH538DB8 on 2007-10-29
I just installed the recent version of Ubuntu as a dual boot on a Compaq nw8440 laptop (other OS is XP Pro). It would appear that with a little fiddling the installation was sucessful however on the fist boot into ubuntu before any of the actual OS comes up I get slapped with the following error:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

I did some googling and aparrently it is associated with broadcom wireless systems. However when I get this error it stops the loading process and the OS refuses to load. Also when this happens the screen flickers like it is trying to display a splash screen or some type of graphic but it is jumbled and then disappears. This happens almost every time the error is displayed (repetatively). Any help would be appreciated.

Oh I forgot the other screen. It says:

The display server has been shut down about 6 times in the past 90 seconds. It is likely something bad is going on. Waiting for 2 minutes before trying again on display :0.

Yeah its a helpful error message.

---

### Post by Pumalite on 2007-10-29
[http://ubuntuforums.org/showthread.php?t=25683&page=43](http://ubuntuforums.org/showthread.php?t=25683&page=43)
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/page4.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/page4.html)
[http://ubuntuforums.org/archive/index.php/t-297092.html](http://ubuntuforums.org/archive/index.php/t-297092.html)

---

### Post by NH538DB8 on 2007-10-29
So your saying that it is definately an issue with the wireless that is not allowing me to boot and causing the error with the display server?

---

### Post by Pumalite on 2007-10-29
I believe you might have to use the workarounds that I provided. And here is another guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

