---
title: "Ubuntu keeps freezing up"
date: 2021-07-30
forum: Installation &amp; Upgrades
---

### Post by tmmls on 2021-07-30
Hi,

With this post I would like to ask a question.

I was running Ubuntu 14 LTS for a very long time, and it was running perfect. But, because it was outdated, I was planning on replacing it with the most recent LTS version, or even Linux Mint, which is based on Ubuntu LTS.

I downloaded version 20.x and wrote it on a dvd from which I booted. After launching up it runs perfect for a few minutes, but then keeps freezing. Sometimes for a few seconds, sometimes for a few minutes, sometimes forever and I need to force reboot.
I tried version 20.x and version 18. I tried using a boot DVD and a boot USB. I also tried Linux Mint the 2 most recent versions. I tried downloading the ISO files from multiple different locations. The result is always the same. 

I removed my old Ubuntu but I'm even not able to install the a new version because of the many freezes.

I'm using a Dell Precision T1650 with a NVIDIA Quadro P400 graphics card, and a Dell u3818dw monitor.

I've lost more then a week trying to install this.

Does anyone know how I can fix this?

Worst case scenario I have to reinstall the 14 LTS version

Thanks

---

### Post by ubfan1 on 2021-07-30
A shot in the dark -- your machine originally came with a 1GB video card, the P400 is 2GB.  Check what firmware/BIOS revision you have on your motherboard, and see if there were any PCI related changes on Top Of Lower Usable Device memory (TOLUD). Look at the syslog or dmesg for the pci mappings that get set up and see if you see any issues.  Fortunately your original OS was 64 bit Win7, so crazy BIOS changes like reducing the TOLUD to give the (non-existent) 32 bit  users more memory probably didn't happen (like some other 2011 era machine experienced).

---

### Post by TheFu on 2021-07-30
Try installing the supported nvidia proprietary drivers.  
**sudo ubuntu-drivers autoinstall**
should do it. Then reboot.  The driver version installed for that P400 GPU should be 460.xx.xx this week.
I have 
```
ii  nvidia-driver-460               460.91.03-0ubuntu0.18.04.1 amd64        NVIDIA driver metapackage
```
Always use the approved-by-Canonical drivers. **Do not** manually get drivers from nvidia.com.

Any sort of hardware problem can cause issues. Older machines often get stressed during a new install/upgrade process, so things that previously were fine stop being perfect.  The system logs should have errors or warnings. Check those out using the **journalctl** tool.  Issues could be anything.

Running 14.04 isn't an option, unless you prefer to be hacked.  Support for that release ended 2 yrs ago. It is very dangerous to keep using.
Most people should stay on the current LTS release for 2 yrs at a time.  20.04 is current. About a year from now would be a good time to plan the move to 22.04. That gives the team a few months to solve any initial quality issues from the April 2022 release date.

---

### Post by MAFoElffen on 2021-07-30
What TheFU suggested should work, except that is tempaory for you, because you haved installed, yet, you are running the LiveCD Environment.

if on the CD boot, you press the shift key until you see the 2 icons at the bottom of the screen... Just like the fist picture in the instructions in post #3 of my sticky post in my signature line... Press <ESC> Then press  <F6>. Enter <ESC>, then select "Try" by hitting the <Enter> key...

Try Ubuntu and see how it works. You won't be using any drivers yet, but you will need to eventually. For you, instead of just using one driver and trusting it works for your card... Install and on the page that says Full install (select), minimal, install updates (select), and Install 3rd party packages (select)... Ensure that you have that 3rd Party checkbox checked.

After the installation finishes On the reboot, see how it goes. After the initial setup screen's, open a terminal by selecting the desktop bacjground with your mouse, then pressing the <Ctrl><Alt><T> keys (at the same time). Then do:
```
sudo spt install ubuntu-drivers-common
```
That may or may not have installed you checked the 3rd Party packages checkbox duruing the install... But we need to make sure. That package will look at your NVIDIA Card and make appropriate mainline NVidia drivers available to your system, based on your GPU model.

Then select "Activities" in the uppper Left ofthe taskbar. Select the search bar in the center of your screen and start typing "Software & Updates'. Select that App.

When that starts, select the "alternate drivers". Once it gets there, it will query your NVidia GPU and display the drivers that should be appropriate for that GPU. There will be a list of NVidia proprietary driver, with the opensource Nouveau driver at the bottom.  It will go through an install phase, then when complete, it will say apply...

Try one near the top and see how it does. Play and see what works best for you.

---

### Post by TheFu on 2021-07-30
I completely missed the Live environment. Sorry.  I'd jumped ahead to the post-install stuff.

I've heard of people needing to use nomodeset with nvidia GPUs on 20.04, but I've not seen that myself - yet.

Whenever having issues with a fresh install, it is useful to read the release notes sooner than later.  I remember nvidia support wasn't good with initial 20.04 ISOs.  It isn't clear which ISO version you have.  If I google "ubuntu 20.04 release notes" ...  [https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes) is the first result.  In the "Known Problems" section is something about nvidia GPUs. One of the possible results is a frozen system.

---

### Post by tmmls on 2021-07-31
Thanks ubfan1, TheFu and MAFoElffen for all your feedback. This was very helpful.
Booting into "safe graphics mode" and starting the installation from this setup solved all my problems ...
It seems the NVIDIA graphics card was the issue.
Ubuntu works great again ...

Again, many thanks...

---

### Post by MAFoElffen on 2021-08-01
Good that all is going for you now and working for you.

Please use:Thread Tools > Mark this Thread As Solved, so that others can find your answer to help them with their's.

---

