---
title: "dv6552ea what a pain"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by gubemton on 2007-10-27
I bought a dv6552ea and thought I would finally be able to try out linux, my other PC is a family one, and they want to keep it windows.

Please note I am a total linux n00b. First I tried to install using the livecd before gutsy. Got an error, something like it couldn't load the graphical installation. Then the new gutsy was released, and this time, actually got to a box saying that it couldn't find drivers for my graphics card, so I tried to boot the low graphics way. Didn't load, so when I restarted the laptop to try again, it keeps giving me the bcm43xx_microcode.fw error and doesn't even load. 

I did a search and there seems to be tons of problems with the dv6000 series, and so many things to do to fix it it seems to be too much of a hassle. I'm gonna leave it for now and wait a few months for another release that hopefully fixes these issues.

---

### Post by hopcroft on 2008-04-27
Well ive managed to install both gutsy and now hardy with no real problems.

Just boot into the live CD then choose the install icon on the desktop.

I'm a relative noob aswell but i managed.

Here's the best ways ive found to install the wireless and the graphics card:

[SIZE="5"]**Wifi:**[/SIZE] 

First i would recommend plugging into the router with an ethernet cable before you start. sounds daft but its easier to get internet when you have internet.

Follow this - 
**STEP 1: OBTAINING THE REQUIRED PACKAGES**
Most of the work from here on will be done from the command-line, so open up a terminal (Applications > Accessories > Terminal), and use it to create your working directory:

```
mkdir wireless-install
cd wireless-install
```

First we need to obtain the correct XP driver (Vista drivers WILL NOT WORK with ndiswrapper) for this chipset, and also install some extra packages. This is easy if you have access to the internet (via a wired connection or otherwise):
```
wget http://ftp.us.dell.com/network/R151519.EXE
```

Next install ndiswrapper. The latest version is available from the Hardy repositories which is a rather nice change for those of us who are used to the need to recompile ndiswrapper on every kernel change!
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

If you have no internet access on your Ubuntu machine then you'll need to get the appropriate driver from [here](http://ftp.us.dell.com/network/R151517.EXE) and copy it to your working directory (~/wireless-install). The packages can be installed from your trusty Hardy LiveCD (a Gutsy, or any other, LiveCD WILL NOT WORK): 
```
sudo mount /dev/cdrom /cdrom
sudo apt-cdrom add -m
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```


**STEP 2: PREVENTING THE NATIVE MODULES FROM INTERFERING WITH NDISWRAPPER**
So firstly we're going to blacklist a few things by adding them to the /etc/modprobe.d/blacklist file:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
```

We need to edit the file:
```
gksudo gedit /etc/rc.local
```
add the following to lines to the end of the script, just before the "exit 0":
```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

To give you an idea, my /etc/rc.local now looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
```

**STEP 3: INSTALLING THE DRIVER WITH NDISWRAPPER**

Now we're going to use the driver we downloaded from the Dell website (note that it doesn't matter if your laptop is not a Dell, this driver should still work if you have the same chipset) to give ndiswrapper all it needs to access our card:
```
cd ~/wireless-install/
unzip -a R151519.EXE -d R151519/
cd R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```
_NOTE:_ Make sure you use the right case, in Linux driver and Driver very different to DRIVER.
_NOTE II:_ For those of you who have funky fonts in the forum, the driver is a lower caps BCMWL5.inf. Some confusion has occurred as to whether the "L" is a "1" or an "I", hopefully that clarifies!

And that's it!

The wifi-light will light up after you "modprobe ndiswrapper".
```
sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```

Then your online, go to the network nanager at the top of the screen and your online.

[SIZE="5"]**Graphics:**[/SIZE]

Now that your online go to System->Administration->Synaptic Package Manager and search for envyng.  You should see 3 options, click on the box next to envyng-gtk and choose mark for install, it will add another package, ok that and then apply.

Now go to Applications->System Tools-> EnvyNG and a window will pop up. Click on NVIDIA then on install automatic and go, it will download and install then prompt to reboot. OK that and reboot.

After you reboot open up the terminal again and type ```
sudo nvidia-settings
``` and a window will pop up, choose screen configuration and change resolution to 1280x800, apply and then save to X-Config.

Close and your done!!

---

