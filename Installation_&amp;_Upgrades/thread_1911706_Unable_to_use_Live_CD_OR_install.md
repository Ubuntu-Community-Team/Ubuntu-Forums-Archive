---
title: "Unable to use Live CD OR install"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by malkuth123 on 2012-01-19
I have a new machine. I am unable to run the live cd nor install (using wubi). The problem is that I cannot get an X display, therefore am unable to continue installation nor run the GUI for live cd. The machine has winblows installed, and it operates fine.

Machine: HP TS 520-1010
Video: NVIDIA GeForce GT 5xx 

If I attempt to boot, I can get progress by using the nomodeset and noapic options on boot. The screen flashes several times and eventually the lightdm process dies. I can get a console by using the ctl/alt/f1 key

From the console (tty) I have run a couple of diagnostics.
lspci reports VGA compatable nVidia Corp GF106 (GeForce GT 555m)
lsmod points drm to nouveau and video to nouveau
The dmesg reports Console Colour VGA 80x25
init: lightdm process terminated with status 1
The Xorg.log reports /usr/share/X11/xorg.conf failed to load module nvidia
drm failed to open device 
segfault in libXi.so.6.1

Windows reports the frequency at 60.

I can boot easily into CLI using a standard tty (ctlr/alt/f1) but that is as far as I am able to go. Since setup has not been able to complete, (either live cd or wubi install), I cannot connect the computer to the internet to obtain the nvidia drivers, etc.

I can boot the computer into winblows, so can possibly obtain needed software that way, however, I am clueless as to where to put it so that wubi can make use of it on boot. Note that I cannot boot the wubi installation, because when the lightdm process fails, it causes a reboot of the machine.

Any assistance or further troubleshooting would be greatly appreciated, as I do not want to continue with winblows on this machine.

---

### Post by mips on 2012-01-19
Have you tried using the alternate install cd?

I stopped using the live/desktop cd a long time ago due to issues like this.

---

### Post by malkuth123 on 2012-01-20
What is the "alternate install cd", and how do I obtain it?

---

### Post by GhostOfTomJoad on 2012-01-20
> **malkuth123 said:**
> What is the "alternate install cd", and how do I obtain it?

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Here you go.

---

### Post by malkuth123 on 2012-01-20
Well, I used the alternate install cd. I was able to complete the install process. I then installed the nvidia-current package. Now I can get a login screen, but the second I put in my password, the screen starts flashing, etc. I do get a glimpse of the nvidia splash screen.

How/where is the xorg.conf file with the "new and improved" lightdm? If I could get to some kind of configuration file for video, I might be able to get a screen up.

---

