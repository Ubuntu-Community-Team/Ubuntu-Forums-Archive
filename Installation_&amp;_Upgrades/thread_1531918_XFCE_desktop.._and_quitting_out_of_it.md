---
title: "XFCE desktop.. and quitting out of it"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by winewood on 2010-07-15
I am looking for the option to quit back to command line from the XFCE 4 desktop environment.
 
I have to install NVidia drivers and it doesn't want the XFCE "X" desktop running.
 
There is no "quit" option that I can find, and logging out only puts me back to a login screen. I feel VERY frustrated as I feel that this thing has hijacked me. 
 
In the past "init 1" has put me into a blue recovery like screen, but now that command doesn't work, or it simply drops my to a "mythbuntu .... " screen which is in-escape-able. 
 
Please help, I am frustrated.

---

### Post by winewood on 2010-07-15
The only way I have found to kill this thing..
 
is remotely ssh'ing into it and killing the X server then running as root " service gdm stop".
 
There has to be an easier way..

---

### Post by Jose Catre-Vandis on 2010-07-15
If you are not autologging in, just do the following:

At the login prompt press CTRL+ALT+F1, this should give you a virtual terminal login prompt. Login using your user and pass, then sudo service gdm stop.

If you are autologging in, just open a terminal and type sudo service gdm stop, you will be sent to a virtual terminal. press CTRL+ALT+F2 and login.

All that said, why aren't you using the hardware drivers applet to install nvidia drivers?

---

### Post by winewood on 2010-07-15
The native NVIDIA drivers for the 7800 do not seem to work with Ubuntu. I had to go directly to the NVidia website to get them and run them via command line. 
 
With my card, I have to install using unique options, then remote login after install, change a file or two then restart. I would almost dare say, do not install MythUbuntu if you have a 7800, stay away from this thing unless you have days to burn.
 
Your technique works WONDERFULLY.. exactly what I needed.  Thank you!

---

