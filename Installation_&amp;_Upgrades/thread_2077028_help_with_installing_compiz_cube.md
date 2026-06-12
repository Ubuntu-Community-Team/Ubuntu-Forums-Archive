---
title: "help with installing compiz cube"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Andrewalc on 2012-10-27
I was running compiz cube before. I had to re-install ubuntu and now it wont work. I installed it with:
> sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-pluginswhen I Installed it before and I changed something in ccsm(compizconfig settings manager) my computer "stalled" for a moment well it made the changes. but now it does nothing. I wonder if it is running unity at all. I have the Ubuntu unity plugin enabled thou. Just a guess. I am at a loss and some direction would be greatly appreciated.
 During my despreation . I tried enabling more plugins, in fact all the plugins, that I got in software center with the search "compiz Plugins". I have now removed them.

I have also done the following commands:
> sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-pluginsI also had to download the unity plug in from software center. it wasn't originally in ccsm.
I was watching a video and it told me to do a
> echo $DESKTOP_SESSION
I was suposed to get back ubuntu and I got back
ubuntu-2d
that may be why I cant get 3d graphics?

---

### Post by Frogs Hair on 2012-10-27
Hello and Welcome 

What version of Ubuntu are you running ?  Unity has been default since 11.04 and I don't how you were able to have a desktop without the Unity Plug-in.

---

### Post by Andrewalc on 2012-10-27
Thank you , and I am running 12.04. I edited my origial thead. I did a 
> echo $DESKTOP_SESSION
and got back
> ubuntu-2d
is this correct?
the video that I was watching said that I should get back
> ubuntu
If its not right do you know how to change it?

---

### Post by grahammechanical on 2012-10-27
You may need to activate a proprietary video driver. You do that through the Additional Drivers utility.

---

### Post by Technicolor on 2012-10-27
I don't exactly know how I got my cube to work, but I know it's possible on Unity.
Uhm, how about going in ccsm and enabling desktop cube, enabling rotate cube, going into general settings, setting vertical workspaces to 1, setting horizontal workspaces to whatever, and then reboot the computer, which I believe worked for me.

---

### Post by Frogs Hair on 2012-10-27
1. Install  proprietary graphics driver because Unity 3D is needed for the cube.   
2. Restart and log into Ubuntu .
3. Drag a terminal onto the desktop just in case. 
4. Open The CCSM.
5. Disable the Unity Plugin and Desktop Wall 
6. Enable Desktop Cube and Rotate Cube.
7. Enable Unity Plugin.

To set the number of sides on the cube proceed to general options > desktop size in the CCSM and set the horizontal size to four.   
 
If you have problems use your terminal. 

Reset Unity   
```
unity --reset
```

---

### Post by Andrewalc on 2012-10-29
so if I log out I can chose between Ubuntu 2d or Ubuntu. (I select Ubuntu). My graphics card in integrated into the mother board as a:
> andrew@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)so the graphic card driver should be already updated. right?
and when I do a 
> unity --reset I Get:> 
andrew@ubuntu:~$ unity --reset
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1e00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1200002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3400004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e00328

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e0032d

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e000b8

Initializing composite options...done
Segmentation fault (core dumped)and I lose my boarder around my windows and I can't move any windows until I logout and then back in.  I still have
> andrew@ubuntu:~$ echo $DESKTOP_SESSION
ubuntu-2dany thoughts?

---

### Post by Frogs Hair on 2012-10-29
Proprietary graphics drivers are installed from additional drivers and provide 3D capability which is needed to run the cube.  Check for 3D support with the following command. ```
/usr/lib/nux/unity_support_test -p
```    

If you have 3D support install the recommended driver and proceed.

---

### Post by Andrewalc on 2012-10-29
I got it to work with:
> sudo apt-get install xserver-xorg-video-intel
unity --reset
compiz --resetI must have either deleted the driver or replaced it with another one.
I thank you with all of you help:)

---

### Post by Frogs Hair on 2012-10-29
That will give a basic cube , but you will have to experiment with the other effects. Have Fun ! :)

---

