---
title: "Help installing Edgy with nVidia 8800 GTS"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by Anomaly on 2007-03-04
I would like to say thx, right away for your help...on with the problem.

I just upgraded my computer to AMD x64 dual core, ASUS motherboard, and the nVidia 8800 GTS (340MB).  I went to the ubuntu site and downloaded the .iso for x64 and burned it.  I tried to run the CD live (from boot, not inside xp) and I get an error saying that X server did not start...

is it because the graphics card is too new?

I also found beta drivers for the card on the net, but I have no idea how to install them before installing ubuntu...

any help will be greatly appreciated...thx again..

---

### Post by tubasoldier on 2007-03-05
Nvidia drivers for the 8800 series are under a different download category than the regular drivers. 
The 8800 series is also not in the supported products list on the Nvidia website:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

Sorry I couldn't help get it working but I would say it is still a bit too new. Good luck though.

---

### Post by aidanr on 2007-03-05
you might want to grab the [alternate install cd]("http://releases.ubuntu.com/edgy/ubuntu-6.10-alternate-amd64.iso") as it doesn't boot up into an x server, and then grab [these drivers]("http://www.nvidia.com/object/linux_display_amd64_1.0-9746.html") from the command line and install them

so basically when you reboot and get the x server error you would switch to a different tty (ctrl+alt+F6), log in and type

```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
chmod +x NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
sudo ./NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
```

follow the instructions and reboot, or alternatively use the [envy script]("http://albertomilone.com/nvidia_scripts1.html")

of course this is assuming that a) you'll be connected to the net and b) the alternate cd installs without bitching about the x server, i haven't used the alternate install disc yet so i'm not sure

---

### Post by tubasoldier on 2007-03-05
You can install the same drivers in a regular install. No need for the alternate install cd.
```
/etc/init.d/gdm stop
```

You have to have build-essentials installed in order to install it. Or at least the kernel source.

---

### Post by Anomaly on 2007-03-05
Thanks for all your help...I'll try these methods as soon as I can and report back.

---

### Post by Takis on 2007-03-06
I had the same problem (I think). My problem was that the Live CD detects that you have some form of NVidia card and sets X to use the 'nv' driver which doesn't work for the 8800.

I was lucky in that X crashed and I was returned to a command line during the Live CD boot - if this happens to you, you need to edit /etc/X11/xorg.conf (ensure you put that capital 'X') and change the line that reads:
```
    Driver         "nv"
```
to
```
    Driver         "vesa"
```

I'm guessing you can use an editor like vi - otherwise you can just pull a nice sed line:
```
    sudo sed -i -e 's/\"nv\"/\"vesa\"/' /etc/X11/xorg.conf
```
...which'll do the same thing.

This will put a really, really generic driver in, but it should work. Now run:
```
   sudo /etc/init.d/gdm restart
```
or if you're trying Kubuntu:
```
   sudo /etc/init.d/kdm restart
```

And that should work (if you have the same prob I did).

---

### Post by scott_aus on 2007-03-12
Looks like official Linux (generic) drivers are available on the Nvidia website as of March 7th 2007:

[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html) (32-bit)

[http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html) (64-bit)

[http://www.nvidia.com/object/freebsd_1.0-9755.html](http://www.nvidia.com/object/freebsd_1.0-9755.html) (FreeBSD)

---

### Post by arito on 2007-03-14
I just filed a bug report about the problem I have with GeForce 8800 320MB card and Ubuntu. I think it'd be good if others with the same problem added to the report, so that developers would get a better picture about the scale of the problem. Perhaps it would be good to mention the exact model of the card.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/91556]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/91556")

---

### Post by eyelessfade on 2007-03-14
"Looks like official Linux (generic) drivers are available on the Nvidia website as of March 7th 2007:"


Not entirely true, the 1.0-9746 (December 21, 2006) is also supporting the 8800 series, I know cause I used them with my 8800GTS. So I have been wondering why ubuntu haven't updated the packages, not even for the feisty (which I run).

---

### Post by MikeCortez on 2007-03-24
I am having this same problem, except im using the 32bit version of ubuntu. I downloaded the new nvidia drivers for my 8800GTS. The only thing is it wont install because i dont have the build-essentials installed in order to install it. Or at least the kernel source." How do i do this? Sorry I'm a total noob with linux. This is the second machine i've install ubuntu on. Since I have 1 HD and its one partition I want to re-partition it with the partition editor in ubuntu before actually installing it. Any help would be appreciated. Thanks.

---

