---
title: "Hardy NVIDIA module failed to load"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by xevix on 2008-02-17
After latest update (linux-image-2.6.24-8-generic) the nvidia kernel module no longer seems to load, kdm fails to load and so does Xorg.  `lsmod | grep nvidia` returns nothing.

Xorg.0.log

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Fixed:

- upstream 2.6.24*9 fixed it.

---

### Post by mohnkern on 2008-04-25
Exactly the same thing here.  NO Nvidia module loaded, and no screens.

Any Solution?

---

### Post by mohnkern on 2008-04-26
This solved my problem:

sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall

All on one line.

did that, rebooted, and came up just fine.

Someone suggested to run this first:

sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall


However that's only if you manually compiled the NVIDIA drivers.

---

### Post by edfromballarat on 2008-04-27
I had a lot of trouble too with my 7600 GT. Repository drivers wouldn't work.  Envy dito (coz they are basically the same thing).  I kept getting errors when I ran the NVIDIA.run file that downloaded directly from the driver link on NVIDIA.com when selecting 7 series, Linux x86.  Turns out this is the 16_ series driver, and there is a newer driver available from the old driver list (go figure) [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html), that is 171.  This installed well and the driver worked.  So if people are having trouble with the repo drivers, if you are happy to follow the instructions on the NVIDIA wiki (can be quite complicated for a NOOB) then try this.

The good news for those who have experienced the pain of crashing the x-server by fiddling with /etc/X11/xorg.conf, with Hardy Herron instead of getting a BSD (not just for Windows eh!) you get a VESA loaded 640*480 GUI to select monitor and graphics card.  While you are searching on the internet for solutions to your graphics driver problem (like you are doing now!) you can upsize the resolution by going to the monitor tab, clicking where it says "generic screen" and you'll get a list.  Go to generic, then next tab pick your screen resolution. Click okay.  Restart the x-server (or just restart the whole computer if you don't know how to do this) and away you go!  Hope this helps.  I've done my driver configuring for the next 6 months, now to play with Compiz!

---

### Post by ccabal on 2008-04-28
Thanks ALOT mohnkern,
as you said, this did it:

sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall



so what exactly was the problem?  Why didnt it work "out of the box" ??

---

### Post by jblackhall on 2008-04-29
> **ccabal said:**
> Thanks ALOT mohnkern,
as you said, this did it:

sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall



so what exactly was the problem?  Why didnt it work "out of the box" ??

Have you checked to make sure you're using the current Hardy kernel?  Run uname -r via terminal and see what comes up.  If it's a kernel version below 2.6.24-16 (the current Hardy kernel), this could be why: You're using the old Gutsy kernel still.  That command is simply installing Gutsy kernel's restricted modules package so it works with the old kernel you're running.  If you're using the correct Hardy kernel, then I dunno what the problem is.

---

### Post by mohnkern on 2008-04-29
Here' my imperfect understanding of the situation:

Whenever you update a kernel, you need new video drivers (well, generally).

the Nvidia drivers are not under the standard GPL, so they are "restricted."  You have to install them separately so you know you're under a different licensing agreement.

On a fresh install, it installs a set of drivers that will "work" but are not the best, so you can't do all the desktop effects.

ON an upgrade, you've probably already installed the restricted drivers, so your xorg.conf file is looking for them, however when you upgrade the kernel, you don't have the right driver, so you have to create a new one.

We have this same problem in RHEL, where every time we do a kernel update, we have to compile a new set of video drivers.

It falls under that black magic known as X11, which I still don't fully understand.

---

### Post by nazg00l on 2008-05-11
> **edfromballarat said:**
> I had a lot of trouble too with my 7600 GT. Repository drivers wouldn't work.  Envy dito (coz they are basically the same thing).  I kept getting errors when I ran the NVIDIA.run file that downloaded directly from the driver link on NVIDIA.com when selecting 7 series, Linux x86.  Turns out this is the 16_ series driver, and there is a newer driver available from the old driver list (go figure) [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html), that is 171.  This installed well and the driver worked.  So if people are having trouble with the repo drivers, if you are happy to follow the instructions on the NVIDIA wiki (can be quite complicated for a NOOB) then try this.

I just upgraded from Gutsy and want to emphasize this good advice. I had the exact same situation. 7600GT, dual-head setup, system previously configured manually (drivers downloaded from nVidia), X crashing out of the box after upgrade. The version of nVidia drivers is crucial! The 169 one does not work. **[COLOR="DarkRed"]Neither does the newest one, 173.08![/COLOR]** 171.06.01 worked. Good job, ***edfromballarat***!

> **edfromballarat said:**
> The good news for those who have experienced the pain of crashing the x-server by fiddling with /etc/X11/xorg.conf, with Hardy Herron instead of getting a BSD (not just for Windows eh!) you get a VESA loaded 640*480 GUI to select monitor and graphics card.

Yeah, sure. It took some brutal killall sprees to stop gdm from respawning (simple **gdm stop** did not work, for some reason)... ;)

---

### Post by kabronkline on 2008-05-13
I had similar problems after a Kubuntu amd64 upgrade from 7.10 to 8.04. Driver version 169.12 has always worked best for me (i.e. no screen crashing), thus I have found it best to stick with this version.  After upgrade kde would not and I was receiving errors mentioned in this thread. Following is a summary of the fix I performed.

**1.** Remove the 'nvidia-glx-new' package installed during upgrade via the following command:[INDENT]sudo apt-get remove nvidia-glx-new
[/INDENT]**2. **Downloaded the driver installation file that works best with your graphics card from Nvidia's official website, here:[INDENT][http://www.nvidia.com/object/linux_display_amd64_169.12.html](http://www.nvidia.com/object/linux_display_amd64_169.12.html)
[/INDENT]Alternatively, for a direct download, run the following command to download the appropriate '.run' file into your home directory (make sure you subsititute the link in the below ommand with the link of the driver '.run' desired):[INDENT]cd $home && wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)

[/INDENT]This driver install file (i.e. the '.run' file) corresponds to my amd64 architecture and the fact that the specific version (i.e. 169.12) works best for my system. If you have a another driver version installed which varies from the version in my example here, by all means make sure you substitute the driver install file I am using with the correct driver version for your system.

As a side note, running the following command is typically a good place to start when determining your graphic card:[INDENT]lspci -v | grep VGA

[/INDENT]**3. **After downloading the '.run' file into your home directory, run the following commands:[INDENT]cd $home && sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run

[/INDENT]This will run you through a guided self-explanitory install. After you have completed the install, run the following command to reboot Linux:[INDENT]sudo reboot

[/INDENT]If you are daring but convinced this all may work you can simple run this command:[INDENT]sudo apt-get remove nvidia-glx-new && cd $home && wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run) && sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run && sudo reboot
[/INDENT]And of course, make sure to change the following link, when neccesary, with the link to the desired '.run' file:[INDENT][http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)
[/INDENT]

---

### Post by hpesoj on 2008-05-15
Thanks mohnkern.  Signed up just to say that your advice worked :).  I have just installed Hardy, without updating from the previous version, and my kernel was definitely the correct version but I was still having the problem (booting in low graphics mode no matter what I did).  Thanks again!

---

### Post by Anthalasa on 2008-06-21
Thank you kabronkline for a wonderful explanation on how to fix this problem.  Worked really well for me. :)

---

### Post by CrazyTycoon on 2008-06-22
so I've gone through all the steps and I'm so stuck...got gdm killes and tried to install the NVIDIA driver and it says its missing the kernal source tree for compiling the driver...can anyone help?

---

