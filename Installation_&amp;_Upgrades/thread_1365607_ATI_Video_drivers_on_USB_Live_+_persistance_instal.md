---
title: "ATI Video drivers on USB Live + persistance install"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by footloose143 on 2009-12-27
Hi 

I've able to successfully install and run ubuntu on USB drive with persistance mode (installation from USB start up disk creator + persistance file), I could also be able to install a couple of video codecs on this installation and works cool, but I have an issue with my video drivers.

I have ATI Radeo video card after installtion I also configure it using
sudo /usr/bin/aticonfig --initial
which updated by /etc/X11/xorg.conf file with the appropriate driver info but the problem I have is its lost every time I reeboot and I am unableto enable my video card :(

However I can see all the ATI catalyst Control centre in my preferences and when I launch it it shows up No ATI graphics card installed or not functioning properly. 

Did anyone faced issues with Video card drivers on USB persistance install and have a working solution? Please dont ask me to install ubuntu on my USB instead of persistance mode USB install I am trying to find a way for this problem on this type of installation. 

Please help!

---

### Post by footloose143 on 2009-12-27
no one???

---

### Post by efflandt on 2009-12-27
Not sure exactly which files are persistent or not, some seem to get overwritten during reboot.  For example I set a password for "ubuntu" and was trying to get bootable iso to not autologin as ubuntu, but those attempts disappeared during reboot.

When I activated Broadcom STA for my wireless and had to reboot to activate it, it still was not loaded (Hardware Drivers then said "activated, but not used").  So I had to manually **modprobe wl** before I could use Broadcom wireless.  So I added something to /home/ubuntu/.profile to modprobe wl, if grep found the Broadcom device in lspci, but not if grep already found "wl" in lsmod. (Note: On a regular install on USB hard drive, "wl" was automatically used on boot once Broadcom STA was activated).

It may take some knowledge and practice at bash scripting, but if you can do something from the command line to make it work, you could probably add something to /home/ubuntu/.profile to do whatever you need to do before X starts.

Part of the problem may be that kernel and initscripts run during boot may be fixed, before the persistent data file (casper-rw) is mounted.  So another way to modify things is to modify the iso itself (which takes a bit more knowledge and work) before you write it to bootable USB.

---

### Post by footloose143 on 2009-12-27
got an ugly hack but does the trick ...

I assume while booting live mode it recreates X11/xorg file so I have taken a backup of /etc/X11/xorg.conf  after aticonfig --initial and updated .profile of ubuntu user to copy this backed up file to /etc/X11 and it now works as charm!!!

---

### Post by footloose143 on 2009-12-27
Thanks effland!

---

