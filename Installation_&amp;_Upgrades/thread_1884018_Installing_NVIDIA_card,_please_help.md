---
title: "Installing NVIDIA card, please help"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by iCracked on 2011-11-20
Hey guys, I have a custom-built system with a MSI Hawk GTX460 1GB, and I am having trouble installing the proprietary drivers instead of the nouveau ones.

Here is why I need them: Because of most games not working with the nouveau drivers on my card. Display works fine at 1920x1200 though.

Here is what I have tried to get it working:
**Attempt 1:** Clean install of Ubuntu 11.10 64 bit, install of the drivers through the additioal drivers utility. What Happened: Blank screen upon reboot, no option to get into CLI, but could boot into recovery root shell but not install anything because of my wireless card.

**Attempt 2: **Clean install of **K**ubuntu 11.10 64 bit, but this time I tried the way I did the first time, plus the manual way. I blacklisted the 5 nouveau drivers according to a guide, and downloaded driver 285.~ from the nvidia site as a .run specifically for my graphics card and linux 64-bit. Instal went fine but now I am stuck staring at a blank splash screen.


Is there anything more I could do? Preferably a guide?

---

### Post by oldfred on 2011-11-20
Welcome to the forums.

It is always better to do the install with a hard wired Ethernet connection. There are so many wireless drivers that the liveCD cannot include all of them, so you often have to download a driver with your Ethernet direct connection. I find a wired connection is faster as the updates & driver downloads often are sizable.

I prefer to install the default driver that Ubuntu recommends for nVidia. But some of the new versions defaulted to the 173 driver, but still had options for current version.

---

### Post by iCracked on 2011-11-20
I don't need the wifi because the driver is actually installed without errors, its the first boot after I have installed it that does not work.

---

### Post by oldfred on 2011-11-20
On first boot before nVidia drivers are installed I have always had to use nomodeset on the linux line in the grub menu.
Do not know about issues with wireless, if that is the issue you should start a new thread with that in the title.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by iCracked on 2011-11-20
yah the wireless is not really a problem, it works in the GUI, I opened this thread for my video card problems. I don't know the actual command to set nomodset from grub though, if I find out how and do set it, I will post back here.

---

### Post by iCracked on 2011-11-20
i followed the guide and setting nomodeset did not work for me, same outcome of the 5 dots loading and then freezing and staying frozen. Maybe I will try fedora or some other linux.

---

### Post by MAFoElffen on 2011-11-20
> **iCracked said:**
> i followed the guide and setting nomodeset did not work for me, same outcome of the 5 dots loading and then freezing and staying frozen. Maybe I will try fedora or some other linux.
My ears were burning...

Try this:
[SIZE=2]**[COLOR=Red][COLOR=Black][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/COLOR][/COLOR][/B]
[/SIZE] 
Please post the results of
```

lspci -vnn | grep VGA

```While still in the CLI, install your drivers, by either of these methods:
[SIZE=2][COLOR=Red][COLOR=Black]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 
[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/COLOR][/COLOR][/SIZE][COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][SIZE=2]
[/SIZE]
[SIZE=1]That card should be nvida-current or binary 275+ to support that card.  I don't think 173 works with that recent a card.[/SIZE]

**[SIZE=1]PAY SPECIAL ATTENTION TO THIS:[/SIZE]**
[/SIZE][/COLOR][/SIZE][/COLOR]> Some may have to additionally do this:
 ```

sudo echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
sudo echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf[FONT=monospace]
[/FONT]sudo update-initramfs -u
 
```It fixes a Plymouth lockup problem...
To fix what you described... locked up in the Plymouth Splash.

---

### Post by iCracked on 2011-11-20
> **MAFoElffen said:**
> My ears were burning...

Try this:
[SIZE=2]**[COLOR=Red][COLOR=Black][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/COLOR][/COLOR][/B]
[/SIZE] 
Please post the results of
```

lspci -vnn | grep VGA

```While still in the CLI, install your drivers, by either of these methods:
[SIZE=2][COLOR=Red][COLOR=Black]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 
[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/COLOR][/COLOR][/SIZE][COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][SIZE=2]
[/SIZE]
[SIZE=1]That card should be nvida-current or binary 275+ to support that card.  I don't think 173 works with that recent a card.[/SIZE]

**[SIZE=1]PAY SPECIAL ATTENTION TO THIS:[/SIZE]**
[/SIZE][/COLOR][/SIZE][/COLOR]To fix what you described... locked up in the Plymouth Splash.

the results of lspci -vnn | grep VGA:

Flags: bus master, VGA palette snoop, 66mhz, medium devsel, latency 64
01:00.0 VGA compatible controller [0300] : nVidia Corporation GF104 [GeForce GTX 460] (rev a1) (prog-if 00 [VGA controller])

---

### Post by MAFoElffen on 2011-11-20
And did you do this?
 ```

sudo echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
sudo echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
 
```

---

### Post by iCracked on 2011-11-20
> **MAFoElffen said:**
> And did you do this?
 ```

sudo echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
sudo echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
 
```

Yes I typed each of those in, only the last one had an actual output though

---

### Post by MAFoElffen on 2011-11-20
> **iCracked said:**
> Yes I typed each of those in, only the last one had an actual output though
Yes, as it should... And on reboot, does it passed the Plymouth Splash now?

---

### Post by iCracked on 2011-11-20
> **MAFoElffen said:**
> Yes, as it should... And on reboot, does it passed the Plymouth Splash now?

No, even after doing all those I still cannot get passed the splash screen. Looks the same as before.

---

### Post by dino99 on 2011-11-21
you need to add this ppa:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

into synaptic, then update and install the latest nvidia-current (after purging the previous installed)

---

