---
title: "visual problems? sent to wiki.x.org?"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by Zonkou on 2007-08-27
hello again guys. Got past my first hurdle, but here comes the second.

Got past the installation portion (i think) and it started to load into ubuntu.  It then showed me a black and white screen with a gui menu in weird lettering, telling me that my computer needed to update someting with my visuals ( i dont have the comp infront of me, since im at work, so i can't list the exact error).

It also told me to go to wiki.x.org to update it.  So i went to that site but since im new to unbuntu and linux installation, I am totally lost what im suppose to download and where im suppose to put the files once there downloaded.

Please let me know if anyone knows what I have to do or can explain this all to me in VERY simple english.  Thank you.

---

### Post by dougfractal on 2007-08-27
> My Specs:
Inspiron 1520, Intel Core 2 Duo T7300, 2.0GHz, 800Mhz, 4M Cache
2GB, DDR2, 667MHz 2 Dimm
256MB NVIDIA GeForce 8600M GT
160G 7200RPM SATA Hard Drive



> Version 100.14.09:
* Adds support for new GPUs:
o GeForce 8600 GTS
o GeForce 8600 GT
o GeForce 8600M GT
o GeForce 8600M GS
o GeForce 8500 GT
o GeForce 8400 GS
o GeForce 8400M GT
o GeForce 8400M GS
o GeForce 8400M G
o GeForce 8300 GS
o Quadro FX 1600M
o Quadro FX 570M
o Quadro FX 360M
o Quadro NVS 320M
o Quadro NVS 140M
o Quadro NVS 135M
o Quadro NVS 130M

Version 100.14.+  required

> [ctrl+alt+F1]
login 
sudo -s
nano /etc/X11/xorg.conf
change driver  "nv"   to driver "vesa"
/etc/init.d/gdm restart

To get thr nvidia drive truly working Install Envy to get the latest drivers
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Zonkou on 2007-08-27
ya, you have the exact laptop that im using...

so install Envy and it will update everything that I need for me? will this work if im using vista and trying to add ubuntu onto the same harddrive?

thank you for your help, but

this time in english! :lolflag:

---

### Post by dougfractal on 2007-08-27
Quote:
My Specs:
Inspiron 1520, Intel Core 2 Duo T7300, 2.0GHz, 800Mhz, 4M Cache
2GB, DDR2, 667MHz 2 Dimm
256MB NVIDIA GeForce 8600M GT
160G 7200RPM SATA Hard Drive 
 sorry that is a quote from YOU in an earlier thread. I was just tring to clarify the post.

can you do this

[ctrl+alt+F1]
login
sudo -s
nano /etc/X11/xorg.conf
change driver "nv" to driver "vesa"
/etc/init.d/gdm restart

to get X working?

---

### Post by Zonkou on 2007-08-27
I will try this in an hour when I get home. Thank you.

---

### Post by Zonkou on 2007-08-27
ok finally at home, when I press ctrl+alt f1, it brings up the help  page.

not sure where you wanted me to be at, in vista or where...but in vista it sends me to help page.

---

### Post by dougfractal on 2007-08-28
> in vista  I thought this was a ubuntu forum !!!

ctrl+alt+f1  from LiveCD at > It then showed me a black and white screen 

then to get X working
login
sudo -s
nano /etc/X11/xorg.conf
change driver "nv" to driver "vesa"
/etc/init.d/gdm restart


This will get X working but you will need "envy" to get the most out off your card.

---

### Post by Zonkou on 2007-08-28
I didn't see anywhere where I could change the driver from nv to vesa.

I got into the nano /etc/x11/xorg.conf and it looked like it brought me to a blank text editor, I tried using all options with no luck and couldn't change the driver or anything?

so much for linux coming out ontop, might need to wait a year or so, so they can make it a little easier to install, especially for us noobs?
ill keep trying, but this is starting to become a useless endeavor.

---

### Post by dougfractal on 2007-08-28
I've just seen the nvidia driver 1.0-9755 and should work for your card

ctrl+alt+f1     #change to CLI

> sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig

ctrl+alt+f7         #   change to GUI
ctrl+alt+backspace     #  restart X


[B]
If this fails[/B]

ctrl+alt+f1     #change to CLI

> sudo sed -i 's/"nv"/"vesa"/' /etc/x11/xorg.conf    [COLOR="DimGray"] #  this will do the change for you[/COLOR]

ctrl+alt+f7         #   change to GUI
ctrl+alt+backspace     #  restart X


the **sed** command must be copied as is.


If you have a wired cable and can **network your two machines**
> sudo apt-get install ssh
ifconfig    # find you IP address

and **putty** on your vista  then login using ssh.



or try Mint Linux or 7.10 gutsy release. [http://cdimage.ubuntu.com/releases/gutsy/tribe-5/](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/)  (preview version)

---

### Post by Zonkou on 2007-08-30
I tried your first option with i guess no luck, I need to check a few things, but when refreshing it, it was still giving me the graphical error..so i move on.

I then tried using the sed search, but it told me that it couldn't search there because 

/etc/x11/xorg.conf

didn't exist? i must have missed a step, just not sure where.
thank you dougfractal for your help.  ill keep fighting the good fight

---

### Post by dougfractal on 2007-08-30
sorry typo

>  sudo sed -i 's/"nv"/"vesa"/' /etc/**X11**/xorg.conf  # this will do the change for you

---

