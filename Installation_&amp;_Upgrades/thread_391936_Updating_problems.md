---
title: "Updating problems"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Olsson on 2007-03-23
Hi. I can't update cause it says that I should close the other applications e.g. 'aptitude' or 'synaptic. But the problem is that I iant got any applications like that.. I ve tried to reboot many times but it won't work ;/ And I'm not running any applications that I'm aware of. What should I do?

Thank you

---

### Post by taurus on 2007-03-23
Open a terminal and paste the output of this command here.

Applications -> Accessories -> Terminal
```
ps  -A
```

---

### Post by Olsson on 2007-03-23
Dosen't seem to work.. what should it do anyway? I'm rebooting now so we'll see if it might work after that.

---

### Post by taurus on 2007-03-23
It should give you a list of all the processes currently running.  I just want to see if you somehow have adept running in the background that prevents synaptic/apt-get/aptitude from running.

---

### Post by Olsson on 2007-03-23
Here it is:  

PID TTY          TIME CMD
    1 ?        00:00:05 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
   61 ?        00:00:00 pdflush
   62 ?        00:00:00 pdflush
   64 ?        00:00:00 aio/0
   63 ?        00:00:00 kswapd0
  657 ?        00:00:00 kseriod
 1777 ?        00:00:00 khubd
 1848 ?        00:00:00 kjournald
 2073 ?        00:00:01 udevd
 2850 ?        00:00:00 shpchpd_event
 2947 ?        00:00:00 kgameportd
 3620 ?        00:00:00 syslogd
 3646 ?        00:00:00 dd
 3648 ?        00:00:00 klogd
 3971 ?        00:00:00 gdm
 3974 ?        00:00:00 gdm
 3997 tty7     00:00:17 Xorg
 4014 ?        00:00:00 hpiod
 4018 ?        00:00:00 python
 4021 ?        00:00:00 hpiod
 4022 ?        00:00:00 hpiod
 4066 ?        00:00:00 cupsd
 4076 ?        00:00:00 kapmd
 4087 ?        00:00:00 apmd
 4113 ?        00:00:00 dbus-daemon
 4198 ?        00:00:08 hald
 4199 ?        00:00:00 hald-runner
 4391 ?        00:00:00 hald-addon-keyb
 4402 ?        00:00:00 hald-addon-stor
 4403 ?        00:00:00 hald-addon-stor
 4405 ?        00:00:00 hald-addon-stor
 4406 ?        00:00:00 hald-addon-stor
 4486 ?        00:00:00 hcid
 4490 ?        00:00:00 sdpd
 4502 ?        00:00:00 krfcommd
 4516 ?        00:00:00 mdadm
 4551 ?        00:00:00 atd
 4564 ?        00:00:00 cron
 4636 tty1     00:00:00 getty
 4637 tty2     00:00:00 getty
 4638 tty3     00:00:00 getty
 4639 tty4     00:00:00 getty
 4640 tty5     00:00:00 getty
 4641 tty6     00:00:00 getty
 4652 ?        00:00:02 x-session-manag
 4695 ?        00:00:00 ssh-agent
 4698 ?        00:00:00 dbus-launch
 4699 ?        00:00:00 dbus-daemon
 4701 ?        00:00:03 gconfd-2
 4704 ?        00:00:00 gnome-keyring-d
 4706 ?        00:00:00 bonobo-activati
 4708 ?        00:00:01 gnome-settings-
 4728 ?        00:00:00 gnome-settings-
 4729 ?        00:00:00 gnome-settings-
 4773 ?        00:00:08 metacity
 4778 ?        00:00:08 gnome-panel
 4780 ?        00:00:06 nautilus
 4785 ?        00:00:00 gnome-volume-ma
 4789 ?        00:00:00 trashapplet
 4793 ?        00:00:02 update-notifier
 4794 ?        00:00:00 nautilus
 4795 ?        00:00:00 trashapplet
 4796 ?        00:00:00 trashapplet
 4798 ?        00:00:00 gnome-vfs-daemo
 4799 ?        00:00:00 nautilus
 4805 ?        00:00:00 gnome-vfs-daemo
 4806 ?        00:00:00 gnome-vfs-daemo
 4810 ?        00:00:01 gnome-cups-icon
 4814 ?        00:00:00 gnome-panel
 4815 ?        00:00:00 gnome-panel
 4820 ?        00:00:00 mapping-daemon
 4822 ?        00:00:00 gnome-power-man
 4826 ?        00:00:00 gnome-cups-icon
 4842 ?        00:00:00 multiload-apple
 4850 ?        00:00:01 clock-applet
 4856 ?        00:00:02 mixer_applet2
 4860 ?        00:00:00 gnome-screensav
 4870 ?        00:00:02 notification-da
 5201 ?        00:00:03 gnome-terminal
 5204 ?        00:00:00 gnome-pty-helpe
 5205 pts/0    00:00:01 bash
 5206 ?        00:00:00 gnome-terminal
 5210 ?        00:00:00 gnome-terminal
 5226 pts/0    00:00:00 ps

What should i close down and how?

---

### Post by taurus on 2007-03-23
From one of the three terminals that you have, what happens when you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Olsson on 2007-03-23
Got it working now! Thanks :)

---

