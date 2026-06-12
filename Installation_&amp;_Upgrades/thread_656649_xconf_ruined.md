---
title: "xconf ruined?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by smaller on 2008-01-02
I've been using the latest Ubuntu since the day it was launched and it has been running absolutely fine with all the whistles and bells activated. (compiz cube :)) 

Until tonight that is when I had the unfortunate idea to install virtualbox, after installing these packages with synaptic I was asked to reboot the system. After a reboot my system complained that it was running with the default video settings for some reason and I was asked to identify my video driver and monitor type.

Problem is that it's not taking my selections. No matter what I select in the "Screens And Graphics" window nothing changes. (I also tried rebooting X and even the entire system) However the next time I open this window the settings have gone back to the default plug'n play monitor and the generic VESA driver.

Could someone kindly point me in the right direction? I even tried overwriting my /etc/X11/xorg.conf file with the earliest backup of today but to no avail. (There are 6 backups, probably all made during my various attempt to get it back to work. Before that it seems the file hasn't been touched in months)

Another thing that is strange is that the shortcut to Restricted Drivers Manager doesn't work anymore, I'm pretty sure this worked before, I'm not sure if it's related or not.

---

### Post by ~LoKe on 2008-01-02
Sounds like you need to reinstall your drivers?  Did you install a new kernel or something?

After re-installing the drivers, try...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by g2g591 on 2008-01-02
I'd try reconfiguring x, by, in a terminal, running sudo dpkg-reconfigure xserver-xorg . 
EDIT:loke, whats the -phigh do?

---

### Post by Saint Angeles on 2008-01-02
try removing virtualbox?

then:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by smaller on 2008-01-02
Oh did I not mention I uninstalled virtualbox? That's obviously the first thing I tried although I knew it wouldn't help me, after ruining my system i couldn't get shot of it fast enough. :)

 I tried the sudo dpkg-reconfigure xserver-xorg too... didn't help unfortunately.

What did seem to help a bit was: sudo nvidia-glx-config enable

I now have my resolution back and in the driver section of "Screens and graphics" I have nv listed as my driver. (Strange, I was expecting  nvidia-glx or something of that ilk)  Unfortunately all is not well though, because in "Appearance"  my "visual effects" are set to "none" and I can't seem to enable any of the other options at all. Now what?

(My restricted modules manager still isn't working either: 
sudo restricted-manager gives the following message:

You need to install the package
  linux-restricted-modules-2.6.22-14-server
for this program to work.

That package doesn't seem to exist... :confused:

---

### Post by smaller on 2008-01-02
> **~LoKe said:**
>  Did you install a new kernel or something?

Thanks Loke, this remark set me on the way to a solution. Turns out that the virtualbox package depends on linux-image-2.6.22-14-server, which is obviously a different kernel to linux-image-2.6.22-14-generic which is what was installed. It's strange that I didn't notice this when I installed it in the first place. I clearly remember seeing only 2 packages to be installed, both of them called virtualbox-something.... Anyhow, I must have been asleep or something.

I booted in the old kernel and all was back to normal, that is to say restricted module manager is working again and I can enable desktop effects again. (Although the cube doesn't seem to be working yet, but all the others are so it must be something trivial I think)  I'm uninstalling the server kernel as we speak and afterwards I have to figure out how to get vmware up and running again, because  that doesn't seem to work anymore, let's hope not too many other programs are affected by this temporary kernel switch!

---

### Post by ~LoKe on 2008-01-02
Glad I indirectly led you to a solution. :lolflag:

---

### Post by smaller on 2008-01-02
> **~LoKe said:**
> Glad I indirectly led you to a solution. :lolflag:

So am I.... :)

If anyone cares everything else is up and running too now.
1) VMWare: had to reconfigure/recompile some stuff due to the kernel switch:
     =>sudo /usr/bin/vmware-config.pl
2) Compiz cube: I had only enabled the cube, not the rotating cube. #-o

And now I'm off to bed, about 3 and a half hours later then planned, and about the same amount of time before the alarm goes off :(

---

