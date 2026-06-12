---
title: "Alienware MX17 64bit quad - NIVIDA graphics"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by reegus on 2010-03-09
Hi all.
I am relatively new to Ubuntu, however since discovering it i have dual systemed it on each of my laptops.  i would not consider myself too techy, but i can usually solve most probs with a bit of patience and forum surfing.

My question in this case is to do with my Alienware MX17 64bit sys.  It has Win 7 on it and of course Ubuntu.  I am having difficulty with the graphics drivers as when i try to enable the downloaded prop drivers, (Nividia 173, and 185 recommended) the system just hangs with a blank screen, leading to me having to do a re-install.  It is a blank (as in utterly no display, off), screen, not a displaying 'black' screen.

I would really appreciate a hand here as while the standard graphics are ok, they are a bit squished, and i don't get the cool warpy effect on the windows with enabled drivers.

I got it working with my HP touch screen lappy, and was impressed with how easy the process was, even the TS operation works.

I am guessing that i need a more specific driver?

Thanks in advance,

Reegus.

---

### Post by tommcd on 2010-03-09
Please provide some more details ...
> **reegus said:**
> 
My question in this case is to do with my Alienware MX17 64bit sys. 
Which version of Ubuntu did you install?? The current version is 9.10 "Karmic Koala". Did you install that? Or did you install an earlier version (like 8.04 LTS??). And did you install the 64bit version of Ubuntu or the 32bit version?? 
> **reegus said:**
> 
 I am having difficulty with the graphics drivers as when i try to enable the downloaded prop drivers, (Nividia 173, and 185 recommended) the system just hangs with a blank screen, leading to me having to do a re-install.
What Nvidia graphics card do you have in your Alienware system? If you do not know, then open a terminal in Ubuntu (applications > accessories > terminal) and type:
```
lspci | grep -i vga
```
and hit enter. It should display what graphics card you have. For example, on my system (running Slackware at the moment):
```

bash-3.1# lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
bash-3.1# 

```
Depending on which Nvidia card you have, you should either install the 173 or the 185 driver, but *not* both. Installing more than one Nvidia driver will cause problems, if that is what you have done.
You can see which Nvidia cards each driver supports here:
For the 173 driver:
[http://packages.ubuntu.com/karmic/nvidia-glx-173](http://packages.ubuntu.com/karmic/nvidia-glx-173)
and the 185 driver:
[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)
Note that there is some overlap for which cards each driver supports. You should probably use the newest driver that supports your card. For example, if you were using the GForce 7100 GS, which is listed as supported by both the 173 and the 185 drivers, you should probably use the 185 driver, since it is newer.
> **reegus said:**
> 
I would really appreciate a hand here as while the standard graphics are ok, they are a bit squished, and i don't get the cool warpy effect on the windows with enabled drivers.
Do a clean install of Ubuntu, (so you are starting from a clean slate). Install the proper driver, and reboot. Then open a terminal and run:
```

glxinfo | grep -i direct

```
It should report:
```

bash-3.1$ glxinfo | grep -i direct
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
bash-3.1$ 

```
or something similar. The important part is **direct rendering: Yes**, which indicates that 3D is properly enabled.
You may want to disable compiz until you get the proper driver installed and enabled ok.
Write back if you need more help. And tell us which version of Ubuntu you are running, and whether it is 32bit or 64bit, and what nvidia card you have., and what nvidia driver you have installed.

And welcome to the Ubuntu forums!!

---

### Post by drbcladd on 2010-03-19
Just installed Karmic on a similar machine (SLI 260M cards). Had exactly the same problem for a while: boot to black screen, boot to recovery and reset xorg.conf and it works...some of the time.

So, thought and thought. Got the NVIDIA-Linux-x86_64-195.36.15-pkg2.run driver (the one pointed to in the NVidia site) and thought some more. 

My solution: Boot to Setup. Goto Advanced -> Graphics Settings. Disable Hybrid Graphics and disable Integrated Graphics. Reboot and the default X drivers look better. 

Then follow the instructions on running the NVidia install: 

Ctrl-Alt-F1 to get console. Log in.

```
sudo stop gdm
```

To stop X.

```
sudo sh ./NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```

Say yes to all the questions

```
sudo start gdm
```

To restart X; you'll see the NVidia logo _and_ nvidia-settings should work.

It worked for me, in any case. Now I am updating all the packages on the new machine. Good luck.

---

