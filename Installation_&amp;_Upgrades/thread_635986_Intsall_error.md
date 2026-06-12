---
title: "Intsall error"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by whi on 2007-12-09
When I try to install something, I get this message:

[Only one software management tool is allowed to run at det same time

Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first

---

### Post by taurus on 2007-12-09
Do you happen to have synaptic or adept running while you try to install something with apt-get/aptitude?  If you do, you need to close it since you cannot run those processes at the same time, just one at a time.

---

### Post by whi on 2007-12-10
No... I only have open the apt-get/aptitude when I try to install

---

### Post by PmDematagoda on 2007-12-10
Could you please post the exact error you are getting?

---

### Post by whi on 2007-12-10
Only one software management tool is allowed to run at det same time

Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first



this is the message i get when i try to istall something....

---

### Post by taurus on 2007-12-10
Open a terminal and run this command.  Then, post the complete output here.

```
ps -A
```

---

### Post by whi on 2007-12-11
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
  118 ?        00:00:00 kseriod
  141 ?        00:00:00 pdflush
  142 ?        00:00:00 pdflush
  143 ?        00:00:00 kswapd0
  194 ?        00:00:00 aio/0
 2235 ?        00:00:00 ksuspend_usbd
 2236 ?        00:00:00 khubd
 2269 ?        00:00:00 ata/0
 2270 ?        00:00:00 ata_aux
 2617 ?        00:00:00 kjournald
 2822 ?        00:00:00 udevd
 3714 ?        00:00:00 kpsmoused
 3980 ?        00:00:00 avahi-autoipd
 3981 ?        00:00:00 avahi-autoipd
 3985 ?        00:00:00 dhclient3
 4354 tty4     00:00:00 getty
 4355 tty5     00:00:00 getty
 4358 tty2     00:00:00 getty
 4359 tty3     00:00:00 getty
 4360 tty1     00:00:00 getty
 4361 tty6     00:00:00 getty
 4565 ?        00:00:00 acpid
 4605 ?        00:00:00 kondemand/0
 4668 ?        00:00:00 syslogd
 4721 ?        00:00:00 dd
 4723 ?        00:00:00 klogd
 4744 ?        00:00:00 dbus-daemon
 4760 ?        00:00:00 NetworkManager
 4773 ?        00:00:00 NetworkManagerD
 4787 ?        00:00:00 system-tools-ba
 4788 ?        00:00:00 dbus-daemon
 4807 ?        00:00:00 hald
 4808 ?        00:00:00 hald-runner
 4852 ?        00:00:00 slmodemd
 4887 ?        00:00:00 hald-addon-keyb
 4888 ?        00:00:00 hald-addon-keyb
 4889 ?        00:00:00 hald-addon-keyb
 4891 ?        00:00:00 hald-addon-cpuf
 4892 ?        00:00:00 hald-addon-acpi
 4893 ?        00:00:00 hald-addon-keyb
 4894 ?        00:00:00 hald-addon-keyb
 4909 ?        00:00:00 cupsd
 4924 ?        00:00:00 hald-addon-stor
 5020 ?        00:00:00 console-kit-dae
 5105 ?        00:00:00 avahi-daemon
 5106 ?        00:00:00 avahi-daemon
 5120 ?        00:00:00 dhcdbd
 5140 ?        00:00:00 hcid
 5150 ?        00:00:00 bluetoothd-serv
 5151 ?        00:00:00 bluetoothd-serv
 5156 ?        00:00:00 krfcommd
 5178 ?        00:00:00 gdm
 5179 ?        00:00:00 gdm
 5191 tty7     00:00:03 Xorg
 5219 ?        00:00:00 atd
 5236 ?        00:00:00 cron
 5314 tty7     00:00:00 Xorg
 5403 ?        00:00:00 gnome-keyring-d
 5406 ?        00:00:00 x-session-manag
 5459 ?        00:00:00 Xgl-lockfile-wr
 5464 ?        00:00:07 Xgl
 5469 ?        00:00:00 ssh-agent
 5471 ?        00:00:01 gconfd-2
 5475 ?        00:00:00 dbus-daemon
 5477 ?        00:00:01 gnome-settings-
 5483 ?        00:00:00 compiz
 5485 ?        00:00:01 gnome-panel
 5487 ?        00:00:00 nautilus
 5491 ?        00:00:00 gnome-volume-ma
 5493 ?        00:00:00 bonobo-activati
 5509 ?        00:00:00 gtk-window-deco
 5510 ?        00:00:03 compiz.real
 5515 ?        00:00:00 gnome-vfs-daemo
 5528 ?        00:00:00 vino-session
 5530 ?        00:00:00 bluetooth-apple
 5532 ?        00:00:00 update-notifier
 5538 ?        00:00:00 evolution-alarm
 5540 ?        00:00:00 trackerd
 5543 ?        00:00:00 nm-applet
 5545 ?        00:00:00 python
 5576 ?        00:00:00 gnome-power-man
 5577 ?        00:00:00 gnome-screensav
 5647 ?        00:00:00 mapping-daemon
 5674 ?        00:00:00 wpa_supplicant
 5711 ?        00:00:00 trashapplet
 5715 ?        00:00:00 dhclient
 5786 ?        00:00:02 fast-user-switc
 5789 ?        00:00:00 mixer_applet2
 5790 ?        00:00:01 deskbar-applet
 5931 ?        00:00:08 opera
 5955 ?        00:00:00 operapluginwrap
 5956 ?        00:00:00 operapluginclea
 5960 ?        00:00:00 gnome-terminal
 5965 ?        00:00:00 gnome-pty-helpe
 5966 pts/1    00:00:00 bash
 5983 pts/1    00:00:00 ps

---

### Post by PmDematagoda on 2007-12-11
Sorry about this, but could you please post a screenshot of the error?

It is essential that the next step be proper instead of making a mistake since the problem is most likely a left-over lock file by a previous Package Management session that was not closed properly.

---

### Post by whi on 2007-12-11
Here...

---

### Post by whi on 2007-12-11
here

---

### Post by PmDematagoda on 2007-12-11
Hmm, there is nothing about a lock file, anyway, do:-

```
sudo rm /var/lib/dpkg/lock
```

Then do:-
```

sudo apt-get update
```

See if that solves your problem.

---

### Post by whi on 2007-12-11
Done that.. but it still don't work :(

This from the terminal:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Fetched 2B in 10s (0B/s)                                                       
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by whi on 2007-12-11
What to do now?

---

### Post by PmDematagoda on 2007-12-11
Your problem has been partly solved, now do:-

```
sudo dpkg --configure -a
```
as suggested by the error message.

That should solve your whole problem.

---

