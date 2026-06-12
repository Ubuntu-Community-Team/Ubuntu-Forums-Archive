---
title: "Problem Installing Version 7.10 on HP Pavilion dv2715nr Laptop"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by juang on 2008-03-13
I am experiencing a problem installing Ubuntu Version 7.10 (i386) on an HP Pavilion dv2715nr Laptop. It cannot recognize the graphics hardware which is an NVidia GeForce Go 7150M graphics processor. The system has an AMD Turion 64x2 CPU. The install is completely failing after it takes me to a dialog that tells me that the Ubuntu install is going to use a low resolution graphics setting. Any assistance is greatly appreciated.

---

### Post by gtdaqua on 2008-03-14
are u able to use the GUI? NVIDIA is simple to get running in Ubuntu/Kubuntu even on development versions. 

use this guide to get the NVIDIA working without any problem. Better print it.

[Gutsy Latest NVIDIA on DELL - walkthrough]("http://ubuntuforums.org/showthread.php?t=596875")

---

### Post by max littlemore on 2008-03-14
> **gtdaqua said:**
> are u able to use the GUI? NVIDIA is simple to get running in Ubuntu/Kubuntu even on development versions. 

use this guide to get the NVIDIA working without any problem. Better print it.

[Gutsy Latest NVIDIA on DELL - walkthrough]("http://ubuntuforums.org/showthread.php?t=596875")

That link looks accurate, but I just had the same problem installing 7.10 on a dv6000 series HP and didn't need to use the command line to get the graphics working.

From memory, you have a choice to configure the graphics? If so, you can use the vesa driver to get the system up and running and then install/enable the restricted drivers through synaptic/restricted drivers manager. If you still need help doing this, post back.

The main reason I'm posting is that the specs for your lappy and mine look similar, although mine's has more chunky features ... and it's bigger :guitar:.

I found a few other problems the way which are worth noting and I may be able to help you avoid wasting some time....

Three problems I had were sound, camera and pointing device

_**Sound**_
It all seems to work great until you plug in headphones. Then when you think your viewing pr0n in private and noone can hear, you notice everyone turns their head and starts laughing... plugging in headphones doesn't mute the speakers.

Your best bet is to install a newer version of alsa than is available in the gutsy repositories which really does need command line treatment. [This is an excellent howto.]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

Also, If you're doing ubuntustudio and want realtime (an excellent reason to buy a turion based system), make sure you follow these instructions for your *-rt kernel and set periods/buffer to 3 for jack.

_**Camera**_
According to the site, your camera is external while mine is built in. The same may apply. 

Run "gstreamer=properties", select the "Video" tab and select "Video for Linux 2 (v4l2_" from the **Default input** plugin dropdown.

_**Pointing device**_
When you lock the pointing device and then unlock it, it always launches the help browser.

Go to *System / Preferences* and pick *Keyboard Shortcuts*. Under "Desktop", find   "Launch help browser" and change it to something else. I used "Shift+Ctrl+Alt+?". Maybe you would have figured this out quickly, maybe not, but there you go.

Post back if you have more problems and I'll help if I can, or someone else might.

---

### Post by gtdaqua on 2008-03-14
> **max littlemore said:**
> 
From memory, you have a choice to configure the graphics? If so, you can use the vesa driver to get the system up and running and then install/enable the restricted drivers through synaptic/restricted drivers manager. If you still need help doing this, post back.
.......


'vesa' driver might work in most cases but to install the actual driver you need to stop the X server! So driver installation can be performed only in command line. Even if you tried installing from X, nvidia will terminate the installation asking u to stop display manager and run the installation again.

---

### Post by max littlemore on 2008-03-14
> **gtdaqua said:**
> 'vesa' driver might work in most cases but to install the actual driver you need to stop the X server! So driver installation can be performed only in command line.

Hmmm... maybe. I do remember the dialog saying that the desktop couldn't continue, and I remember being impressed that for the first time since I started playing with Linux in 98, I didn't actually need to use the command line to get X started when installing on hardware that doesn't yet have quality free drivers.

As I originally posted, I got a desktop working and then set up the correct drivers. Then I rebooted, without using the command line.

If you do need to go to the command line, backup and edit /etc/X11/xorg.conf change the driver to vesa to get started, although I didn't need to. Perhaps pressing "continue" worked for me.

---

