---
title: "LiveCD works, but install fails"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by bexmex on 2005-07-28
I have a Dual 2GHz G5 running UBuntu 5.04. If I use the LiveCD and opt for the "live-power4" option for the g5 specific configuration, it boots fine and everything seems to work. So I decided to install it.

Well, now the screen is totally blank when I boot it. I cant do anything at all. It doesn't even seem to complete the startup. Im not even sure if the right kernel was loaded. Apparently the installer didn't seem to do as good of a job as the LiveCD did. Odd, because on the forums Im hearing the exact opposite...

Is there a quick and easy way to copy ALL the LiveCD configuration to the main disk? Kernel, xorg config, the whole thing?

In lieu of that, what is the most likely set of files that I need to move over manually?

I mounted the original filesystem with:

mkdir /mnt/drive/
mount -t ext3 /dev/sda3 /mnt/drive

so I can access the logs and configuration... but Im having a hard time tracking down what exactly went wrong dring the install. I dont even have an xorg.log to look at.

any tips?

---

### Post by autocrosser on 2005-07-28
Well--you could try to install with the "expert" option or ask for powerpc4 -- ask for options (help or just <tab>) where the install disc boots & select one of those modes-- It sounds like the installer is selecting the wrong kernel--I would guess powerpc-smp (for G4 duals)--once you have a "real" install, you can use Synaptic to get the kernel you "really" want.....

If you can get to what is installed right now---look at the contents of /boot--that is where the kernel image(s) are.... also, look at /etc/X11/xorg.conf & post the info--I'll look & try to steer you where you need to go---

As for the LiveCD--it uses a ram disk to run--the .conf files won't run your system (in their .conf it states to use only for the LiveCD) :roll: --

---

### Post by bexmex on 2005-07-30
OK, got it working this time...

I didnt have an xorg.conf, which confused me. So I checked the master install log, and it looked like it was interrupted. DUH! The install didn't work because I got impatient! I installed and rebooted, and had a blank screen for 5 minutes. I thought something was wrong, but it was just taking a long time to finish the install.

I did the expert option the second time, and chose the linux-image-2.6.10-power4 kernel. After I rebooted, I just went out for lunch. When I got back, Unbutu was up and running. Pretty damn snapppy, I might add...

Thanks!

---

### Post by autocrosser on 2005-07-31
Glad to hear it--Any other probs--just ask--someone will have the answer--

---

