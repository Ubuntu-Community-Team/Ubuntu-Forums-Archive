---
title: "[SOLVED] 64 bit, Installed to spare HD, trouble with nvidia and screen res."
date: 2008-07-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-12
No auto offer to install proprietary driver.

Top panel out of monitor.

Had to use screens and graphics to sort out res. Lots of flicker.

Tried installing nvidia-glx-new but it wanted to remove ubuntu-desktop and ton of xserver stuff. Tried envy - message about system not compatible.

Apart from this minor glitch the boot up time is very much improved. And the desktop is very much snappier.

How do I fix the nvidia driver.

---

### Post by psyke83 on 2008-07-12
> **philinux said:**
> No auto offer to install proprietary driver.

Top panel out of monitor.

Had to use screens and graphics to sort out res. Lots of flicker.

Tried installing nvidia-glx-new but it wanted to remove ubuntu-desktop and ton of xserver stuff. Tried envy - message about system not compatible.

Apart from this minor glitch the boot up time is very much improved. And the desktop is very much snappier.

How do I fix the nvidia driver.

You would save yourself a lot of bother by searching this forum, it's been discussed extensively. Depending on the model of your NVIDIA card, you need to install either nvidia-glx-71, nvidia-glx-96, nvidia-glx-173 or nvidia-glx-177. You may also need to adjust your xorg.conf (it's an alpha release, don't complain).

---

### Post by philinux on 2008-07-12
> **psyke83 said:**
> You would save yourself a lot of bother by searching this forum, it's been discussed extensively. Depending on the model of your NVIDIA card, you need to install either nvidia-glx-71, nvidia-glx-96, nvidia-glx-173 or nvidia-glx-177. You may also need to adjust your xorg.conf (it's an alpha release, don't complain).

I'm not complaining at all, only took 5 mins to sort out with screens and graphics. I had to resort to that as the menu bars were out of the monitor. Happy to test. As you see I've installed to my spare HD as before I had a Vbox install.

It's a 8600 GT.

---

### Post by psyke83 on 2008-07-12
> **philinux said:**
> I'm not complaining at all, only took 5 mins to sort out with screens and graphics. I had to resort to that as the menu bars were out of the monitor. Happy to test. As you see I've installed to my spare HD as before I had a Vbox install.

It's a 8600 GT.

I know you weren't complaining, but it was a warning to others who may be tempted to do so ;). During the development cycle, the restricted drivers often give users trouble, and it's simply unavoidable due to the work involved. 

This is especially relevant for Intrepid as a) nvidia have split the drivers into four versions, depending on your card (crazy), and b) the fglrx drivers don't seem to support kernel 2.6.26 yet (although maybe now they do, I don't have an ATI card). When all this stabilizes later in the development cycle, I'm sure the "Restricted Drivers Manager" (is it called jockey now?) will work automatically.

---

### Post by BackwardsDown on 2008-07-12
I have a Nvidia Quadro NVS 140m.

How do I know if I need the 177, 173, 71 or the 96 driver? I have googled but it I can't find it.

And why doen't the restricted-driver-manager do this for me? Is this something that is being worked on?

---

### Post by philinux on 2008-07-12
I installed 177, but no joy. Now in low res mode.

Did the 

sudo nvidia-xconfig 

Got low res.

any suggestions.

---

### Post by Nullack on 2008-07-12
I had the same issue, no auto hardware prompt for installing the nvidia driver

I used synaptic to install the 177.13 driver

Then did the /etc/init.d gdm stop, nano -w /etc/X11/xorg.conf

adding:

Driver    "nvidia"
Option    "NoLogo"

to it and saving

Do not use the nvidia setup program for xorg.conf - have a read on nvnews forum its not right.

I did not add anything else to the xog.conf

One thing to note is that it doesnt like conky auto loading on user login

---

### Post by philinux on 2008-07-13
First did this.

sudo dpkg-reconfigure xserver-xorg -phigh

To reset to standard xorg.conf

Then added the two lines.

nvidia
nologo

Rebooted, and now got driver installed correctly. Although sys>admin>hardware drivers shows nothing.

I assume,the xorg error, or maybe it's not an error, has been reported. I don't want to raise a duplicate.

---

### Post by Gina on 2008-07-13
I installed the nvidia driver as per plun's post then copied my working xorg.conf (which I keep handy) to replace the system xorg.conf.  Rebooted and I immediately got the right resolution.

---

