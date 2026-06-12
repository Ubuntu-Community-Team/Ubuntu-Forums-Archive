---
title: "ASUS K53TA Graphics Problem"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by Daakshi on 2012-02-12
I've installed ubuntu 11.10 onto a partition dual booted with grub on my ASUS laptop. When I select linux to boot it loads to a purple screen for a few moments, a green line appears and the monitor shuts off, while the computer is still running. I have tried booting onto recovery mode and installing the suggested nvidia drivers, but it didn't help.

---

### Post by sandy8925 on 2012-02-14
I have the same laptop, it has AMD graphics card only not NVIDIA. Installing the NVIDIA drivers will make the situation worse. Uninstall them if possible.

About the problem, there was a bug in Linux kernel 3.0 due to which the laptop display doesn't work (but externally connected displays e.g through HDMI will work). This bug was fixed in Linux kernel 3.2. Apparently the Ubuntu 3.0.0-16 kernel works properly. If that sill doesn't work, compile a stable version of the Linux 3.2 kernel from kernel.org and then it should work.

---

### Post by tamuru on 2012-02-18
How exactly would one go about compiling the kernel? I'm kinda unfamiliar with that sorta thing. (boyfriend of the OP here, have ubuntu working on my own laptop, dual booted with win7, I can use both, but know win7 more)

---

### Post by MAFoElffen on 2012-02-19
> **tamuru said:**
> How exactly would one go about compiling the kernel? I'm kinda unfamiliar with that sorta thing. (boyfriend of the OP here, have ubuntu working on my own laptop, dual booted with win7, I can use both, but know win7 more)
You don't have to compile it.  

Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) Download the kernel you want.  That would end up in your ntfs partition for Win7 right?

Boot from a LiveCD. Use Nautilus to copy the .deb files from the ntfs partition to your installed filesystem... say in your download directory. Close down Nautilus and unmount the filesystems from the desktop.

Follow the directions here:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Mounting An Installed System From the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]
Which, what you are doing is mounting and chrooting to the installed system. 

From there, open a terminal session.
```

cd Download
dkpg -i *.deb

```
...But should you first try to purge the nvidia driver (not just remove) and install the ATI drivers to see if that fixes your problem?

---

### Post by sandy8925 on 2012-02-21
well, the open source drivers have this problem. if you install the AMD proprietary drivers then it works fine (atleast if you install Catalyst 11.8. after that a number of problems are present in the newer drivers e.g after suspend, screen is blank when you resume, and 2D is sluggish)

---

### Post by Daakshi on 2012-02-23
I got it working, thanks for all the help! It turns out that I was trying to install the 32 bit version, and I tried the 64 bit version and downloaded the proprietary AMD driver (on the driver installer app it was the second on the list, the newest driver didn't work) and it works well aside from a maybe 18 pixel wide line spanning the width of my monitor on the top. It looks like it is the bottom 18 or so pixels of my screen, because it changes when I scroll and I can see my mouse if I move it down. I tried to take a screenshot of the problem, but the screenshot looked normal. Any ideas on what's causing it, or do I just have to wait until a new update and hope it fixes it?

---

### Post by sandy8925 on 2012-02-29
that doesn't sound normal, I don't have that problem. try rebooting?

best thing to use right now seems to be Catalyst 11.8, since that works perfectly (although 3D is faster on the newer drivers)

---

### Post by Daakshi on 2012-03-01
> **sandy8925 said:**
> that doesn't sound normal, I don't have that problem. try rebooting?

best thing to use right now seems to be Catalyst 11.8, since that works perfectly (although 3D is faster on the newer drivers)

When I reboot, everything is normal for a while, and then the screen will flicker and the little bar is back again. I am going to try Catalyst 11.8, I'll update after it's installed.

---

