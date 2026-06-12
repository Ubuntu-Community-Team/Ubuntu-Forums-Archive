---
title: "nvidia issue during latest upgrade"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gspat on 2008-09-22
Hi!

I should start of by saying that I've never been able to get nvidia drivers working on my test box. This hasn't really bothered me too much, since the NV driver works and gives me the resolution I want, but it's still a little niggly thing that I would like to eventually solve.

I did a update and upgrade here this morning and noticed something strange...

```
Setting up nvidia-173-modaliases (173.14.12-1-0ubuntu3) ...
Setting up nvidia-177-kernel-source (177.76-0ubuntu1) ...
Cleaning up the DKMS tree
ls: cannot access /var/lib/dkms/nvidia/: No such file or directory
Done.
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 177.76
Doing initial module build
Installing initial module
Done.

Setting up nvidia-177-modaliases (177.76-0ubuntu1) ...
Setting up nvidia-glx-177 (177.76-0ubuntu1) ...

```

Does this mean that I have both 173 AND 177 installed simultaneously on this machine? I thought that software checks made that impossible (or close to it at least!).

This is the first time I've seen this in any upgrades I've done...

what is missing in the line 

```
ls: cannot access /var/lib/dkms/nvidia/: No such file or directory
```

Thanks for any assist!!!

---

### Post by hellibombelli on 2008-09-22
I'm not sure if this is the same bug I had about a failure on loading type1 module, but the following is worth a try:
1. run in a terminal:
```
sudo nvidia-xconfig
```2. ```
gksudo gedit /etc/X11/xorg.conf
```3. Comment out the line with "type1" in the modules section:
```
Section "Module"
    Load           "dbe"
    Load           "extmod"
#   Load       "type1"
    Load           "freetype"
    Load           "glx"
EndSection
```4. Log out and restart your Xserver: ctrl+alt+backspace

This is the actual workaround for my nvidia kernelmodule loading problem. Don't know about this type1 module.:confused:

HTH

---

### Post by Quikee on 2008-09-22
> **gspat said:**
> 
Does this mean that I have both 173 AND 177 installed simultaneously on this machine? I thought that software checks made that impossible (or close to it at least!).


No.. it means only that the modaliases for nvidia 173 were installed, not the driver itself. 

> **gspat said:**
> 
This is the first time I've seen this in any upgrades I've done...

what is missing in the line 

```
ls: cannot access /var/lib/dkms/nvidia/: No such file or directory
```


/var/lib/dkms/nvidia/ directory is missing... but it never said anything about this being a problem - quite the opposite - it looks like the driver compiled and installed OK.

---

### Post by Coleop on 2008-09-22
I am not sure if this might be your issue but I had the same problem every time the the nvidia driver is updated I have to copy the libglx.so from /usr/lib/xorg/modules/extensions to /usr/lib/xorg/modules.  If the old libglx.so file is there you will have to remove it before copying the new file.   It is so frustrating to me to have to do this but I can't find where to make it default to the /usr/lib/xorg/modules/extensions directory. I have had to do this every time but figured it out in Alpha 1.  Any suggestions for xorg to look to the extension directory for the driver would be appreciated and would save me a lot of time.

---

### Post by Sef on 2008-09-22
I couldn't load the 177 drivers, but the 173 drivers worked on my 8600 GT,

Update 1: 

> sudo gedit /etc/X11/xorg.confThat is not quite the correct code.   The correct code is ```
gksudo gedit /etc/X11/xorg.conf
```  With graphical applications, you need to use gksudo for Ubuntu and Xubuntu.  Kdesu with Kubuntu.

---

### Post by gspat on 2008-09-22
Nope it's a no-go... it just brings up the bulletproof x window and will only load up with either vesa or the nv driver...

I can go into hardware drivers and set it to be used, but it says that the driver is installed but not used... so, I go to appearances and try to turn on lower 3d stuff, but it asks me to let it install the 173 driver!!!??? I know this should not be the case!!!

btw... when I try to copy the symlink for libglx.so to the modules directory, it shows up as a broken link(!!??) but if I create a link of the link, it will copy to the folder successfully... is this a proper way to do this?

---

### Post by Nullack on 2008-09-22
> **hellibombelli said:**
> I'm not sure if this is the same bug I had about a failure on loading type1 module, but the following is worth a try:
1. run in a terminal:
```
sudo nvidia-xconfig
```2. ```
gksudo gedit /etc/X11/xorg.conf
```3. Comment out the line with "type1" in the modules section:
```
Section "Module"
    Load           "dbe"
    Load           "extmod"
#   Load       "type1"
    Load           "freetype"
    Load           "glx"
EndSection
```4. Log out and restart your Xserver: ctrl+alt+backspace

