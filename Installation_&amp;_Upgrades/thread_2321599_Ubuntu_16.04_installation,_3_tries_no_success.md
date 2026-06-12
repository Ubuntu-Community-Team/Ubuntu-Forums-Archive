---
title: "Ubuntu 16.04 installation, 3 tries no success"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by egandt on 2016-04-23
First the Desktop version installation, does not work in VMWARE 12.1 see my other post (VMware 12.1 and Ubuntu Desktop 16.04, unable to complete GUI installation).

Second I've done a single full install based off of Server and then installing all the required products (this is the only install so far that mostly worked), however many applications: Firefox, Thunderbird, Libre Office ... simply did not load and throw now errors to allow troubleshooting.  Note the ssdm manager does not work well (if at all), sometimes after 5 minutes it would load othertimes I had to manually force init 3 and then back to init 5 and wait to get a screen to login, lightdm worked here.

My last install was Ubuntu 16.04 Server and then I installed the desktop packages: 
    apt-get install aptitude
    apt-get install xubuntu-desktop ubuntu-desktop kubuntu-desktop ubuntu-gnome-destop open-vm-tools-desktop
    # need to fix telepathy manually by removal through aptitude (no idea why there are actual broken packages after this)
    apt-get install -f
    apt-get autoremove
    reboot
Simply put while it does boot, the GUI is completely hung (lightdm in this case since it worked best last time), in fact it takes no mouse of keyboard input.  Now this install is still operational and I can shut it down, but as the GUI is hung well, I'm unwilling to do much less with it, but call it another failed attempt.  I've waited 15 minutes without response from the UI.  This is a reasonably simple install simply adding vm-tools (as it is running in VMWARE) and the standard desktops.

Simply put all of my installs are on VMWARE, but multiple failures one after another as well as having to fix packages after install kubuntu-desktop are all bad signs when it comes to stability and testing.

For now I'm in no need of an upgrade, but it is the least stable Ubuntu version I've ever tested upon release.
ERIC

---

### Post by egandt on 2016-04-23
Please note I'm well aware I could likely fix the last two installs if I wanted to spend the time and effort, my point is that it should not be needed, and it speaks volumes to the stability of the 16.04LTS release that these issues are occurring.

ERIC

---

### Post by ajgreeny on 2016-04-23
I've never used vmware but there was a problem for some using VirtualBox with kernel numbers 4.4.0-20 and there is also a bug which may or may not be related [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221)
See [http://ubuntuforums.org/showthread.php?t=2320780&p=13472202&viewfull=1#post13472202](http://ubuntuforums.org/showthread.php?t=2320780&p=13472202&viewfull=1#post13472202)

---

