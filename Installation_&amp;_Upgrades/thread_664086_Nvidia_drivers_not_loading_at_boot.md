---
title: "Nvidia drivers not loading at boot"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by teoryn on 2008-01-10
I've just built a new computer and I'm attempt to switch to Ubuntu after 2.5 years with Gentoo. I started with a fresh install of Gusty which went smoothly after adding "irqpoll" to the boot options of the live cd and the actual install and going to the safe video option on the live cd. I'm using the source.list from ubuntuguide.org and installed all the updates that were needed.

Having attempted to use the nvidia drivers in repo with my 8800GT in previous install attempts I instead downloaded the drivers from nvidia's site. I proceeded with the directions and upon starting gdm again I got the splash screen and desktop effects were working fine.

I then rebooted the computer to find ubuntu entering safe graphics mode at 800x600, so I repeated the steps of installing the nvidia driver and again everything worked; until reboot.

At this point everything goes like this:
[LIST]
[*]Boot computer, goes into low res mode.
[*]Ctrl-Alt-F2 and run the following:
[/LIST]
```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.07-pkg2.run // I just agree, except xorg.conf is fine so I leave it alone
sudo /etc/init.d/gdm start
```

At this point everything is working fine until reboot.

I've found the following things interesting:
```
kevin@vesper:~$ dmesg | grep -i nvidia
[   40.476486] nvidia: module license 'NVIDIA' taints kernel.
[   40.480069] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-7185  Mon Apr  2 13:03:04 PDT 2007
[  214.025738] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.07  Thu Dec 13 18:34:01 PST 2007
[  248.324558] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.07  Thu Dec 13 18:34:01 PST 2007
```
To me this looks like the wrong driver is being loaded at boot. I don't know how to change that, and I haven't installed any other nvidia drivers besides the one from nvidia's site so I'm not sure what is happening.

```
kevin@vesper:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
```
I tried adding "nvidia" to the end of this file, but nothing happened.

```
kevin@vesper:~$ modprobe -l | grep -i nvidia
/lib/modules/2.6.22-14-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.22-14-generic/volatile/nvidia_new.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/video/nvidia/nvidiafb.ko
```
This is the same before and after "sudo sh NVIDIA-Linux-x86_64-169.07-pkg2.run".

Thanks in advance,
-Kevin

---

### Post by oldsoundguy on 2008-01-10
try using the third party installer ... Envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Has worked for me on 3 machines thus far!

---

### Post by manimal347 on 2008-01-10
As a Gentoo user of 2.5 years, I imagine you've already tried "modprobe nvidia," but if not, that might work. It loads the Nvidia kernel module in case it didn't get loaded at startup.

You say your xorg.conf is "fine?" I'm afraid your expertise probably far outstrips that of the top five percentile of Ubuntu users, so I'll err in trusting your judgment (ARCH/Gentoo/Slackware make you learn *.conf files backwards and inside out :D). Maybe you might want to ask on the Ubuntu developer mailing list or something, as I gather you likely are diligent about checking the Web, relevant Wiki pages, and all applicable man pages, as well as reading bug reports on things like Launchpad (Canonical/Ubuntu's bug tracker). You may get a resolution here, but this problem might be a tad complex for the forum.

Also, thanks for posting your config files! It might have been interesting to see your xorg.conf, but what you did post saved me from giving rudimentary answers that won't fix your trouble. Just so other people know, the Nvidia drivers shipped with Gutsy Gibbon are by now obsolete and don't support the 8800GT card, so "the Nvidia way" was his only option.

---

### Post by teoryn on 2008-01-10
oldsoundguy - I've read post about people not having much luck with envy and the 8800GT, so I decided to just do it manually.

manimal347 - I did try "modprobe nvidia" without luck.

I did some more digging and found the solution at [http://ubuntuforums.org/showthread.php?t=651783&page=2](http://ubuntuforums.org/showthread.php?t=651783&page=2)

I just had to add "nv" to DISABLED_MODULES in /etc/default/linux-restricted-modules-common

---

