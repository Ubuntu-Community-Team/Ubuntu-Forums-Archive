---
title: "Problems installing Xubuntu x64 via LiveCD"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by SBFC on 2007-03-01
Has anyone had problems installing Xubuntu (or any of the others) on a newer system with the LiveCD? I've done some searching and seen threads about ppl having problems installing via LiveCD's because of older systems, but not newer.

I'm downloading the alternate cd right now to try that out...just wish I knew why the LiveCD was giving me so much trouble. It gets to the point of actually starting XFCE and then just freezes. I can still move the mouse cursor, nothing else responds though.

2.2 Ghz 64
2 Gig RAM
Nvidia 7800 GT OC
Asus A8N-SLI (only one gpu though)

Why in the world would this setup not be able to load XFCE? Seriously.

Just wondering if anyone else has had a similar experience. Hopefully the alternate cd will work. *crosses fingers*

---

### Post by Kateikyoushi on 2007-03-01
Because it can not handle your VGA or something on the mobo.

---

### Post by SBFC on 2007-03-03
Bad news...I successfully installed Xubuntu from the alternate cd...

However, upon logging in XFCE behaves the same way as the LiveCD did...can move the mouse, but everything else locks up. Can't switch to tty, can't kill the xserver. I get the nice XFCE blue background, and part of the taskbars..weird lines across the screen where the toolbars are though...

:(

I decided to switch to a tty at the login screen and install fluxbox. Restarted gdm, clicked 'Session' and the dialog pops up...full of lines, can move mouse, cannot kill xserver or switch back to tty, have to reboot. Arg...

Gonna try and find out which file stores the chosen WM to load and set it to Fluxbox to see if I flux even works...

Has anyone else had this problem? Kinda sad right now...was excited to set my new system up. :P

Suppose it'll be some forum digging for a while.

---

### Post by Kateikyoushi on 2007-03-03
Did you try to install your video card ?

---

### Post by SBFC on 2007-03-03
Haven't checked yet, I'll do that now.

When I installed Xubuntu x32 on my older machine the nvidia drivers were installed out of the box.

Also, when the system is booting after the message 'Uncompressing linux kernel' (or some such) the Xubuntu load screen is not displayed, just a black screen til gdm starts up.

I'll check into my vid card though...

---

### Post by Kateikyoushi on 2007-03-03
I think those default drivers are not capable of handling your vga, those are not made by nivida, what was the video card in the other machine an older model right ?

---

### Post by SBFC on 2007-03-03
Thank you very much for your suggestion. The nvidia drivers were indeed NOT installed. Can login to XFCE no prob now.

Are the drivers not being installed by default a difference between the LiveCD and the alternate cd?

I also notice that my wireless card isn't setup (not a problem as I'm right next to my router) whereas on my x32 system it was setup right after installation (using a livecd).

---

### Post by SBFC on 2007-03-03
Graphics card in the older machine is an Nvidia also, GeForce 5600 FX.

---

