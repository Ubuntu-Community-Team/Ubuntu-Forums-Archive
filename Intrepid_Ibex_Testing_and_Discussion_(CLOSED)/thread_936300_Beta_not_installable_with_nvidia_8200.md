---
title: "Beta not installable with nvidia 8200"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lem on 2008-10-02
The beta iso gets to starting x and pops up a message stating that you're in low graphics mode, followed by another asking if you want to reconfigure or troubleshoot.
Whatever you do here (including manually trying to stop/start gdm) ends up back at this prompt until you eventually lose your mind or boot back into Hardy.

Trying the 'install' option just drops me to a cli prompt. gdm start just gets me back to the situation above.

Hardy and Alpha2 both installed fine.

---

### Post by plun on 2008-10-03
This must be a detection error....

There is a new Jockey out today but it will probably not help you.
[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007871.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007871.html)

From CLI

```
sudo apt-get update && sudo apt-get upgrade
```

You can also install nVidias driver from CLI
```

sudo apt-get install nvidia-glx-177
```


About this driver
[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

Where to file a bug:
[https://launchpad.net/distros/ubuntu/+source/nvidia-graphics-drivers-177/+bugs](https://launchpad.net/distros/ubuntu/+source/nvidia-graphics-drivers-177/+bugs)

---

### Post by Lem on 2008-10-03
.

---

### Post by Lem on 2008-10-03
Thanks for that. Ok if anyone else stumbles into this - workaround is as follows.

Alt-F1 to get a CLI

```

sudo apt-get update
sudo apt-get install nvidia-glx-177
sudo nvidia-xconfig
sudo gdm stop

```

---

### Post by plun on 2008-10-03
Great ! Have fun with Intrepid.


Change wallpaper perhaps as first step  ....:D


It is probably also fixed now with latest Jockey

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/277419](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/277419)

---

### Post by hdhrnova on 2008-10-04
> **plun said:**
> Great ! Have fun with Intrepid.


Change wallpaper perhaps as first step  ....:D


It is probably also fixed now with latest Jockey

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/277419](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/277419)

next you will discover there are performance issues with the 8200gs and Interpid.   Try playing a Flash video off youtube.

---

### Post by fewjr on 2008-10-06
Hello folks,
     I have never gotten Hardy to work right with my new computer yet. This is the setup:

Gigabyte GA-M78SM-S2H AM2+/AM2 nVidia GeForce 8200 motherboard 

AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Dualcore processor

4GB G.Skill DDR2 800 (PC2 6400) Dual Channel RAM

2- Hitachi Deskstar P7K500- 500 GB SATA harddrives

Sony Optiarc DVDROM and Pioneer DVDR Burner master & slave 
on Primary IDE Channel (only IDE Channel)

USB Card reader in floppy bay

     I could get it to install with pci=nomsi. I had issues with wireless and video after install. I thought I would give ibex a try to see if things may be a little better for this chipset. I tried to install without any extra parameters...no go. Next I tried with pci=nomsi. It made it all the way to where it trys to load X. It tells me that loading X FAILED. I was running without quiet splash. It ends up at the Ubuntu$Ubuntu prompt. I will give your suggestion a try tomorrow when I get home from work. 

          Thanks
          fewjr

---

### Post by fewjr on 2008-10-06
Okay...I'm home. I ran>

```
sudo apt-get update
sudo apt-get install nvidia-glx-177
sudo nvidia-xconfig
sudo gdm stop
```

It seems to have done the trick. The system is being installed as we speak. I guess we'll see what happens after the install is done.

---

### Post by fewjr on 2008-10-06
Well after install was done I rebooted....went to black screen with blinking cursor. What now I wonder.

---

### Post by Lem on 2008-10-06
Press ctrl+F1 and repeat the process above for your new install. Then reboot.

You might want to read this first though;
[http://ubuntuforums.org/showthread.php?p=5901853](http://ubuntuforums.org/showthread.php?p=5901853)

---

### Post by tydfil on 2008-10-07
Follow the advice and the nvidia driver is indeed installed, but it is so unstable on my machine (XFX8200) Phenom 8450) as to be unusable.  Contant flicker wehn mouse is at top of screen and sometimes when an app is one top of another.

Todays update seems to have fixed a few of my problems.  Now if I could only have full graphics accelleration........................

---

### Post by tydfil on 2008-10-07
Problem according to xorg error log is that 8200 chipset is "unsupported".

Shame the driver does not work properly.

---

