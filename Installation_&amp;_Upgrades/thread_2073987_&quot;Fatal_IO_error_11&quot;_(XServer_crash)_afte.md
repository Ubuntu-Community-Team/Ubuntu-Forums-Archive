---
title: "&quot;Fatal IO error 11&quot; (XServer crash) after launching Thunderbird"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by blueSpirit on 2012-10-20
Hello,

when starting the thunderbird on my brand new 12.10 installation (installed from scratch), the xserver is rebooting.

This is from from .xsession-errors:
```
compiz (core) - Warn: Attempted to restack relative to 0xe00009 which is not a child of the root window or a window compiz owns
** Message: moving back from GtkStatusIcon to indicator
(nm-applet:2058): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(polkit-gnome-authentication-agent-1:2067): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(gnome-settings-daemon:2017): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(nautilus:2053): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-session[1935]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(bluetooth-applet:2059): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0
(gnome-terminal:2256): Gdk-WARNING **: gnome-terminal: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
(telepathy-indicator:2231): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
(gnome-fallback-mount-helper:2052): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

```And this from Xorg.0.log.old:

```
[    49.995] (II) XKB: generating xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    76.664] (EE)
[    76.664] (EE) Backtrace:
[    76.664] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7fd617924ac6]
[    76.664] (EE) 1: /usr/bin/X (0x7fd61777c000+0x1ac8f9) [0x7fd6179288f9]
[    76.664] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fd616aa2000+0xfcb0) [0x7fd616ab1cb0]
[    76.664] (EE) 3: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7fd614582000+0x102b1) [0x7fd6145922b1]
[    76.664] (EE) 4: /usr/lib/xorg/modules/libshadowfb.so (0x7fd61351a000+0x22e1) [0x7fd61351c2e1]
[    76.664] (EE) 5: /usr/bin/X (miPaintWindow+0x220) [0x7fd617906b10]
[    76.664] (EE) 6: /usr/bin/X (miWindowExposures+0xc8) [0x7fd617906c58]
[    76.664] (EE) 7: /usr/bin/X (miHandleValidateExposures+0x68) [0x7fd61791cfd8]
[    76.664] (EE) 8: /usr/bin/X (MapWindow+0x27f) [0x7fd6177fd6ff]
[    76.664] (EE) 9: /usr/bin/X (0x7fd61777c000+0x50290) [0x7fd6177cc290]
[    76.664] (EE) 10: /usr/bin/X (0x7fd61777c000+0x55a51) [0x7fd6177d1a51]
[    76.664] (EE) 11: /usr/bin/X (0x7fd61777c000+0x4456a) [0x7fd6177c056a]
[    76.664] (EE) 12: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fd61572776d]
[    76.664] (EE) 13: /usr/bin/X (0x7fd61777c000+0x448ad) [0x7fd6177c08ad]
[    76.664] (EE)
[    76.664] (EE) Segmentation fault at address 0x7fd614381668
[    76.664]
Fatal server error:
[    76.664] Caught signal 11 (Segmentation fault). Server aborting
[    76.664]
[    76.664] (EE)

```Other apps as firefox, software center or skype are working fine. Starting thunderbird with gdb/strace give no reasonable output.

When booting the LiveDVD everything works fine. I first installed Ubuntu from an USB-Stick on my SSD, now I repeated it with an DVD on a regular HDD - on both the the same error. In the next step I will try to downgrade to 11.04 - but if it's a topic with my video card (nvidia 640 GT) I will have there the same problems (?).

Charly

---

### Post by blueSpirit on 2012-10-20
Anyone with an idea?

I'm wondering, why just thunderbird let's the XServer die. When starting thunderbird with --safe-mode, the safe-mode dialog appears, but the crash follows...

---

### Post by funicorn on 2012-10-20
You are asking a plausible question. Xserver crashed due to loading some unusable library file, which is called for by certain application. Yet it's unlikely only thunderbird calls for that library then crashes Xserver. The crash itself indicates Xserver  went wrong working with certain library in your system, which for most cases fell on the libraries installed via your video driver, the nvidia binary driver for example.

---

### Post by blueSpirit on 2012-10-20
I've just installed 12.04 and this version doesn't support my video chard -> wrong screen resolution. Thunderbird is starting, but applications like jockey-gtk are crashing, thus I cannot configure the nvidia driver by GUI. I will go back to 12.10...

