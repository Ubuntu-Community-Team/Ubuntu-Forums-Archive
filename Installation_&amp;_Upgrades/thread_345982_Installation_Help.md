---
title: "Installation Help"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by RDUBBALO on 2007-01-25
Hello Everyone I am new with Ubuntu and I am looking foward to getting started, but I am having a problem with the install and I havent found this in any other posts. My disk works and I get to the ubuntu start up selection screen, then it starts to go and I get a screen that has a window pop up saying "Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" Ok so then i looked there and I have (ww)I810: no matching device section for instance(BusID pci :0:2:0) and (EE) No devices detected  Fatal error no screens found. So i guess it isnt picking up the graphics card. Ok I have no idea where to go from here and i see everyone out here is more than helpful so i would appreciate some help. Thank you. I am running a dell dimension E310 and i have a seperate graphics card, PNY 128 mb ddr G-Force fx 5500 pci.

---

### Post by renzokuken on 2007-01-25
you will have to install the nvidia grafix driver by the sound of it. if you have an internet connection, this can be done from the terminal.

```
sudo apt-get install nvidia-glx
```

to install it, then

```
sudo nvidia-xconfig
```

to configure it

---

### Post by aberry9036 on 2007-01-25
What was posted above will work but ONLY if you have a terminal which, if you're computer's like mine, you don't yet. The reason for this happening is that the drivers that ubuntu preloads for your card don't work, they're the wrong ones. To get the desktop (although it will be dodgy graphics until you get the decent drivers) you should do the following.

When the CD boots up it will give you a list of options and a set of F-key options alont the bottom, one of them should say something like "boot options" (I'm pretty sure it's F6).

Press this button and it will bring up a line that tells Ubuntu how to go through the process of starting up. At the end of this line their should be text saying "quiet - splash" I think (sorry for being vague but im not in front of an ubuntu pc at present :S). Delete this ending and type in "break=bottom" and then boot. Now when you boot it will not show the rolling loading bar and will give you a command prompt after a few seconds. In this Command prompt type the following:

chroot /root nano /etc/X11/xorg.conf (remember to put it in EXACTLY as you see it ie upper and lower case stay the same)

This will open up the configuration file for your graphics. Using the keyboard scroll down until you can see a heading called "Device". Under this there should be a line saying "driver" on the left with the driver ubuntu has selected in quotation marks to the right of it. Change whatever is in those quote marks to "vesa"

Once you've done this save and exit this program (ctrl-o, ctrl-x) and then, when the command prompt comes back up, type "exit".

Now Ubuntu should boot in to the desktop. Install it and then, once you have rebooted from your hard drive rather than the cd, follow the instructions above this post :)

---

### Post by renzokuken on 2007-01-25
couldnt you alternatively just boot up until it gives the error message. then press Ctrl+Alt+F1 to get to a terminal/CLI interface?

---

### Post by RDUBBALO on 2007-01-25
> **renzokuken said:**
> you will have to install the nvidia grafix driver by the sound of it. if you have an internet connection, this can be done from the terminal.

```
sudo apt-get install nvidia-glx
```

to install it, then

```
sudo nvidia-xconfig
```

to configure it

Ok this works here after pressin ctrl+alt+f6, but then after the config part it doesnt do anything it say it is installed, but then how do I get ubuntu to start up again. I tried to reboot and it still says its still missing. I need to know what to do after this step here the config code.

---

### Post by RDUBBALO on 2007-01-25
Any Ideas here anyone. I would like to get this program runnung

---

### Post by aberry9036 on 2007-01-26
I didnt know you could get a terminal up by doing that but fair enough, once you've done all those drivers you can't reboot until you've installed it on to your hard drive ( it's running off ram) when you get a console message again after you've installed the drivers type in "startx" or "start-x" or "gnome" or something to bring up the desktop. If that doesn't work try the way I said :D.

---

