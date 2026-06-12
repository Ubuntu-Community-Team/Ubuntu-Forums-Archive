---
title: "The application compiz has closed unexpectedly error in ubuntu 12.10"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by anoopp on 2012-11-29
Hi,

Few weeks back i had upgraded to ubuntu 12.10 from ubuntu 12.04. After few updates whenever i start my laptop i am getting an error with description "The application compiz has closed unexpectedly" (See the screenshot for more details).


Any pointer to resolve this problem.

---

### Post by dino99 on 2012-11-29
it could be a few things to do:

- open synaptic to purge all the related installed compiz packages, then reinstall compiz

- do the same thing with the video driver

- sudo rm /etc/X11/xorg.conf

then reboot

note: on dist-upgrade, often the old settings can do weird issues; you can erase (or rename): .gconf, .config, .gnome2 , .local (hidden folders inside /home, ctrl+h to unhide them). They will be cleanly recreated on next boot (but without your custom tweaks, as its the default settings)

---

### Post by anoopp on 2012-11-29
> **dino99 said:**
> it could be a few things to do:

- open synaptic to purge all the related installed compiz packages, then reinstall compiz

- do the same thing with the video driver

- sudo rm /etc/X11/xorg.conf

then reboot

Thanks for the reply dino. Could you please explain the first and second steps in detail?

---

### Post by dino99 on 2012-11-29
sudo apt-get install synaptic
(if not yet installed)

sudo synaptic

there, search the installed *compiz* packages (left pane: select "status" from bottom, then "installed" from top), and select each one to purge them (right-click) (remove them all, then select compiz for reinstallation)

can do the same with your video driver (xserver-xorg-video-xxxx , where xxxx is yours (either nvidia/amd/intel/...)

---

### Post by anoopp on 2012-11-29
Dino, Thanks for the reply again :). I will check it out and let you know.

---

