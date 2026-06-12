---
title: "Help installing my video card nVidia"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by limiz on 2010-11-26
I just try seeing if I can get it work myself. No luck. I'm using nVidia GT 240. And it dose not work off the back. So I have to leave the video card out before I can get the install. But some how I fail. And need to reinstall **Ubuntu 10.10 64bit**. And my internet speed is meh slow but not dial up slow. *internet form my cellphone* What happen was I uninstall all the ati(witch I'm using a ati integrated sigh) And so I thought I install nVidia. Was using Synaptic Package Manager. I don't want reinstall ubuntu all over again(don't want to install after this one). So I'm asking if their a better way on doing this?

---

### Post by Hippytaff on 2010-11-26
Try this :-)
[http://www.troublefixers.com/solved-manually-download-and-install-nvidia-graphics-drivers-in-ubuntu-get-best-graphic-effects-in-ubuntu-by-installing-graphics-drivers/](http://www.troublefixers.com/solved-manually-download-and-install-nvidia-graphics-drivers-in-ubuntu-get-best-graphic-effects-in-ubuntu-by-installing-graphics-drivers/)

---

### Post by limiz on 2010-11-26
There one little problem. The person did not list the lib need before hand. Who knows if he had all the right lib before hand and did not know it. I need a little more detail!

---

### Post by Hippytaff on 2010-11-26
I might be wrong, but I thought that if you do it this way the lib's and dependencies would be taken care of :-)

Though there is every possibility I'm misunderstanding :-)

---

### Post by efflandt on 2010-11-26
Did you use any proprietary drivers for your integrated ATI video, and were they from System > Administration > Hardware Drivers or somewhere else?  If you activated any video drivers from Hardware Drivers, remove that first, or if you installed special ATI drivers any other way, you need to remove them.

I don't know if your BIOS automatically disables on board video if it senses other video, or if you need to disable something in CMOS setup (some key you press during BIOS splash screen before grub menu).  If you have an existing **/etc/X11/xorg.conf** file, from ATI, that may be interfering.  **sudo mv** it to a different name or **sudo rm** it to remove it.

But if you can somehow get it to boot with video showing on the GT 240 it should work with default nouveau drivers, or would work better once you go to System > Administration > Hardware Drivers and "activate" nvidia.

If you installed the nvidia drivers using Synaptic. it is possible that they are not configured yet.  In that case you could try going to a console (Ctrl+Alt+F1), login, then:

```
sudo stop gdm
sudo nvidia-xconfig
sudo shutdown -r now
```and see if it works.  Although, it would be simpler if activating them from Hardware Drivers works (you have to reboot for that to take effect).

---

