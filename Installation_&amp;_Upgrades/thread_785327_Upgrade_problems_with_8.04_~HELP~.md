---
title: "Upgrade problems with 8.04 ~HELP~"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by caveman79 on 2008-05-07
Today I decided to update my 7.10 to 8.04. I clicked on the upgrade under the software updates and ran through all the steps until it completed. When I restarted my system it came up with the unknown display driver window. I went through and tried to select the right driver for the NVIDIA e-GEFORCE 7950 GT, but none of them passed the test. OK...so I started it under low resolution mode. 

Here is where the real problems start. I can only open some of the applications, but not all of them. The software sources, hardware driver, and synaptic will not start. When I try to change the appearance to normal or high it tell me that it can't. I was running the last one  just fine before so I didn't think there would be any problems, but each time I try to run those programs the circle spins and nothing.

Does anyone know what I can do to fix this problem? Right now it is looking like I have no choice but to format and do a clean install.

---

### Post by Dakiraun on 2008-05-07
This is likely due to some lingering old configs.  First thing to try would be to get things working right with the graphics and X.  Try logging out then dropping to the terminal (CTRL+Alt+F1).  Shutdown the gdm:

```
sudo /etc/init.d/gdm stop
```

Then make a backup of your xorg.conf:

```
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
```

Of course, you can name the backup file whatever you want - doesn't have to be what I did.  Next, rerun the utilities to configure the nVidia card:

```
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
```

This should create a new xorg.conf for you.  When I upgraded from 7.10 to 8.04 on a Precision M65 laptop, I couldn't carry over the old xorg.conf and had to build a new one to get things to work.

You may also want to install the nVidia settings panel for more precise control over the card later:

```
sudo apt-get install nvidia-settings
```

Once your're done, restart the gdm and see if your situation has improved:

```
sudo /etc/init.d/gdm start
```

Hope that helps stabilize things.  Are you getting any error messages when you tried to run the other apps?

---

### Post by caveman79 on 2008-05-07
Thanks for the advise, I will give it a shot. Right now I am working with 600x800 display and it is making it hard to get around. 

As for error messages, I am not getting any. The program just looks like it is starting then goes away. It says in the bar that it is starting admin, then a second later that disaperes.

---

### Post by caveman79 on 2008-05-07
I followed the steps and everything looked good. The only catch is that the driver was already installed. I followed all the other steps and everything looked good until i restarted. When I login I get the graphic are running at low screen and it prompt me to select a driver and monitor. I have gone through all of the nvidia ones it list and none of them test out stat. The test says each and every one of them failed. What do I do now?

I installed the nvidia settings and it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Under the Hardware drivers, I have disabled and re-nabled the nvidia.

On a happier note, I was able to find a solution to the problem of not being able to access the program. Just by chance I found a poster with a similar problem. The solution turned out to be to go into the network manager and change the host name. After the restart everything worked fine.

---

### Post by Dakiraun on 2008-05-09
Hmmm... odd, seems like it's using a different nVidia driver than usual.  Well, I would try what it says, but like before you'll need to drop out of your session to the login window, go to the prompt, kill the gdm (which stops X) then do:

```
sudo nvidia-xconfig
```

I've not tried that before, but I'm guessing it rewrites the xorg.conf as well.  Glad the other issues got resolved for ya.

---

