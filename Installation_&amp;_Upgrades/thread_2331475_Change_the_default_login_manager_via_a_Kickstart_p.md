---
title: "Change the default login manager via a Kickstart process"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by i2dave on 2016-07-22
I'm trying to install a new 16.04 LTS system via Kickstart / preseed over netboot, and would like to change the login manager showing on boot up.

The desktop is ubuntu-desktop, and the login manager I want to see is sddm (using the maldives theme).

If I add a line into the ks.cfg file (the kickstart runs via a local URL process) like so:

    echo "/usr/bin/sddm"  >  /etc/X11/default-display-manager

The PC reboots after kickstart and just shows a blank screen!

If I subsequently login and run "dpkg-reconfigure  -f noninteractive  sddm", and restart the sddm service, then it works!

So, is there a way I can run the reconfigure command from the kickstart process, or any other way I can set the default login manager to be sddm?

---

### Post by QDR06VV9 on 2016-07-22
> **i2dave said:**
> I'm trying to install a new 16.04 LTS system via Kickstart / preseed over netboot, and would like to change the login manager showing on boot up.

The desktop is ubuntu-desktop, and the login manager I want to see is sddm (using the maldives theme).

If I add a line into the ks.cfg file (the kickstart runs via a local URL process) like so:

    echo "/usr/bin/sddm"  >  /etc/X11/default-display-manager

The PC reboots after kickstart and just shows a blank screen!

If I subsequently login and run "dpkg-reconfigure  -f noninteractive  sddm", and restart the sddm service, then it works!

So, is there a way I can run the reconfigure command from the kickstart process, or any other way I can set the default login manager to be sddm?
See if this is of any use: [http://askubuntu.com/questions/697529/lightdm-sddm-fight-on-greeter-screen](http://askubuntu.com/questions/697529/lightdm-sddm-fight-on-greeter-screen)

---

