---
title: "HH upgrade trashed my nVidia drivers"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2008-04-28
Hi guys,

upgraded from GG to HH Friday. No problems during the actual process. Previously I had managed to get Compiz working, and was very happy.

Rebooted, and straightaway went to a warning screen about low resolution video. I tried the "configure" option, to use the "nv" driver for my nVidia GeForce440MX card, but it wouldn't work.

I logged in, used Synaptic to install Envy and tried again. Still no dice. I then used Envy to REMOVE the nVidia drivers, and the resolution warning went away, and I was able to go to 1280x1024.

However, when I tried to enable "advanced desktop effects" I got a warning that the nVidia restricted driver was needed. I let Ubuntu install that, rebooted, and went back to step 1. Low res and not able to configure the "nv" driver.

I did see a post about manually installing the nVidia drivers, but that has to be done from an ctrl-alt-F1 terminal window, and guess what ? I've never been able to switch to a terminal window in ubuntu on this machine. I just get a blank screen, and then can't switch back to ctrl-alt-f7. I did try and run the nVidia install package from the recovery terminal, but I got a warning about being in the wrong term level or something. When I ignored the error, I got a message that the package would have to recompile itself for my kernel, and then it bombed out with an error saying it couldn't find the precompiled headers .....

Can anyone help please I guess what I need is 

1) fix ctrl-alt-F1 issue so I can run a terminal
2) manually install nVidia drivers
3) try and enable compiz.

---

### Post by russ18uk on 2008-04-28
Hi mate. I had a problem after upgrading to Kubuntu 8.04 from Kubuntu Gutsy in which it would only boot to the terminal, and any attempt to startx resulted in a few flashes and straight back to terminal. It largely borked my Nvidia drivers so I reinstalled the official drivers from nvidia. Reboot to recovery mode, don't think I had to switch run level but it might complain about it, so you can try and install in default recovery mode run level or telinit 3 to run level 3. If you're using 32bit then the latest drivers for GF4 series are:

wget [http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/NVIDIA-Linux-x86-96.43.05-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/NVIDIA-Linux-x86-96.43.05-pkg1.run)

cd into the directory and run the installer. Install over any problems if the installer says it can't find xx or uninstall fails and hopefully you should be back up.

---

### Post by martrn on 2008-04-28
Agreed use nvidia driver from nvidia works fine

first you need to install the kernel headers for the kernel you are using so at a terminal type :

```

uname -r
sudo apt-get install linux-headers-(yourkernelversion)
```

where (yourkernelversion) is replaced with i386 generic or whatever is returned from uname -r

Then follow russ18uk 's guide.

---

### Post by Jethro_uk on 2008-04-29
> **martrn said:**
> Agreed use nvidia driver from nvidia works fine

first you need to install the kernel headers for the kernel you are using so at a terminal type :

```

uname -r
sudo apt-get install linux-headers-(yourkernelversion)
```

where (yourkernelversion) is replaced with i386 generic or whatever is returned from uname -r

Then follow russ18uk 's guide.

'Friad that didn't work. I got a message saying there was no matching package or something. I fixed the ctrl-alt-F1 issue, and tried running the install again, but it grumbled about wanted precompiled headers, and then when I tried to get it to compile the headers for me I got a message about needing version 4.1 of gcc, not the version 4.2 that I got with HH. I suspect I can change the gcc symlink to point to the 4.1 version (which appears to be still installed) but that'll have to wait till I'm at home (I'm posting from work here).

---

