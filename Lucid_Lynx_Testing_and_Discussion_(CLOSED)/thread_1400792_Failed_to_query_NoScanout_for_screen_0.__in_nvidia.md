---
title: "Failed to query NoScanout for screen 0.  in nvidia-settings"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Posiden on 2010-02-07
Hello, I recently installed the second alpha and after getting the nvidia drivers installed (173) I went to configure my second monitor. I went to X Server Display Configuration and it displayed this error:

```
Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.
```

I have a Geforce FX 5200 graphics card and everything worked fine in 9.10.

---

### Post by bladerunner6 on 2010-02-09
same problem I also get message in hardware drivers that the driver is activated but not in use,
but glxinfo shows its direct rendering

---

### Post by mamboze on 2010-02-10
I'm getting exactly the same error message. The 173 driver is working but I cannot access the window controlling screen resolution.  I'm only running one monitor tho. 

The frustrating thing is that the nvidia driver worked perfectly for 9.04. 

I'm guessing here, but maybe the problem is the xorg.conf file.

Any help etc much appreciated, thanx

---

### Post by kaligus on 2010-03-10
I am getting the same error after the most recent update from the nvidia ppa (195) but I am getting it on karmic 9.10 if that has any awakening properties in someone's mind...

It worked perfectly until this update which also for the first time in a long time broke many things.

```

 p, li { white-space: pre-wrap; }  Commit Log for Sat Mar  6 03:00:09 2010
 
 
 Upgraded the following packages:
 audacity (1.3.11-1~getdeb1) to 1.3.11-karmic~ppa1
 audacity-data (1.3.11-1~getdeb1) to 1.3.11-karmic~ppa1
 k3b (1.68.0~alpha3-0ubuntu1) to 1.69.0~alpha4-karmic~ppa2
 k3b-data (1.68.0~alpha3-0ubuntu1) to 1.69.0~alpha4-karmic~ppa2
 k9copy (2.3.3-0ubuntu1) to 2.3.5-karmic~ppa1
 libgphoto2-2 (2.4.6-1ubuntu6) to 2.4.8-karmic~ppa1
 libgphoto2-port0 (2.4.6-1ubuntu6) to 2.4.8-karmic~ppa1
 libk3b6 (1.68.0~alpha3-0ubuntu1) to 1.69.0~alpha4-karmic~ppa2
 libvamp-hostsdk2 (1.3-1) to 2.1-karmic~ppa1
 libvamp-sdk1 (1.3-1) to 2.1-karmic~ppa1
 libvlc2 (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 libvlccore2 (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 nvidia-190-modaliases (190.53-0ubuntu1~karmic~nvidiavdpauppa10) to 190.53-karmic~ppa3
 nvidia-195-kernel-source (195.36.03-0ubuntu1~karmic~nvidiavdpauppa2) to 195.36.08-karmic~ppa1
 nvidia-195-modaliases (195.36.03-0ubuntu1~karmic~nvidiavdpauppa2) to 195.36.08-karmic~ppa1
 nvidia-glx-195 (195.36.03-0ubuntu1~karmic~nvidiavdpauppa2) to 195.36.08-karmic~ppa1
 nvidia-settings (190.53-0ubuntu1~karmic~nvidiavdpauppa1) to 195.22-karmic~ppa1
 rhythmbox (0.12.6-1~getdeb1) to 0.12.6-karmic~ppa2
 shutter (0.85.1-1~getdeb2) to 0.85.1-karmic~ppa1
 sonic-visualiser (1.7cc-1) to 1.7.1-ppa1
 ttf-symbol-replacement (1.1.39-0ubuntu1~karmic5) to 1.1.40-0ubuntu1
 ttf-tahoma-replacement (1.1.39-0ubuntu1~karmic5) to 1.1.40-0ubuntu1
 vamp-examples (1.3-1) to 2.1-karmic~ppa1
 vamp-plugin-sdk (1.3-1) to 2.1-karmic~ppa1
 vlc (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 vlc-data (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 vlc-nox (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 vlc-plugin-pulse (1.0.5-1~getdeb1) to 1.0.5-karmic~ppa1
 wine1.2 (1.1.39-0ubuntu1~karmic5) to 1.1.40-0ubuntu1
 
 Installed the following packages:
 libfishsound1 (0.9.2-1)
 libfluidsynth1 (1.0.9+dfsg-2)
 liblash2 (0.5.4-0ubuntu3)
 liblo0ldbl (0.25-karmic~ppa1)
 liblrdf0 (0.4.0-1.2)
 liboggz1 (0.9.9-4build1)
 libosso1 (2.16-0ubuntu3)
 librubberband2 (1.4-karmic~ppa1)
 libzvbi-common (0.2.33-1)
 libzvbi0 (0.2.33-1)
 nvidia-195-libvdpau (195.36.08-karmic~ppa1)

```

---

### Post by CrusaderAD on 2010-03-21
I'm in the same boat guys. Hopefully this gets resolved soon.

---

### Post by collinp on 2010-03-21
According to comment #6 on Launchpad bug [#523108]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108"), it has been fixed in a upstream nVidia release but has yet to be updated in Ubuntu's repositories.

Running Lucid Beta, apt-cache policy output:
```
nvidia-glx-173:
  Installed: (none)
  Candidate: 173.14.22-0ubuntu10
  Version table:
     173.14.22-0ubuntu10 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Packages
```

---

### Post by FezzFest on 2010-03-24
I have the same problem.

Running Ubuntu 10.04 Beta1 on an Nvidia GeForce 4 MX420 card with Vvidia driver 96. I hope this will be fixed soon.

---

### Post by a.walker on 2010-03-27
> **FezzFest said:**
> I have the same problem.

Running Ubuntu 10.04 Beta1 on an Nvidia GeForce 4 MX420 card with Vvidia driver 96. I hope this will be fixed soon.

I have the same problem in Beta 1 with a GeForce 5200fx. I enabled twinview by adding the line```
option     "twinview"
``` to the xorg.conf. I now have my dual monitors running. Hopefully this bug will be squashed soon.

---

### Post by murb on 2010-03-30
I was experiencing a similar problem, but I managed to fix it by switching the nvideo driver (in Hardware Drivers). One has a version 'current', the other has version 173. I removed version 173 and activated the 'version current'. Rebooted and everything worked fine again.

---

### Post by CrusaderAD on 2010-03-30
> **murb said:**
> I was experiencing a similar problem, but I managed to fix it by switching the nvideo driver (in Hardware Drivers). One has a version 'current', the other has version 173. I removed version 173 and activated the 'version current'. Rebooted and everything worked fine again.

I tried this... it didn't work for me. I did do a fresh install. Maybe I'll try again.

---

### Post by zhangsong023 on 2010-04-01
Same problem with 10.04 beta1 and nvidia-96 package.

---

### Post by CrusaderAD on 2010-04-01
I tried again with a fresh install, no luck. With the basic default drive loaded, I can have a higher resolution but no desktop effects. With the nvidia driver installed I can have a low resolution with desktop effects. Hopefully this gets resolved soon. It's tolerable now cause we're still in beta, but we can still hope.

---

### Post by sandys1 on 2010-04-01
This issue is being tracked by a bug - [https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196](https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196)

Add yourself to "This bug affects me" at the top.

---

