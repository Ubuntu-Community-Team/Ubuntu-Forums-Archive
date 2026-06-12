---
title: "[SOLVED] did an aptitude dist-upgrade from hardy to intrepid, instead of using update"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by astrophoenix on 2008-11-02
instead of using the update manager, I ran "aptitude dist-upgrade" to try to upgrade from hardy to intrepid. 

now I have lots of issues; the hardy kernel is still running, instead of the intrepid kernel. I installed the intrepid kernel, but my encrypted lvm2 root partition won't work with that kernel. 

is there any way to do the rest of whatever update manager would have done? or should I just give up and re-install?

---

### Post by astrophoenix on 2008-11-04
to fix this, I just ran update manager:

```

aptitude install update-manager
update-manager -d

```

that installed 60 more packages, removed a couple dozen, and ran some scripts.

after the reboot, the intrepid kernel was running, and my encrypted LVM2 partitions were working. no X though.

first i tried installing nvidia-glx-177:

```

aptitude install nvidia-glx-177

```

upon trying to start X, I got the message that my video card was no longer supported in /var/log/Xorg.0.log. then I tried to fall back to older versions. with 173 I also got the unsupported message. with 96, I get an error about unresolved symbols. I will probably spend more time later to try to get that working (probably just need to install another package or two).

to get X to run, I went ahead and switched to the Free nv driver.

```

aptitude install xserver-xorg-video-nv

```

then I edited /etc/X11/xorg.conf, and changed 

```

Driver "nvidia"

```

to

```

Driver "nv"

```

and now X is running, and I seem to have a working intrepid install.

---

