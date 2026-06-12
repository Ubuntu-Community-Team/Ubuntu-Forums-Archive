---
title: "Dell XPS 15 (2014) No TouchPad when installing Ubuntu Server to --&gt; Desktop version"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by naisanza on 2017-05-02
I need a specific setup with an encrypted LUKS partition, and the current Ubuntu Desktop installer does not have it available. So I am using the Ubuntu Server 16.10 ISO for the install. Server version installs fine, but after installing ubuntu-gnome-desktop and ubuntu-desktop, and rebooting, the touchpad isn't recognized or working. The touchpad works in Ubuntu Live. And an external mouse works

The script I use for setting up my Ubuntu instance is running the following shell script here:

[https://github.com/TheShellLand/exo/blob/master/readyUp/ubuntu-readyup.sh](https://github.com/TheShellLand/exo/blob/master/readyUp/ubuntu-readyup.sh)

ISO: Ubuntu Server 16.10 ISO

---

### Post by naisanza on 2017-05-02
Installing Ubuntu Server 16.10 ISO version, and adding "ubuntu-gnome-desktop" and "ubuntu-desktop" packages, the pm-util tools, such as "pm-suspend" does not do anything

ISO: Ubuntu Server 16.10 ISO

---

### Post by naisanza on 2017-05-02
I'm installing Ubuntu Server 16.10 ISO, and I need all the packages required to convert it into what Ubuntu Desktop 16.10 would have

The only ones that I know of are:

+ ubuntu-desktop
+ ubuntu-gnome-desktop

However, the touchpad doesn't work, and neither do power management controls, such as pm-suspend

---

### Post by oldfred on 2017-05-02
I would not install more than one. You can and depending may not have issues/conflicts.
But if you just want to try one, better to allocate another 25GB and just install to that as a new / (root).

Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel
sudo apt install ubuntu-server
[URL="https://help.ubuntu.com/community/Tasksel"]https://help.ubuntu.com/community/Tasksel

      [/URL]
 [https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE & new in 17.04 Ubuntu Budgie
Mythbuntu discontinued Nov 2016 MythTV will continue to be available from the repositories just like any other package. 
    [URL="https://help.ubuntu.com/community/Tasksel"]
[/URL]
 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
MATE Desktop Environment
Or:
sudo apt-get install ubuntu-desktop
Minimal gnome fallback desktop, replaced with flashback in 14.04   gnome-session-flashback
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback
 Xenial flashback w/metacity tweaks
[http://ubuntuforums.org/showthread.php?t=2302432](http://ubuntuforums.org/showthread.php?t=2302432) 

[URL="https://help.ubuntu.com/community/Tasksel"]
[/URL]

---

### Post by naisanza on 2017-05-11
Perfect. Will give those a try. I think ubuntu-base gets installed along with ubuntu-desktop, but if I'm wrong, then that could be what I'm missing

---

