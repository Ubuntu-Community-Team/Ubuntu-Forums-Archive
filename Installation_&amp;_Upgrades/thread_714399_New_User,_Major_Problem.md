---
title: "New User, Major Problem"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Schwooter on 2008-03-03
Hi.

So, I've decided to install Gusty Gibbon on my machine. The Ubuntu install went flawlessly. Now, when I start up, I get a prompt telling me that I have restricted drivers for my Nvidia card I can install. So, I install it, and when I reboot, Ubuntu shuts down properly, and when it comes back up, there's a sliver of orange on the load bar and then I get a black screen.

How can I fix this? Currently, I'm downloading the 196 updates I need. I haven't downloaded the restricted drivers yet. However, I did some research, and found a script called "Envy" which finds the drivers for my video card and downloads/installs them. Should I use that?

Thanks.

---

### Post by PmDematagoda on 2008-03-03
It mostly depends on your VGA card, if it is not well supported on the Nvidia driver provided through the repositories then you may have to manually install the driver or use Envy. It is ok to use Envy, but first remove the old Nvidia driver using:-
```
sudo apt-get purge nvidia-glx-new
```

---

### Post by Schwooter on 2008-03-03
Thanks for that. I haven't tried it out yet, still downloading these updates.

However, I've noticed my sound isn't working. I have a Sound Blaster Audigy... What drivers would I need for it to properly work?

---

### Post by Schwooter on 2008-03-04
Still having problems.

Later last night, the update finished. I rebooted, and everything was fine. I then ran Envy, it installed my Nvidia drivers, and I rebooted.

Now, I get the full Ubuntu bar to load, and then black screen. After that, my moniter's "on" light blinks like when I have the computer off.

What is the problem here?

---

### Post by dstew on 2008-03-04
You need to reconfigure the xserver, the program that runs the video display. When you get to the black sceen, press ctrl-alt-F1 and you should get a command line. On the command line, enter sudo dpkg-reconfigure xserver-xorg. You will get a text-based installation program that takes you through all the steps needed to reconfigure your graphical user interface. There are explanations at every step, and a lot of it is about your keyboard, mouse etc. The part to pay attention to is the video display part. You are asked to pick a driver. You can try nvidia if it is a choice. I recommend for a resolution picking as the maximum the one you actually use. Don't pick a super-high resolution, thinking that later I will get that big display.

After you have finished with the reconfiguration, enter startx on the command line. If that doesn't work, try ctrl-alt-backspace. If that doesn't work, reboot. If you still have the problem, I guess the nvidia driver is not working for you. Then you have to reconfigure to the vesa driver to get your desktop, and study the driver issue a bit more.

---

### Post by Schwooter on 2008-03-04
> **dstew said:**
> You need to reconfigure the xserver, the program that runs the video display. When you get to the black sceen, press ctrl-alt-F1 and you should get a command line. On the command line, enter sudo dpkg-reconfigure xserver-xorg. You will get a text-based installation program that takes you through all the steps needed to reconfigure your graphical user interface. There are explanations at every step, and a lot of it is about your keyboard, mouse etc. The part to pay attention to is the video display part. You are asked to pick a driver. You can try nvidia if it is a choice. I recommend for a resolution picking as the maximum the one you actually use. Don't pick a super-high resolution, thinking that later I will get that big display.

After you have finished with the reconfiguration, enter startx on the command line. If that doesn't work, try ctrl-alt-backspace. If that doesn't work, reboot. If you still have the problem, I guess the nvidia driver is not working for you. Then you have to reconfigure to the vesa driver to get your desktop, and study the driver issue a bit more.

I just tried this. When I hit Ctrl-Alt-F1, nothing happens. My monitor's on light continues blinking and the screen stays black.

---

### Post by PmDematagoda on 2008-03-04
Boot Ubuntu in Recovery Mode and then reconfigure the X-Server to it's defaults using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After that is done, start the X-Server using:-
```
sudo startx
```

---

### Post by Schwooter on 2008-03-04
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode and then reconfigure the X-Server to it's defaults using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After that is done, start the X-Server using:-
```
sudo startx
```

This is going to sound stupid, but how do I get into recovery mode?

---

### Post by PmDematagoda on 2008-03-04
When you boot the PC you will reach a menu, from that menu select Ubuntu (Recovery Mode), that will start Ubuntu in Recovery Mode.

---

### Post by Schwooter on 2008-03-04
Awesome! I can finally see my desktop again. However, I need to have these drivers to get Beryl and Desktop Effects going... What should I do to solve this problem?

---

### Post by PmDematagoda on 2008-03-04
First things first, remove the nvidia-glx-pacakges using:-
```
sudo apt-get purge nvidia-glx-new
```
For the next steps the VGA card specifications would be needed, most specifically the model of the VGA card.

---

### Post by Schwooter on 2008-03-04
My card is a Nvidia GT 8500 Geforce.

---

### Post by Skullbasher on 2008-03-04
stupid stupid stupid

---

### Post by Schwooter on 2008-03-04
Alright, I think I've exhuasted all of Envy's install possiblities... Automatic, Manual, with or without the nvidia-glx-new driver enabled. None of them worked. There has to be something I'm missing here. I'd really like to get this to work. Please, help.

---

### Post by PmDematagoda on 2008-03-04
Install the Nvidia driver manually:-

1) Install the prerequisites for the Nvidia installer:-
```
sudo apt-get install build-essential
```

2) Download the Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

From the previous step onwards the CLI(Command Line Interface) will be used.

3) Kill the GUI with:-
```
sudo /etc/init.d/gdm stop
```

4) Run the installer with:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

5) After the installation is finished reconfigure the GUI with:-
```
sudo dpkg-reconfigure xserver-xorg
```
select any options you need.

6) Restart the GUI with:-
```
sudo /etc/init.d/gdm start
```

See if the X-Server now works properly.

---

