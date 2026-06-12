---
title: "How to reorder dual boot startup priority?"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2010-08-01
By default, after 10 seconds grace, my dual boot computer starts up Ubuntu. Since it is being shared, I want to re-order the dual-boot selection to start with Windows instead without having to re-install Ubuntu. Thanks in anticipation of.

---

### Post by aeronutt on 2010-08-01
Assuming you're using grub 2

Edit '/etc/default/grub'
Change the line "GRUB_DEFAULT=0" to the menu entry in grub.cfg that you want the default to be. IE GRUB_DEFAULT Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.

You can also change the 10sec to whatever you wish by changing "GRUB_TIMEOUT=10".

Run sudo update-grub

More info
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


EDIT:  Just learned of this 'startupmanager', GUI for grub2, install via synaptic package manager.
Probably does everything you need and more.
Some info on it 
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by badaveil on 2010-08-02
> **aeronutt said:**
> Assuming you're using grub 2

Edit '/etc/default/grub'
Change the line "GRUB_DEFAULT=0" to the menu entry in grub.cfg that you want the default to be. IE GRUB_DEFAULT Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.

You can also change the 10sec to whatever you wish by changing "GRUB_TIMEOUT=10".

Run sudo update-grub

More info
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


EDIT:  Just learned of this 'startupmanager', GUI for grub2, install via synaptic package manager.
Probably does everything you need and more.
Some info on it 
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Your startup-manager  advice worked liked a breeze. Cool coz I'm a GUI-Man.

---

