---
title: "Blank screens after applying update to 7.10 BETA"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by trippingbillee on 2007-10-08
Hi Everyone-

I completely wiped a Thinkpad t40 that used to dual boot to WinXP and Feisty. I then installed the 7.10 Beta. It booted fine and everything looked good.After getting in it told me to upgrade the distribution. This took about an hour, and then it rebooted. After the reboot, X won't start. I can get into the recovery console, but startx causes a blank screen that seems to remain forever. Going back and trying to start the earlier kernel does the same thing. 

Any ideas? I've poked around xorg.conf but still am not quite sure what I'm doing in there. The thinkpad has an ATI mobility 7500 card.

Worse case, I'll wait for the official release, but I'm worried that this same issue will occur.

---

### Post by Pumalite on 2007-10-08
Have you tried

sudo dpkg-reconfigure xserver-xorg, choose 'vesa' as the driver, then: startx

---

### Post by calldrin on 2007-10-08
My screen is also  blank after upgrading to 7.10 ;-(
I have a normal boot and everything seems to run OK until I try to select a different screen "desk"
If i select desk #2 or any other desk#, I get a blank screen with just the mouse pointer.
I can move the mouse but can't find anything to select.
The only way I can get out is to do  a manual reboot by using the power button!

Any help?

Thanks,
Chuck
Chico, CA

---

### Post by Nebby on 2007-10-08
@calldrin
What do you mean by select a different screen desk?
If you mean Ctrl+Alt+F[number], that should show a terminal login for F1-6, your default session for F7 and a flashing _ on a black background on anything above F8 unless you've started extra sessions.

---

### Post by calldrin on 2007-10-08
> **Nebby said:**
> @calldrin
What do you mean by select a different screen desk?
If you mean Ctrl+Alt+F[number], that should show a terminal login for F1-6, your default session for F7 and a flashing _ on a black background on anything above F8 unless you've started extra sessions.

There are 4 boxes located on the bottom right side of the desktop.
They are "desk 1 through desk 4"
 When you click on any of them it opens a new desktop window.
This worked fine until I upgraded  ;-(

Chuck

---