This is the actual workaround for my nvidia kernelmodule loading problem. Don't know about this type1 module.:confused:

HTH

I don't recommend running nvidia's x config. Neither does NVIDIA anymore they have a post about it on nvnews. What is recommended by Nvidia is to run an absolute minimal xorg.conf. Try to avoid specifying anything in the conf you dont need too lik that bunch of modules.

---

### Post by gspat on 2008-09-23
well.. I tried some more and tried using envyng like some other posts mentioned, but had no joy...

as I was watching the startup i saw this...

> *Preparing Restricted drivers...
mkdir: cannot create directory "/lib/modules/2.6.27-4-generic/volatile/": read-only file system   [Fail]

This is the only fail during startup, so it's probably the culprit...

Any ideas?

---

### Post by gspat on 2008-09-23
Scratch that... The error in the above post went away after I created a volatile folder under 2.6.27-4-generic...

now it says 

> * Preparing restricted drivers                             [OK]

but still not able to use the nvidia driver... sigh... anyone?

---

### Post by philinux on 2008-09-23
I'm booting with 27.3 as it loads the nvidia driver fine.

27.4 results in X going round complaining about low graphics but never getting to the login window. Have to reboot.

---

### Post by hellibombelli on 2008-09-23
You're right Sef, sorry for the mistake. Forgot to mention to run this command from a terminal.

At Nullack: I didn't know that. Before nvidia-xconfig I've tried a minimal config with no success.

---

### Post by Sef on 2008-09-23
> You're right Sef, sorry for the mistake. Forgot to mention to run this command from a terminal.

That's ok.  I have made that mistake too.  After all, life is goes better is you listen to others and correct your mistakes instead of insisting you are always right.

---

### Post by philinux on 2008-09-24
> **philinux said:**
> I'm booting with 27.3 as it loads the nvidia driver fine.

27.4 results in X going round complaining about low graphics but never getting to the login window. Have to reboot.

Just done todays updates, 24/9/08, and I can now boot 2.6.27-4. 177 driver working fine.

---

### Post by gspat on 2008-09-24
tried the updates and still no-go...

could someone show me an example of a minimalist nvidia based working xorg.conf please?

---

### Post by LaLLi on 2008-09-24
This is my minimalistic xorg.conf for my GF8600GT.
```
Section "Device"
	Identifier "NVIDIA Device"
	Driver "nvidia"
	Option "NoLogo" "True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by keep-on-smiling on 2008-09-24
hi

couple days back I installed Intrepid and enabled nvidia drivers as one of the first things "tweaked".

last night I did the relevant updates and that nvidia/kernel update took down my system - this morning I changed my tactic:

wiped the partition, did a fresh install, did every update available 

...and THEN enabled nvidia 

(courage in both my paws...), and this seems to work fine (OK niggling crashes with sound, but that's another thread)

here's to the first RC1 :) (getting champers ready)

---

### Post by gspat on 2008-09-24
Thanks LaLLi, tried your xorg.conf and it still won't play nice...

still get the lowres stuff window where it complains it failed to load the nvidia driver and have to change "nvidia" to "nv" to get it to load a desktop.

Sigh...

Any other ideas?

---

### Post by gspat on 2008-09-24
Oops.. Double post...

---

### Post by gspat on 2008-09-24
> **keep-on-smiling said:**
> hi

couple days back I installed Intrepid and enabled nvidia drivers as one of the first things "tweaked".

last night I did the relevant updates and that nvidia/kernel update took down my system - this morning I changed my tactic:

wiped the partition, did a fresh install, did every update available 

...and THEN enabled nvidia 

(courage in both my paws...), and this seems to work fine (OK niggling crashes with sound, but that's another thread)

here's to the first RC1 :) (getting champers ready)

That will probably be the step that finally fixes it for me... Was hoping to be able to finesse it to work though..

---

### Post by gspat on 2008-09-25
just tried using envyng on it to see if that would fix it, but nope.. still stubborn as ever!!!

What would make the system say it had loaded the nvidia modules during bootup but not be able to find them to use them?

---

### Post by GavinZac on 2008-09-25
Restricted drivers/jocket doesn't appear to work for me at all, and I tried installing the drivers off the nvidia website, only to get presented with low graphics mode.

---