@funicorn: My questions would be: 

[LIST]
[*]Why is it working on the LiveDVD and not on my installed system? What is the difference? Kernel flags/boot options, drivers, ...?
[*]Can I do something else than waiting for a fix by Ubuntu?
[*]How can I identify the causing library - e.g. to be aware of future crashes. Would it make sense to downgrade to an ancient version of thunderbird?
[/LIST]
I already tried to start thunderbird with "DISPLAY=':0' thuderbird -g" from tty - but it's only caused by thunderbird: it's just terminating because Xserver is gone.

---

### Post by blueSpirit on 2012-10-21
After updating the system I was able to switch to the binary nvidia driver - and now also the screen resolution is supported. I ve attached the xorg.log of the working 12.04 with nvidia driver.

---

### Post by funicorn on 2012-10-21
OK I see libwfb.so in the xserver log. This library is used to provide software 3D acceleration for certain NVIDIA cards, i.e., the newest ones with Geforce8 series module which are not fully supported by nvidia binary driver. 

The answers to your questions would be:

[LIST]
[*]Ubuntu livecd use nouveau, the open source nvidia driver by default. This driver works more consistently on 2D rendering as for certain NVIDIA cards, whereas lacks of genuine 3D acceleration support.
[*]If your hardware platform deploys NVIDIA OPTIMUS technology, the best relief so far is to install bumblebee. OPTIMUS means you have both integrated Intel gpu and nvidia gpu working online.
[*]If it's only thunderbird crashing your Xserver, you can install thunderbird-dbg, run 'gdb thunderbird' in gnome-terminal and trace what happens when the crash takes place. However I really don't see this coming. If thunderbird makes a crash, so does firefox. They are basically the same thing.
[/LIST]

> **blueSpirit said:**
> After updating the system I was able to switch to the binary nvidia driver - and now also the screen resolution is supported. I ve attached the xorg.log of the working 12.04 with nvidia driver.

---

### Post by blueSpirit on 2012-10-21
> **funicorn said:**
> Ubuntu livecd use nouveau, the open source nvidia driver by  default. This driver works more consistently on 2D rendering as for  certain NVIDIA cards, whereas lacks of genuine 3D acceleration support.
My installed system also crashed with nouveau. I even removed everything (exept nvidia-common) - because I had some problems after switching to nvidia and back - and thunderbird still caused the crash.
> **funicorn said:**
> If your hardware platform deploys  NVIDIA OPTIMUS technology, the best relief so far is to install  bumblebee. OPTIMUS means you have both integrated Intel gpu and nvidia  gpu working online.
Ok, I will try bumblebee and give feedback.
> **funicorn said:**
> If it's only thunderbird crashing your Xserver, you can install thunderbird-dbg, run 'gdb thunderbird' in gnome-terminal and trace what happens when the crash takes place. However I really don't see this coming. 
gnome-terminal is a bad choice when the xserver crashes. Further more, you have to call "thunderbird -g" since thunderbird in the path is only a script (at least on ubuntu). I already did so, see
> **blueSpirit said:**
> ready tried to start thunderbird with  "DISPLAY=':0' thuderbird -g" from tty - but it's only caused by  thunderbird: it's just terminating because Xserver is gone.
The problem is, that thunderbird causes no SEGV or similar, so it would be really challenging to set the breakpoint directly before the crash. Do you have a tip for me, how to do it?
> **funicorn said:**
> If thunderbird makes a crash, so  does firefox. They are basically the same thing.
Firefox definitly runs stable, while thunderbird crashes. I'm also wondering about this... > **blueSpirit said:**
> Other apps as firefox, software center or  skype are working fine. Starting thunderbird with gdb/strace give no  reasonable output.
But anyway, thanks a lot for your time and care. So the next thing would be bumblebee - please cross your fingers ;) If it fails, maybe I can compare Xorg.log of the LiveDVD with my current one, to find the difference...

