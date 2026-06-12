---
title: "No screen after GRUB"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by Katsu!! on 2010-09-09
Basically my brother who lives quite a distance away runs ubuntu 10.04 as of last week, today I used team viewer to access his computer to modify grub, the only modification I made was to change the timeout to "-1" so that the grub screen would show, ( he was having kernel issues )

Anyway he rebooted after a few updates and now after choosing the kernel, (theres only one to choose from plus its recovery mode) he gets a green screen and then his monitor goes into power saving mode cause it doesn't detect an output.

I've tried the whole, press 'e' and edit the quiet splash to say i.915mode=1/0 the xforcevesa and the nom one

nothing changes

He's running an old Time machine which we dont have the right specs for, all I know is that he has 512 Ram.

Any ideas of recovering this?

---

### Post by oldfred on 2010-09-10
Can he boot thru the recovery mode or to a command line?

Did you say you tried nomodeset as that was the one that worked for me.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

Lucid 10.04 KMS advanced settings:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Katsu!! on 2010-09-11
Yeah I tried just about all of what you posted, I put it down to a bad job with the kernel and just re-installed 10.04. told him not to do any kernel updates for a while.

---

