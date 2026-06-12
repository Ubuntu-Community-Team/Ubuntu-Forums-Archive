---
title: "Installing and Updating asks for 'disc'"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by aajjbb on 2012-09-27
Hello, I'm a Ubuntu user and just Installed Xubuntu to try the Xfce interface, I'm doing really fine but I'm dealing with a boring error, when I try to install VLC, I receive the follow error information.

```

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.3-2~ppa2) but 2.0.3-2~ppa2 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but it is not going to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but it is not going to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but it is not going to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
     Depends: libva1 (> 1.0.15~) but it is not going to be installed
     Depends: libxcb-composite0 but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed
     Depends: libxcb-randr0 (>= 1.1) but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

```Looking over the internet I've found that the possible solution would be run the follow command in the terminal:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install build-essential
```I'm used to run this command in ubuntu and it works fine, downloading all the data needed from the internet bu now, the xubuntu is trying to get this data from de 'CD' of installation(I've installed using a USB Pendrive). This is the message:

```

Media change: please insert the disc labeled
 'Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)'

```What I have to do to fix it ? Thanks in advance.

---

### Post by daslinkard on 2012-09-27
Maybe this command will work for you?

```
sudo add-apt-repository ppa:n-muench/vlc
```
```
 sudo apt-get update && sudo apt-get install vlc 
```

Let me know how this works for you?

---

### Post by lisati on 2012-09-27
Do you have the CD/DVD selected as a software source in update manager?

---

### Post by aajjbb on 2012-09-27
I'm currently running the commands 'daslinkard' sent. I also noticed that the CD was selected in 'Ubuntu Software Center', I'll give feedback of what happened soon.

---

### Post by aajjbb on 2012-09-27
Thank you, VLC is now running smoothly. The problem was really have the Xubuntu Installation CD as a software source.

---

### Post by daslinkard on 2012-09-27
Glad you were able to get this solved!  Please mark the thread as such and know that any time you have any questions we are here for you.

---

