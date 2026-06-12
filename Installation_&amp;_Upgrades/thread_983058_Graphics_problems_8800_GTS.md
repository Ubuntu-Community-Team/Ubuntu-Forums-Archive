---
title: "Graphics problems: 8800 GTS"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by mastaphoo on 2008-11-15
Okay, here goes. I auto-upgraded to 8.10 last week, and since then my graphics have been giving errors. I booted just fine the first time, and installed the nVidia 177 drivers, which were recommended. I believe I had the 173 drivers before, and had no problems with games or desktop effects or anything. I restarted, and got an error about the drivers not loading (which I can post if needed) before I even got to my desktop. My choices were to use a default configuration, run in low graphics mode, or use a backup config. I tried default config, and tried both 177 and 173. Both gave the same message, and I now can't run compiz and haven't even tried games. I have an eVGA 8800 GTS in an Asus P5B with a Core2Duo E6400. Any ideas?

---

### Post by pdub on 2008-11-15
These are the steps that I follow when installing NVidia drivers.

1. Choose low graphics mode if you are presented with this option, and login

2. Download the latest NVidia driver from the nvidia site. Be sure to choose the proper driver for your platform.

3. Use CTRL+ALT+F1 to open a terminal, then login

4. Navigate to the location where you saved the NVidia driver

   ```
sudo chmod +x NVIDIA-** (file name of the downloaded NVidia driver)
```

5. You may need to install build-essential if not already installed

	```
sudo apt-get install build-essential
```

6. Stop GDM

	```
sudo /etc/init.d/gdm stop
```

7. Install the new NVidia driver, I use all of the default settings.

	```
sudo ./NVIDIA-** (file name of the downloaded NVidia driver)
```

8. Load the driver

	```
sudo modprobe nvidia
```

9. Restart GDM

	```
sudo /etc/init.d/gdm start
```

10. To prevent the restricted NVidia driver from loading do the following from terminal.

	```
sudo nano /etc/default/linux-restricted-modules-common
```

    Add the following

	```
DISABLED_MODULES="nv nvidia_new" 
```

11. Delete the restricted module

	```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```

You may need to repeat these steps if you upgrade your kernel in the future or wish to install the newest NVidia drivers.

---

### Post by mastaphoo on 2008-11-16
Okay, so when I try to go into low graphics mode it says "Wait one minute while your display is reset" and whether I click OK or not, it just stays on a black screen. Is there any way to do this without going into low-gfx mode?

---

### Post by pdub on 2008-11-16
Try ctrl+alt+F1

---

### Post by mastaphoo on 2008-11-16
I did, no dice. Just a black screen, and nothing makes anything respond.

---

### Post by Scunizi on 2008-11-17
Try Ctrl+Alt+F3 instead.  If it's trying to reset the video it might be using TTY1..

---

### Post by mastaphoo on 2008-11-21
I'm still getting nothing, and it's quite irritating. Is there some way I can do all of that without going into low-graphics mode? Or some way I can go into low-graphics mode without restarting? I also now have the option of graphics driver 96, I'll let you all know how that goes.

EDIT: Version 96, my bad

---