UPDATE: First, now also meld crashes. It runs fine one time - and after a while it crashes now like thunderbird. Further more I booted the liveDVD - and now the crash appears there too :( I compared it's Xorg.conf with mine, and they are quite the same - expect some different paths.

---

### Post by funicorn on 2012-10-21
Good luck. just that before you  proceeding make sure your hardware does deploy NVIDIA OPTIMUS, that's crucially important.

---

### Post by blueSpirit on 2012-10-21
Now I remember why I don't like all these graphical tools: Switching to nvidia driver succeeded (in the GUI) but after reboot the desktop doesn't fill my screen. Xorg.log says that loading nvidia failed, and I should check my kernel log. But kern.log doesn't say a word about this failure.

The reason was, that installing nvidia-current failed, because the "kernel sources" cannot be found. This is only visible with "sudo apt-get install --reinstall nvidia-current". Installing linux-sources doesn't help - but installing "linux-headers-generic". So after that - and restarting lightdm everything looks fine and thunderbird is working. So it seems that thunderbird requires some feature, which makes the nouveau crashing... but not nvidia.

@bumblebee: After installing I realized that I had to check "lspci -vnn | grep '\''[030[02]\]'" first - which of course showed me, that my system does not support Nvidia Optimus - since it's a workstation and no notebook.

---

### Post by funicorn on 2012-10-21
Finally I peered your bingo. All comes from that the kernel interface for nvidia-current can't be built because of missing headers. 'apt-get purge' anything you installed relevant to nvidia-current, then start this over with:
```

sudo apt-get install linux-source 
sudo apt-get install linux-headers-generic 
sudo apt-get install linux-image 
sudo apt-get install nvidia-current 
jockey-text -e xorg:nvidia_current
sudo reboot

```

---

### Post by jusmop on 2012-11-03
I experienced exactly the same issues with both the nvidia proprietary driver not being installed correctly and nouveau crashing the xserver frequently (for me, it was every time I started chrome or firefox).

I am much obliged to both of you for the solution!

However, I am disappointed that Ubuntu let such a critical and hard-to-diagnose bug (for non-experts) get into the 12.10 release. For me, this started when installing the nvidia 3rd party driver as the first step after a clean install of 12.10.

I've been using Ubuntu since Dapper and have never had this issue before.

---

### Post by funicorn on 2012-11-03
It's not fair to blame  this on Ubuntu. A kernel interface to NVIDIA binary driver has to be built against the specific kernel version. This is why the linux-source package has to be installed to provide needed linux headers in certain cases. But linux-source is not always necessary provided linux-header-xxx-generic has been installed.  So it's a hardware dependent thing. It's obviously not appropriate to install linux-source by default on every desktop.

---

### Post by jusmop on 2012-11-03
> **funicorn said:**
> It's not fair to blame this on Ubuntu...

I disagree. Ubuntu provides a *simple* mechanism for installing the Nvidia non-free drive via their GUI (i.e. Settings -> Software Sources -> Additional Drivers). A single click and off it goes and downloads and installs the driver. If the kernel headers and source are a dependency, then they should be automatically downloaded and installed too, just like dependencies of any other package being installed.

This is clearly broken in the 12.10 64-bit desktop.

---

### Post by funicorn on 2012-11-03
It's not that simple. It's difficult to establish a precisely in-control dependency pattern when the unsolved dependent issue is hardware-dependent. You have to include an exclusive hardware list  which correctly triggers the self-adapting mechanism. This is never possible for the open source developing chain, because It needs a lot of testing under various hardware platforms by a lot of people.  If you go across all the development of Linux desktops, you may agree with me on that point. That's the intrinsic drawback of any open source project, even for the ones hold by the entire community, which generally consists of less than 1% of the total users.

---

### Post by jusmop on 2012-11-04
> **funicorn said:**
> It's not that simple. It's difficult to establish a precisely in-control dependency pattern when the unsolved dependent issue is hardware-dependent...

If the single-click-to-install button can't be made to work for the majority of ubuntu's target hardware, then they shouldn't implement it. Period. Broken features are *worse* than missing features.

But, while I'm no expert and maybe I'm missing something, the dependency issue is already solved. You yourself provided the solution: simply make the packages linux-source, linux-headers, and linux-image dependencies of nvidia-current. The hardware dependencies are already taken care of by apt.

Worked for three of us at least!

---

### Post by funicorn on 2012-11-04
Yes you missed one key point, single click works for the majority, and linux-source is only needed by a few modules on NVIDIA cards, mostly the newest ones.

---

