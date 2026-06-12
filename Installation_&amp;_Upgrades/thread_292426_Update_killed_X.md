---
title: "Update killed X"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by goldenatom on 2006-11-03
I just applied a kernel update and when I rebooted X wouldn't start up. I had the beta nvidia driver installed. I remember someone telling me (after this happened) that every time a change to the kernel was made, I would have to reinstall the nvidia drivers. Can someone explain why this is the case...and what can I do to reinstall the drivers. When I try 

sudo apt-get install nvidia-glx

I get some error saying that its uninstallable. I'm not even sure if thats what I should have tried.

---

### Post by towsonu2003 on 2006-11-03
That someone was correct. Each module (driver) has to be compiled for the specific kernel you are running. you experience this problem because you compiled your own module for your own kernel version. 

I think you will find this link interesting and helpful: [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

as per "sudo apt-get install nvidia-glx", what is the exact error message? someone might be able to help you with that...

---

### Post by todak on 2006-11-03
Try this from the text console after booting up: sudo apt-get install xserver-xorg

That should get you into the GUI after installing and log-out/log-in. Otherwise, reboot and it should be working.:)

---

### Post by BobBlum on 2006-11-03
Press Enter to get a prompt.  Then log in.

At the command line, type the following:  sudo apt-get install xserver-xorg

This was suggested in a blog located at [http://www.planetmy.com/blog/](http://www.planetmy.com/blog/)

It worked for me.

---

### Post by goldenatom on 2006-11-04
That did the trick, thanks all.

---

### Post by pain of salvation on 2006-11-04
I have the same problem after updating the kernel.

Tried apt-get install nvidia-glx, but it says this package needs nvidia-kernel-1.0.9625

Tried apt-get install xserver-xorg, but it says that the new version of this package is already installed.

Can someone help me :confused:

---

### Post by towsonu2003 on 2006-11-04
> **pain of salvation said:**
> I have the same problem after updating the kernel.

Tried apt-get install nvidia-glx, but it says this package needs nvidia-kernel-1.0.9625

Tried apt-get install xserver-xorg, but it says that the new version of this package is already installed.

Can someone help me :confused:
Maybe [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182) ?

It may be an issue with an out-of-sync mirror... Try 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx
``` again. hopefully this time the problem will be solved.

---

### Post by Absolute Nirvana on 2006-11-04
> **pain of salvation said:**
> I have the same problem after updating the kernel.

Tried apt-get install nvidia-glx, but it says this package needs nvidia-kernel-1.0.9625

Tried apt-get install xserver-xorg, but it says that the new version of this package is already installed.

Can someone help me :confused:

I have the same problem on a clean install of edgy I did today when trying to install the beta nvidia 9625 driver. I had no problems with the same driver before I did the clean install.

---

### Post by pain of salvation on 2006-11-04
> **towsonu2003 said:**
> Maybe [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182) ?

It may be an issue with an out-of-sync mirror... Try 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx
``` again. hopefully this time the problem will be solved.

didn't work...

---

### Post by towsonu2003 on 2006-11-04
> **Absolute Nirvana said:**
> I have the same problem on a clean install of edgy I did today when trying to install the beta nvidia 9625 driver. I had no problems with the same driver before I did the clean install.

> **pain of salvation said:**
> didn't work...

hmm, I won't be able to help further with this. hopefully someone else (who is actually using edgy) can help... 

If you cannot find a solution, please briefly comment to the bug report I linked above describing the problem. [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67182)

In the meantime (while waiting for help), you can recover your X with ```
sudo dpkg-reconfigure xserver-xorg
``` and choosing the **nv** driver instead of the **nvidia** driver. Once you do that, start X with the command startx. If that doesn't recover X either, try **vesa** instead of **nv** (by reissuing the above command).  

I'm pretty sure you're frustrated at this point -but patience ;)

---

