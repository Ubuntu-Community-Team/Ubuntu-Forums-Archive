---
title: "How do I restore Ubuntu splash?"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bwallum on 2010-04-12
Hi

I have been trying to restore my Ubuntu splash image, the simple 'ubuntu' text underscored with 5 red/white dots.

I lost it trying out 'StartUp-Manager'. I tried changing resolution and colour bits and now have a couple of thin lines of coloured pixels where the os boot splash should be. 

How can I restore the splash please?

---

### Post by VMC on 2010-04-12
Try this:

```
$ **sudo update-alternatives --config default.plymouth**
There are 5 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        manual mode
* 3            /lib/plymouth/themes/solar/solar.plymouth               10        manual mode
  4            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        manual mode
  5            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by bwallum on 2010-04-12
Thanks (although I only got two choices):(> There are 2 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        manual mode
* 2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press enter to keep the current choice[*], or type selection number: 


---

### Post by aviramof on 2010-04-12
you can download more via synaptic just search **plymouth** and download the themes.

thanks for the info vmc:)

---

### Post by bwallum on 2010-04-12
> **aviramof said:**
> you can download more via synaptic just search **plymouth** and download the themes.

thanks for the info vmc:)

and thank you aviramof, I now have 5 alternatives too!:)> There are 5 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        manual mode
  3            /lib/plymouth/themes/solar/solar.plymouth               10        manual mode
  4            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        manual mode
* 5            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press enter to keep the current choice[*], or type selection number: 


---

### Post by bwallum on 2010-04-17
Hi again

I still get rubbish from the boot splash. Do I have to run a config file (I'm thinking something similar to running a script that does the config update - say like grub2)?

---

### Post by d3v1150m471c on 2010-04-17
boot into recovery mode and repair broken packages. Usplash will resort back to it's original. (I think you're talking about the login background?)

---

### Post by philinux on 2010-04-17
> **bwallum said:**
> Hi again

I still get rubbish from the boot splash. Do I have to run a config file (I'm thinking something similar to running a script that does the config update - say like grub2)?

Yep.

```
sudo update-initramfs -u
```

---

### Post by bwallum on 2010-04-17
Thanks all!

The problem (or manifestation of it) was with the nvidia driver -current - recommended, loaded from the Hardware Drivers gui.

Run with nvidia driver - random pixel splash
Run with x default - splash fine 
Run with nvidia driver - random pixel splash
.
.
.
.

Tried with sudo update-initramfs -u in between, no effect. Above behavior repeatable 100%. Don't you just kick yourself when you see how easy it is to overcome!

---

### Post by bwallum on 2010-04-17
Played around with another machine and managed the same glitch. Hardware Drivers shows three nVidia offerings as green. Is that a 'feature' change?

---

### Post by cariboo on 2010-04-17
From the looks of it you installed all three drivers, go to System->Administration->Nvidia X Server Settings to check what driver you are actually using and remove the others.

---

### Post by mc4man on 2010-04-17
> Hardware Drivers shows three nVidia offerings as green

That's fairly typical, you have nvidia-current installed and in use.

As far as the other 2 it's most likely you only have the modaliases for them installed, though it's possible you could also have the driver installed.
 
*It's not an issue either way*, though if the nvidia-current is working well there would never be a need to switch to the older driver. ( so no reason to have installed if it is -  which it most likely isn't.

You can always see what's installed and available from update-alternatives
```
sudo update-alternatives --config gl_conf
```

Note: you can switch from 1 avail. choice to another thru update-alt...,( typically nvidia < - > nouveau) but there are some commands that need to be run afterwards so, if inclined, don't switch if not prepared.

---

### Post by bwallum on 2010-04-18
I didn't install 3 drivers, the changes have been made by recent Lucid updates. If I put the mouse pointer over the other driver lines then the message says available and not activated (although the green light is on).

```
sudo update-alternatives --config gl_conf 
```returned:-
> There are 1 choices for the alternative gl_conf (providing /etc/ld.so.conf.d/GL.conf).

  Selection    Path                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/mesa/ld.so.conf   500       auto mode
* 1            /usr/lib/mesa/ld.so.conf   500       manual mode

Press enter to keep the current choice[*], or type selection number: 
I am just running the default graphics driver having removed the nvidia driver.

There does appear to still be an issue:-

I used Hardware Drivers to install the recommended nVidia driver and this time got the appropriate window display (one green light, two grey). I guess further updates resolved the issue. However Usplash is now back to thin lines of scrambled pixels. This could be a real problem if a disk check starts because you can't see what's happening on the screen, it just looks as though the system has hung.

I'll check out Launchpad....

EDIT
Seems to be a bug [https://bugs.edge.launchpad.net/ubuntu/+source/jockey/+bug/562226?comments=all]("https://bugs.edge.launchpad.net/ubuntu/+source/jockey/+bug/562226?comments=all")

Usplash scramble reported as bug [https://bugs.edge.launchpad.net/ubuntu/+bug/565866]("https://bugs.edge.launchpad.net/ubuntu/+bug/565866")

---

