---
title: "Cannot Display Video Mode"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by skiforfun on 2007-03-06
I'm new to linux and ubuntu.... tried to install ubuntu 6.10 through the desktop disk, and the screen went black with a "cannot display video mode" message. Searched the forum and someone who had the same problem said he changed the resolution (the cd installer has that option) to 1024x768, he said that fixed his problem but he couldnt see the mouse pointer, he was able to install ubuntu anyway. I tryed the same and experienced the same no-pointer problem, I was also able to install ubuntu anyway. When I finished installing it, it asked me if i wanted to reboot or continue running ubuntu from the live-cd, I chose to reboot. After rebooting it asked which OS to run I chose ubuntu, and after loading it, the screen went black saying "cannot display video mode" once again, but this time I didnt have the resolution option from the liveCD. 
I have no clue on how to fix this, and everytime I search the net, I find lots of people saying you should edit the xorg.conf file, located in /etc/x11/xorg.conf. They usually tell you to back it up first, typing "sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.back" the problem is that when I do this, it tells me the file doesn't exist, and if i try to edit the file, I get into a blank file. Im not even sure if Im typing it in the right place, I have tried typing it in the ubuntu safe mode console, i have also tried running the live cd (changing the resoluton) and opening the terminal application, and also tried running ubuntu normally and when i get the "cannot display..." i press ALT+CTRL+F1 what takes me to the console. None of these consoles works when i type "sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.back", they all say the file doesnt exist. No document or forum post Ive seen talks about not finding the xorg.conf file, they all assume you are in it and tell you how to edit it, so I cant fix my problem, if anyone could help, thanks in advance.

Here are my video card/PC details:
System Model: Dell Dimension 4700               
Processor: Intel(R) Pentium(R) 4 CPU 3.00GHz (2 CPUs)
Memory: 510MB RAM
Card name: NVIDIA GeForce 6800 
Display Memory: 256.0 MB
The monitor is a Dell 17" LCD

---

### Post by bulldog on 2007-03-06
You have to type sudo cp /etc/**X**11/xorg.conf,otherwise your file doesn't exist.

But back to your problem,if you can boot into recovery mode and login in your console,try the next command.
```
sudo dpkg-reconfigure xserver-xorg
``` and choose the desired resolution for your monitor.

Also it could be a good idea to install the drivers for your graphics as well.
```
sudo aptitude install nvidia-glx
``` maybe you should do this first.

---

### Post by skiforfun on 2007-03-06
Thanks for your reply!
Unfortunately Im still far from solving my problem.
The "sudo aptitude install nvidia-glx" command does nothing as it says there are no matches and 0 files were installed.
The second command takes me through a config screen and even if I choose the 1024x768 resolution (that worked during the live cd installation), when i reboot the ubuntu loading fails, displaying same message "cannot display video mode" I really dont know what to do :confused: I typed all the correct info on the config screen, including the monitor sync rates.
I tryed to edit the /etc/X11/xorg.conf but when I type the command it says it cannot be displayed or something, when i run it on the console.
Any more help would be really useful, totally stuck right now :(

---

### Post by dotman on 2007-03-07
bull dog is right, un-# the multiverse repo in your /etc/apt/sources.list and install the nvidia drivers first. Once those have been installed run: dpkg-reconfigure xserver-xorg to rebuild your xorg.conf file.

If given the option use the 'nvidia' drivers. Run 'startx' when you are done and see if it crashes the same way.

If you are still stuck in CLI mode you will have to edit your /etc/X11/xorg.conf file and tell it what graphics driver to use.

If your Device section looks like this: 

```
Section "Device"
	Identifier	"YOUR NVIDIA GRAPHICS CARD"
	Driver		"nv"
```

it is still using the old driver

change it to look like this:

```

Section "Device"
	Identifier	"YOUR NVIDIA GRAPHICS CARD"
	Driver		"nvidia"
```

---

### Post by skiforfun on 2007-03-07
> bull dog is right, un-# the multiverse repo in your /etc/apt/sources.list and install the nvidia drivers first.

I don't know how to do this :confused: 
I tryed looking on the HOWTO section, for installing nvidia drivers, and they say to download drivers and double click them on ubuntu, but the problem is I cant use anything else than the safe mode, and i dont know how to install them from there. I also dont know what to do with the "un-# the multiverse repo..." instruction.
If you could explain some more please, thanks again!:)

---

### Post by bulldog on 2007-03-07
Your repositories were you download your updates,are listed in your sources.list.
This list is located in /etc/apt/sources.list.

BTW,can you tell me which distro you have?like Dapper [6.06] or Edgy [6.10] or even Feisty [7.04]

If you can't login in graphical mode,you have to use nano as your editor in your console.
A warning though,you have to type the commands really carefully because if you missed a 'space' or an uppercase it will give you an error.

Okay let's begin.
First we try to install your graphics driver again.
```
sudo aptitude install nvidia-glx
```
This should work.

If the install is correct,check in your xorg.conf if the driver is set to "nvidia" instead of "nv"
```
sudo nano /etc/X11/xorg.conf
```
Scroll trough the text till you see the device section,check if it's okay,if not change it and safe the file with CTRL-x

Reboot and see what happens.

---

### Post by dotman on 2007-03-07
> **skiforfun said:**
> I also dont know what to do with the "un-# the multiverse repo..." instruction.
If you could explain some more please, thanks again!:)

Sorry for being vague. As bulldog said, the repositories are where you are downloading files using apt-get or aptitude are located in a file at /etc/apt/sources.list. You may be getting the "no matches found" error because the file is not in any of the repos you have enabled in your sources.list file. If this is the case you will have to edit this file using
```
$ sudo nano /etc/apt/sources.list
```
and make sure that
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

does not have a # in front of it. The # means: don't use this! If for some reason they are not already in the file, just add them at the bottom.

At that point you can run
```
$ sudo aptitude update
```
to update your file list, and then proceed with the instructions given earlier in the post.

---

### Post by skiforfun on 2007-03-07
Thanks once again for the replies, but still got another problem :( 
When I installed Ubuntu, i was unable to set up my internet connection. I use a USB wireless adapter on that computer, and it connects to a wireless network from my router. During the installation, it said it couldnt detect any wireless points (i got perfect signal), so it asked me the name of the wireless network and the password. I typed em both correct, and when it had to detect the DHCP part, it failed and i couldnt fix it so I just left it. So... I dont have internet connection through Ubuntu. 
What should I do in this case? is it possible to load the file from a pendrive or cd-rom from the ubuntu safe mode? 
Thanks for your patience :) 

BTW the distro i have, i think its the edgy 6.10, i just downloaded the first one from the download section, the normal desktop Ubuntu 6.10

---

### Post by dotman on 2007-03-08
i think it is pretty unlikely the driver is on the install CD. You could attempt to set up the wireless connection but i think you'd have better luck using an ethernet connection in this situation.

---

