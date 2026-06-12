---
title: "Seemingly Unable to Install Ubuntu"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by miser89 on 2010-12-23
Hi,

I've just bought a new laptop - a Sony Vaio - and I was very keen to install Ubuntu on it, but all of my attempts so far have failed.  I first burnt a copy of the live CD for 10.10 and went through the installation process with it and everything was seemingly a success until after it asked me to reboot, where after I did so and chose Ubuntu from the GRUB menu, Ubuntu failed to load and simply showed me a blank, black screen.

I thought that perhaps I had made a mistake installing, so I tried again but reached the same problem, and then tried again with a 32bit copy instead of the 64bit, and still had the same problem after installation.

So I tried WUBI, which downloaded and installed Ubuntu 10.10 64bit and I restarted, selected Ubuntu from the Windows bootloader, and then again met with the blank screen!

I've searched but I haven't been able to find any answers to how to fix this problem.  Might it be an incompatibility with my graphics card?  (An NVidia GT 330M)

Please let me know your thoughts on how I might fix this problem - I was looking forward to switching to Ubuntu.

---

### Post by dino99 on 2010-12-23
welcome,

yes this issue might be a graphic issue

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[http://www.uluga.ubuntuforums.org/showthread.php?p=10266166](http://www.uluga.ubuntuforums.org/showthread.php?p=10266166)

after installation, update your sources.list (synaptic repo tab) with this ppa, then update/upgrade

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by sikander3786 on 2010-12-23
Yes that is indeed a graphic issue.

If you've Ubuntu there on your HDD at the moment, from Grub menu highlighting the Ubuntu entry, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully you should see the desktop this time.

Then from System > Administration > Additional Drivers, install the current drivers and the issue might resolve itself permanently. Let us know how that goes and also, Welcome to the forums :-)

---

### Post by miser89 on 2010-12-23
Thanks for your replies.  I replaced 'quiet splash' with 'nomodeset' and Ubuntu loaded as terminal with no GUI.  I was able to log in but I wasn't sure what to do after that?

Thanks for your help so far.

---

### Post by sikander3786 on 2010-12-23
Is this a Wubi install or a proper install currently? Which graphics card is there? What does these commands return.

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

```
cat /etc/X11/xorg.conf
```

---

### Post by miser89 on 2010-12-23
Thanks for your reply.  Right now I've got Ubuntu installed in its own partition.

I ran the commands you gave me with the following results:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
```

I didn't have the gtxinfo command available.  When I tried to use it Ubuntu suggested to me an apt-install command for it, but I was unable to because it could not access the internet.

The xorg.conf file wasn't available, but there was an /etc/X11/xorg.conf.failsafe, the contents of which were:
```
Section "Device"
    Identifier "Configured Video Device"
    Driver "vesa"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
EndSection
```

I hope this information helps.

---

### Post by sikander3786 on 2010-12-23
You've got 2 graphics controllers there. Which one are you using currently?

Try reconfiguring your graphics in the mean time.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

---

### Post by miser89 on 2010-12-23
It would be the nVidia one, as that's the one this laptop was advertised as using.  I think the Intel one would be on-board graphics.

I've just tried the dpkg command but unfortunately there was no change in the boot behaviour after a restart.  However, I did manage to boot into low-graphics mode when I added the parameters *single nomodeset* in GRUB, and then I was able to install an nVidia driver, but I still can't boot properly.

---

### Post by miser89 on 2010-12-23
Update: I've succeeded to get it working on nVidia!  I think I still need to do a bit of hacking to get it to work with visual effects, but it works great with graphics on the 'none' setting.

I found this guide very useful: [http://www.voip-x.co.uk/files/adam/IMPORTANT_README](http://www.voip-x.co.uk/files/adam/IMPORTANT_README)

Hopefully I will be able to get it working with full graphics.  Thanks everyone for your help.

---

### Post by kroon78 on 2010-12-23
Wow, sounds like a real nightmare.  Glad things seemed to work out for you.  So far the two laptops i have installed ubuntu on have never given me much trouble.

---

