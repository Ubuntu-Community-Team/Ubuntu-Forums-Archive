---
title: "Installation of nvidia drivers"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by dsfx3d on 2018-03-10
Hi,

I'm fairly new to ubuntu and can't figure out how to properly install nvidia-drivers on my system.

I'm running Ubuntu 16.04.03 on hp-pavilion 15 | geforce 740m

I've tried many ways for installing gpu drivers but they never work; this is what i've done:

**0. Disabled nouveau**

**1. Installation from terminal**:
tried installing from terminal but the system boots in low graphic mode. I purged nvidia-* to fix that, then tried lspci to check VGA compatible controllers

lspci returned something like this:

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
.
.
.
0a:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

```

I assumed that maybe my graphic card doesn't support VGA display and that's why low graphics mode, so I googled again and downloaded a runfile from nvidia
[B]
2. Manual Installation
[/B]
stopped lightdm > switched to tty > started the runfile with option '--no-opengl-files' > the drives installed and I rebooted. 
after reboot i tried nvidia-detector, it returns none. I thought maybe the drivers weren't installed so I opened Software and Updates >> Additional Drivers: it said the device is using alternative drivers and 'continue using manually installed drivers' was selected.

I'm confused please help with the installation

---

### Post by Autodave on 2018-03-10
Whenever possible, never install drivers from a website. Always try the repositories first.

First, you need to remove the one you already installed.  In a terminal:

sudo apt purge nvidia*

Now, go to where you went before: software -> updates and see what one is recommended.  Start with that one.

---

### Post by cruzer001 on 2018-03-10
Also note worthy is the Ubuntu PPA

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

[https://www.howtogeek.com/242045/how-to-get-the-latest-nvidia-amd-or-intel-graphics-drivers-on-ubuntu/](https://www.howtogeek.com/242045/how-to-get-the-latest-nvidia-amd-or-intel-graphics-drivers-on-ubuntu/)

---

### Post by monkeybrain20122 on 2018-03-10
> **Autodave said:**
> Whenever possible, never install drivers from a website. Always try the repositories first.

First, you need to remove the one you already installed.  In a terminal:

sudo apt purge nvidia*

Now, go to where you went before: software -> updates and see what one is recommended.  Start with that one.

If he installed from the run fie sudo apt purge would not work, it only works for packages installed through apt obviously (.deb or repository) OP has to manually find all nvidia remnants and delete them manually.

But I totally agree that OP shouldn't have installed from the .run file.

---

### Post by monkeybrain20122 on 2018-03-10
> **dsfx3d said:**
> Hi,

I'm fairly new to ubuntu and can't figure out how to properly install nvidia-drivers on my system.

I'm running Ubuntu 16.04.03 on hp-pavilion 15 | geforce 740m

I've tried many ways for installing gpu drivers but they never work; this is what i've done:

**0. Disabled nouveau**

**1. Installation from terminal**:
tried installing from terminal but the system boots in low graphic mode. I purged nvidia-* to fix that, then tried lspci to check VGA compatible controllers

lspci returned something like this:

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
.
.
.
0a:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

```

I assumed that maybe my graphic card doesn't support VGA display and that's why low graphics mode, so I googled again and downloaded a runfile from nvidia
[B]
2. Manual Installation
[/B]
stopped lightdm > switched to tty > started the runfile with option '--no-opengl-files' > the drives installed and I rebooted. 
after reboot i tried nvidia-detector, it returns none. I thought maybe the drivers weren't installed so I opened Software and Updates >> Additional Drivers: it said the device is using alternative drivers and 'continue using manually installed drivers' was selected.

I'm confused please help with the installation

In the other thread you started you were already told not to install from the ./run file, and if you have already delete everything from it and install from the repository instead.

Also do you have an Optimus machine? (two gpus, an intel card and a Nvidia card) You need to go through some hoop to get it to work. Like I said on the other thread, google Ubuntu Optimus

---

### Post by mc4man on 2018-03-10
I have a lenovo with 755m & a lenovo with a 6**m,  never had any issue using the packaged nvidia drivers on either. 
It was mentioned in other thread about using nvidia-390, just to note those are not in the standard Ubuntu 16.04 repo's, are in that ppa. For 16.04 there are the nvidia-384 drivers which should work fine.

As far as installing the blob via a .run, not the best idea on an optimus machine. I believe you need to run an uninstall script to really get rid of.
As far as disabling nouveau before you started the orig. packaged nvidia driver install, also not a good idea.

If you can't  manage to undo the nouveau disable & the .run install completely then maybe save yourself some time & aggravation & do a fresh install of 16.04 using either the 16.04.1 image or the 16.04.4 image.

(- 16.04.4 image may be better, nvidia users who want to maintain prime sync on 16.04 may need to keep or add the 4.4.0 kernel that's on the 16.04.1 image but not on the 16.04.4 image, it can be added to a 16.04.4 image install later if the need arises when 16.04.5 HWE comes around with the currently 'bad' 4.15 kernel

---

