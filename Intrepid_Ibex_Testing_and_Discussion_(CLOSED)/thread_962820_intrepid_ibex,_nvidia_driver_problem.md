---
title: "intrepid ibex, nvidia driver problem"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2008-10-29
hello all.

ive just tried to install the rc of intrepid, the install went well, but i have found the same issue as i did with the beta of intrepid, that being that it wont let me use the nvidia 177.80 driver.

if i activate the driver and then restart like it suggests when the system restarts all i get is a blank screen, and the only way i can get a working system (or working graphics) is to restart and then select recovery mode and then select fix xserver.

has anyone else had this issue ? and if so have you found a solution ?
technically i can manage with the screen as it is, but i am unable to change resolutions, or the screen size because i cant use the nvidia driver.
cheers (i may post a bug report on launchpad)

---

### Post by ad_267 on 2008-10-29
What video card do you have?

I didn't have any problems with my 6600gt.

---

### Post by techno-mole on 2008-10-29
the system ive just installed intrepid on is using an nvidia 8600gs (agp) which works perfectly by the way.
i had the same problem with the beta of intrepid on my system, which is running an 8600gt pci express, im about to install intrepid (the rc on my system as well)

---

### Post by ad_267 on 2008-10-29
How are you trying to install the drivers? They have done things a bit differently with the nvidia driver packages in Intrepid, I remember I went to System - Administration - Hardware Drivers and there were a few different options to choose from. The recommended drivers were the 177 version which worked perfectly.

---

### Post by techno-mole on 2008-10-29
i have tried 2 ways.

1 - when you first install kubuntu (ubuntu) normally if there are drivers (eg - for the nvidia cards) a message appears letting you know about it, you can then choose what ever suits (in this case i chose the 177 driver)
it will then download and install whats needed (if anything) then it will tell you to restart the system, which i do,
 i am thne presented with a blank screen (no login window etc)

2 - i go to hardware/drivers and then select the recommended (again the 177 driver) again it installs whats needed, and again it says you need to restart the system, which i do and again im presented with a blank screen.

the system keeps telling me i should use the 177 driver but it wont actually let me use it.

i have tried removing it altogether and then re-installing in the 2 ways described above, and all result in the same thing, a blank screen when restarted.

for some reason things are not as simple as they were in hardy and previous, all i used to do was let it install and activate the restricted drivers and restart, then all would be well, but not now it seems.

---

### Post by blackvd on 2008-10-29
I had this same issue on both laptops I upgraded. What solved the problem on the first one was to use envyng to install the driver.

In a terminal

```
envyng -t
```

On the second laptop I accidently selected keep current menu.lst when upgrading which caused me to only be able to boot into Kernel 2.6.24-19. So I had to edit /boot/grub/menu.lst and add kernel 2.6.27-7 to the list and boot into it.

Hope this helps.

---

### Post by blitzer on 2008-10-29
Same problem here :confused: plus wireless :confused:

Maybe the packages are not ready to be released :confused:

Waiting to play with Ibex patiently. :lolflag:

---

### Post by RAOF on 2008-10-29
The interesting piece of debugging information here would be your /var/log/Xorg.0.log file.  I've seen similar sorts of strange nvidia behaviour before; when looking in the Xorg.0.log there's a big warning saying something along the lines of 
"You know that auxiliary power supply socket on the card?  Please plug it in.  I'm not going to start until the card's fully powered".

Even if that's not your problem, there's approximately nothing anyone can do without the information in the debug log - that is: Xorg.0.log.  You'll need to get this by enabling the nvidia driver, booting to the black screen, then rebooting into recovery mode (not the GUI recovery mode - that will overwrite the log) and copying the log with
```

cp /var/log/Xorg.0.log ~/Xorg.0.log-black-screen

```

---

### Post by Kleist on 2008-10-29
I'm having the same problem. 

My video card is 

 nVidia Corporation GeForce 7300 GT 

and I've been trying to install the different nvidia drivers such as:

177.80
173.14.12.1
96.43.05

with system-->Administration-->hardware drivers
and also with EnvyNg with no luck. As tecno-mole says, after the install and restart of my computer I got a black screen that says: frequency out of range. Then I have to restart the computer and I have to fix X server, but then I just got only the 800x600 resolution.

