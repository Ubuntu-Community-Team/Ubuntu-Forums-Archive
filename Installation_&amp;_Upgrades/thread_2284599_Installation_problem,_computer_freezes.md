---
title: "Installation problem, computer freezes"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by Tuber1221 on 2015-06-30
I'm having problem installing Ubuntu on my laptop, when I try installing with an USB, the computer freezes entering GUI for installation. And with wubi, the installation has an error. 
I've read other post and it might be a problem with the graphic card (Nvidia K5100m) but I couldn't solve it.

---

### Post by Bashing-om on 2015-06-30
Tuber1221; Hello ; Welcome to the forum.

WUBI is no longer supported, so that option is not under consideration.

Install process :
verify the .iso;
verify the burn to USB
Boot up the liveUSB -> soon as the bios screen clears depress and hold the right - shift - key -> language screen; escape key to accept the default -> boot options screen ( check disk for defects ) -> F6 key for boot options parameters, select "nomodeset" ctl+x to continue the boot process. If this works to boot up in "try ubuntu" mode, then use this setting when installing the ubuntu operating system.
At a later time when the install completes an appropriate driver for the graphics can be installed.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-06-30
You do not say what version of Ubuntu you are using. Does the Live session load to a desktop? The live session uses an open source driver. When we install and tick to also install third party software we also get a proprietary video driver.

So, there are two questions. 1) Does the open source video driver in that version of Ubuntu have support for the Nvidia Quadro K5100M adapter. 2) Does that version of Ubuntu have the newest Nvidia drivers that support the Quadro K5100M adapter?

According to the Nvidia web site Linux drivers 346.59, 347.25 and 352.21 have support for Quadro K5100M. But Linux driver 344.65 does not support the Quadro K5100M. As far as I can tell.

I think that Ubuntu 15.04 has a Nvidia 346 series driver but I am not sure. But as for the other ones, I cannot say. My Nvidia adapter is now classified by Nvidia as requiring a legacy driver. The latest Nvidia drivers do not support my adapter. So Additional Drivers no longer shows me the latest available Nvidia drivers even though I am running the 15.10 development version. And I know of no other way to find out what drivers the latest versions of Ubuntu are carrying.

You might need to be installing Ubuntu 15.04 or even Ubuntu Wily Werewolf (15.10) that is still under development to get more up to date video drivers. Both of the open source kind and the proprietary kind.

Regards.

---

### Post by Tuber1221 on 2015-07-16
Thanks for the help.

I'll try both options an tell you how it goes.

---

### Post by Tuber1221 on 2015-07-20
I tried to follow your steps but it didn't go well, I checked the installation guide and I didn't have the same initial screen, instead I have this one:
[IMG]http://i.imgur.com/I9bzE.jpg?1[/IMG]

Does this mean something?

---

### Post by mörgæs on 2015-08-12
Exactly which options have you tried?

---

### Post by Tuber1221 on 2015-08-12
First, I tried to install Ubuntu 14.04 LTS via wubi, the installation was successful, but when I tried to enter Ubuntu the computer freezes in the loading screen. Only one time I could access to the desktop but after 1 minute the computer freezes again, The only different thing was that when the computer freezes in the loading screen, I have been using the computer for a long time, and the only time I access the desktop, was a cold day and was just starting the computer.

After that I tried to install via USB an I got the screen I showed, never have the screen showed in the guide. Whatever option than needs GUI (test or installing) the computer freezes in the loading screen.

Then I friend of mine give a CD from an old Ubuntu (9 I think, I don't remember well) and the computer worked well, but it was 32-bit and Ubuntu didn't let me update to a 64-bit OS (which I need for my work).

Finally I download Ubuntu 15.04 and the problem was the same with the 14.04 via USB.

---

### Post by mörgæs on 2015-08-13
What about Lubuntu 15.10 (beta) as mentioned in post 3?
You can download it here: [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by Tuber1221 on 2015-08-19
> **mörgæs said:**
> What about Lubuntu 15.10 (beta) as mentioned in post 3?
You can download it here: [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Sorry I forgot the try this, Only tried with 15.04, I'll let you know how it goes!

---

### Post by Tuber1221 on 2015-08-26
The same :( I get the same initial screen and stop working in the loading screen.

---

### Post by Tuber1221 on 2015-08-26
The same :( I get the same initial screen and stop working in the loading screen.

---

### Post by mörgæs on 2015-08-28
During installation did you get the option to install additional / closed-source drivers?

---

### Post by Tuber1221 on 2015-09-22
Even with Lubuntu I'm having the same problem

---

