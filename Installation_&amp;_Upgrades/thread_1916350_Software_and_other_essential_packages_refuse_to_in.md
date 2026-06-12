---
title: "Software and other essential packages refuse to install since &quot;Partial Upgrade&quot;"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by KBD20 on 2012-01-27
Hi, recently, after being prompted to do a partial upgrade (which I went through with),  I came across an issue after the cleanup process. 

There are certain programs (from synaptic/market) that refuse to install, namely VLC Media player, and gstreamer (specifically, gstreamer0.10-ffmpeg), the error mentions that the package(s) have "unresolved dependancies" that it has, which I am sure are available from the download centre or synaptic. 
Example:
> gstreamer0.10-ffmpeg:
 Depends: libavcodec53 but it is not going to be installed
 Depends: libavformat53 but it is not going to be installed
  Depends: liborc-0.4-0 (>=1:0.4.16) but 1:0.4.14-1ubuntu1 is to be installed
  Depends: libpostproc51 (>=5:0.9.1) but 4:0.6.2-1ubuntu1.1 is to be installed
Thanks to anyone who can help with this problem.

Also the version of Ubuntu I am using is Ubuntu 11.10 -32bit

---

### Post by plucky on 2012-01-28
> **KBD20 said:**
> Hi, recently, after being prompted to do a partial upgrade (which I went through with),  I came across an issue after the cleanup process. 

There are certain programs (from synaptic/market) that refuse to install, namely VLC Media player, and gstreamer (specifically, gstreamer0.10-ffmpeg), the error mentions that the package(s) have "unresolved dependancies" that it has, which I am sure are available from the download centre or synaptic. 
Example:
Thanks to anyone who can help with this problem.

Also the version of Ubuntu I am using is Ubuntu 11.10 -32bit

What happens if you run from a terminal ```
sudo apt-get update
sudo apt-get install -f
```

If no errors,then run ```
sudo apt-get dist-upgrade
```

If there are any errors,please post the output.

Good Luck

---

### Post by mörgæs on 2012-01-28
Partial upgrades are dangerous:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by KBD20 on 2012-01-28
Ok after using apt-get autoremove, then apt-get dist-upgrade I still get errors when force and regular installing vlc and gstreamer0.10-ffmpeg

> sudo apt-get install vlc -f
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1:1.1.13-0.0) but it is not going to be installed
       Depends: libavcodec53 (>= 5:0.9) but it is not going to be installed
       Depends: libva-x11-1 (> 1.0.14~) but it is not going to be installed
       Depends: libva1 (> 1.0.14~) but 1.0.12-2 is to be installed
       Recommends: vlc-plugin-notify (= 1:1.1.13-0.0) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1:1.1.13-0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.> 
sudo apt-get install gstreamer0.10-ffmpeg -f
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gstreamer0.10-ffmpeg : Depends: libavcodec53 (>= 5:0.9.1) but it is not going to be installed
                        Depends: libavformat53 (>= 5:0.9.1) but it is not going to be installed
                        Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.14-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.Also, the partial upgrade was offered on a final build of Ubuntu 10.10

---

### Post by Old_Grey_Wolf on 2012-01-28
Try these commands to fix the partial upgrade ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by KBD20 on 2012-01-28
> **Old_Gray_Wolf said:**
> Try these commands to fix the partial upgrade ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

I tried this, and after disabling some obsolete sources from "software sources" the error shown when doing an apt-get update is gone, everything in that area went smoothly, however there are still issues with installing certain packages.

---

### Post by KBD20 on 2012-02-04
After doing a dist-upgrade (and checking the update manager) the following updates won't install (with the output: "The following packages are to be kept back): 
```
postproc shared libraries (libpostproc52)
MPlayer's Movie Encoder (mencoder)
Ultimate Movie Player For Linux (mplayer) 
```

Would this have anything to do with the partial upgrade issues?

---