I read somewhere that the problem is with the nvidia driver, nothing to do with ubuntu, but even though is a nuisance. Besides that, II works fine in my computer. 
:)

---

### Post by Awperator on 2008-10-29
> **Kleist said:**
> I'm having the same problem. 

My video card is 

 nVidia Corporation GeForce 7300 GT 

and I've been trying to install the different nvidia drivers such as:

177.80
173.14.12.1
96.43.05

with system-->Administration-->hardware drivers
and also with EnvyNg with no luck. As tecno-mole says, after the install and restart of my computer I got a black screen that says: frequency out of range. Then I have to restart the computer and I have to fix X server, but then I just got only the 800x600 resolution.

I read somewhere that the problem is with the nvidia driver, nothing to do with ubuntu, but even though is a nuisance. Besides that, II works fine in my computer. 
:)

Same problem here as well with a Nvidia Geforce 4 Ti 4800. I tried to update using the hardware restricted drivers thing (doesn't even show up anymore) and also installing the 96.43.05 binary straight from nvidia. No luck with either.

---

### Post by techno-mole on 2008-10-29
```
Xorg.0.log there's a big warning saying something along the lines of
"You know that auxiliary power supply socket on the card? Please plug it in. I'm not going to start until the card's fully powered".
```

its funny you should mention that, but......

i have just re-built the system that had the problem, i had forgotten that it needs to have a molex plugged into the back of it (my pci express doesnt need a power input) this has now solved my problem, and yes i do feel like a plank :)

for anyone else having trouble, the best thing i can suggest is to look about the forums, and maybe post a bug report on launchpad, i did have the same problem with the beta, and after while it sorted itself out, but it would seem that some issues still remain with the new driver and the new kernel.

cheers

---

### Post by RAOF on 2008-10-29
> **Awperator said:**
> Same problem here as well with a Nvidia Geforce 4 Ti 4800. I tried to update using the hardware restricted drivers thing (doesn't even show up anymore) and also installing the 96.43.05 binary straight from nvidia. No luck with either.

That's because (as explained in the release notes and warned of in update-manager) there isn't actually an nvidia driver that supports both your card and Xserver 1.5.  Apparently there's been a beta driver that does that released today - either that driver or the final release of that driver should get into Intrepid via intrepid-updates.

---

### Post by Awperator on 2008-10-29
Edit:
Got the new beta driver to work with my legacy Geforce 4 Ti MX 4800 SE

Beta driver now available for legacy:
[http://www.nvnews.net/vbulletin/showthread.php?t=122139]("http://www.nvnews.net/vbulletin/showthread.php?t=122139")

Havent tried it yet, watching Obama on tv

---

### Post by Tristan_B on 2008-10-29
> **techno-mole said:**
> hello all.

ive just tried to install the rc of intrepid, the install went well, but i have found the same issue as i did with the beta of intrepid, that being that it wont let me use the nvidia 177.80 driver.

if i activate the driver and then restart like it suggests when the system restarts all i get is a blank screen, and the only way i can get a working system (or working graphics) is to restart and then select recovery mode and then select fix xserver.

has anyone else had this issue ? and if so have you found a solution ?
technically i can manage with the screen as it is, but i am unable to change resolutions, or the screen size because i cant use the nvidia driver.
cheers (i may post a bug report on launchpad)

I had exactly this problem when I upgraded. It turns out you need to have the kernel headers installed in order for the build the graphics driver. Unfortunately, for some reason the Hardware Drivers programme (jockey) doesn't think to install these for you.

The solution is to install the package linux-headers-generic, then use the hardware drivers programme to activate the driver again. Then reboot (fully, don't just restart X), and all should be working.

Hope this helps!

---

### Post by techno-mole on 2008-10-30
well for the most part everything is working (well on one system anyway)
the driver is installed and being used, although it seems a curious set up with the driver and xorg, but there you go.

however when i run nvidia-settings (as root, and in a terminal) to set up the display, when i try and save the configuration file i get " segmentation fault " and thats it ? i dont think its actually saving the file.

Never mind i have found the solution (seems it has been reported as a bug on launchpad)
if you are having the same problem then try this.

in a terminal type the following

```
sudo nvidia-xconfig
```

then run 

```
sudo nvidia-settings
```

this should allow you to set the resolution etc to however you want it, and save the the configuration.
hopefully this will help someone.

---

