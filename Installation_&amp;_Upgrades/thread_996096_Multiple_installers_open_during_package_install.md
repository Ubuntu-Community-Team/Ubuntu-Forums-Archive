---
title: "Multiple installers open during package install"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by thefiestysoldier on 2008-11-28
When I install a .deb package manually using package installer (navigating to it in the file browser then doubleclicking on it) it stops me from installing and asks me to close other package managers(no others are open)

---

### Post by taurus on 2008-11-28
Look at the output of this command from a terminal to see if synaptic, apt, apt-get, or adept running.

```
ps -A
```

---

### Post by thefiestysoldier on 2008-11-28
Heres the output during normal operation:
```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  120 ?        00:00:00 cqueue
  124 ?        00:00:00 kseriod
  158 ?        00:00:00 pdflush
  159 ?        00:00:00 pdflush
  160 ?        00:00:00 kswapd0
  200 ?        00:00:00 aio/0
 1103 ?        00:00:00 ksuspend_usbd
 1108 ?        00:00:00 khubd
 1121 ?        00:00:00 khpsbpkt
 1145 ?        00:00:00 ata/0
 1148 ?        00:00:00 ata_aux
 1416 ?        00:00:00 knodemgrd_0
 1429 ?        00:00:00 scsi_eh_0
 1430 ?        00:00:00 scsi_eh_1
 2005 ?        00:00:00 kjournald
 2179 ?        00:00:00 udevd
 2363 ?        00:00:00 kpsmoused
 2527 ?        00:00:00 pccardd
 3975 tty4     00:00:00 getty
 3976 tty5     00:00:00 getty
 3983 tty2     00:00:00 getty
 3984 tty3     00:00:00 getty
 3985 tty6     00:00:00 getty
 4158 ?        00:00:00 acpid
 4205 ?        00:00:00 kondemand/0
 4275 ?        00:00:00 syslogd
 4325 ?        00:00:00 dd
 4327 ?        00:00:00 klogd
 4350 ?        00:00:00 dbus-daemon
 4372 ?        00:00:00 avahi-daemon
 4373 ?        00:00:00 avahi-daemon
 4417 ?        00:00:00 cupsd
 4503 ?        00:00:00 winbindd
 4511 ?        00:00:00 winbindd
 4530 ?        00:00:00 hald
 4533 ?        00:00:00 console-kit-dae
 4596 ?        00:00:00 hald-runner
 4616 ?        00:00:00 hald-addon-dell
 4625 ?        00:00:00 hald-addon-acpi
 4627 ?        00:00:00 hald-addon-inpu
 4643 ?        00:00:00 hald-addon-stor
 4691 ?        00:00:00 bluetoothd
 4696 ?        00:00:00 btaddconn
 4698 ?        00:00:00 btdelconn
 4720 ?        00:00:00 krfcommd
 4742 ?        00:00:00 NetworkManager
 4746 ?        00:00:00 wpa_supplicant
 4749 ?        00:00:00 nm-system-setti
 4784 ?        00:00:00 gdm
 4785 ?        00:00:00 gdm
 4790 tty7     00:00:23 Xorg
 4822 ?        00:00:00 system-tools-ba
 4857 ?        00:00:00 atd
 4885 ?        00:00:00 cron
 4957 tty1     00:00:00 getty
 4993 ?        00:00:00 sh
 5105 ?        00:00:00 ssh-agent
 5108 ?        00:00:00 dbus-launch
 5109 ?        00:00:00 dbus-daemon
 5119 ?        00:00:00 xfce4-session
 5125 ?        00:00:00 gconfd-2
 5126 ?        00:00:00 gnome-screensav
 5128 ?        00:00:00 gvfsd
 5135 ?        00:00:00 xfce-mcs-manage
 5137 ?        00:00:00 gnome-keyring-d
 5138 ?        00:00:00 Thunar
 5141 ?        00:00:00 gam_server
 5142 ?        00:00:02 xfdesktop
 5144 ?        00:00:00 update-notifier
 5146 ?        00:00:01 pidgin
 5147 ?        00:00:00 gnome-power-man
 5210 ?        00:00:00 python
 5224 ?        00:00:00 python
 5226 ?        00:00:00 nm-applet
 5409 ?        00:00:00 dhclient
 5576 ?        00:00:05 compiz.real
 5582 ?        00:00:00 sh
 5583 ?        00:00:00 compiz-decorato
 5585 ?        00:00:00 gtk-window-deco
 5612 ?        00:00:01 jockey-backend
 5701 ?        00:00:02 avant-window-na
 5703 ?        00:00:01 awn-applet-acti
 5709 ?        00:00:00 gnome-vfs-daemo
 5749 ?        00:00:13 firefox
 5792 ?        00:00:00 xfce4-terminal
 5809 ?        00:00:00 gnome-pty-helpe
 5810 pts/1    00:00:00 bash
 5848 pts/1    00:00:00 ps
```



and after I open the Package installer(right before I press the Install Package Button):


```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  120 ?        00:00:00 cqueue
  124 ?        00:00:00 kseriod
  158 ?        00:00:00 pdflush
  159 ?        00:00:00 pdflush
  160 ?        00:00:00 kswapd0
  200 ?        00:00:00 aio/0
 1103 ?        00:00:00 ksuspend_usbd
 1108 ?        00:00:00 khubd
 1121 ?        00:00:00 khpsbpkt
 1145 ?        00:00:00 ata/0
 1148 ?        00:00:00 ata_aux
 1416 ?        00:00:00 knodemgrd_0
 1429 ?        00:00:00 scsi_eh_0
 1430 ?        00:00:00 scsi_eh_1
 2005 ?        00:00:00 kjournald
 2179 ?        00:00:00 udevd
 2363 ?        00:00:00 kpsmoused
 2527 ?        00:00:00 pccardd
 3975 tty4     00:00:00 getty
 3976 tty5     00:00:00 getty
 3983 tty2     00:00:00 getty
 3984 tty3     00:00:00 getty
 3985 tty6     00:00:00 getty
 4158 ?        00:00:00 acpid
 4205 ?        00:00:00 kondemand/0
 4275 ?        00:00:00 syslogd
 4325 ?        00:00:00 dd
 4327 ?        00:00:00 klogd
 4350 ?        00:00:00 dbus-daemon
 4372 ?        00:00:00 avahi-daemon
 4373 ?        00:00:00 avahi-daemon
 4417 ?        00:00:00 cupsd
 4503 ?        00:00:00 winbindd
 4511 ?        00:00:00 winbindd
 4530 ?        00:00:00 hald
 4533 ?        00:00:00 console-kit-dae
 4596 ?        00:00:00 hald-runner
 4616 ?        00:00:00 hald-addon-dell
 4625 ?        00:00:00 hald-addon-acpi
 4627 ?        00:00:00 hald-addon-inpu
 4643 ?        00:00:00 hald-addon-stor
 4691 ?        00:00:00 bluetoothd
 4696 ?        00:00:00 btaddconn
 4698 ?        00:00:00 btdelconn
 4720 ?        00:00:00 krfcommd
 4742 ?        00:00:00 NetworkManager
 4746 ?        00:00:00 wpa_supplicant
 4749 ?        00:00:00 nm-system-setti
 4784 ?        00:00:00 gdm
 4785 ?        00:00:00 gdm
 4790 tty7     00:01:43 Xorg
 4822 ?        00:00:00 system-tools-ba
 4857 ?        00:00:00 atd
 4885 ?        00:00:00 cron
 4957 tty1     00:00:00 getty
 4993 ?        00:00:00 sh
 5105 ?        00:00:00 ssh-agent
 5108 ?        00:00:00 dbus-launch
 5109 ?        00:00:00 dbus-daemon
 5119 ?        00:00:00 xfce4-session
 5125 ?        00:00:00 gconfd-2
 5126 ?        00:00:01 gnome-screensav
 5128 ?        00:00:00 gvfsd
 5135 ?        00:00:00 xfce-mcs-manage
 5137 ?        00:00:00 gnome-keyring-d
 5138 ?        00:00:01 Thunar
 5141 ?        00:00:00 gam_server
 5142 ?        00:00:02 xfdesktop
 5144 ?        00:00:00 update-notifier
 5146 ?        00:00:01 pidgin
 5147 ?        00:00:00 gnome-power-man
 5210 ?        00:00:00 python
 5224 ?        00:00:00 python
 5226 ?        00:00:00 nm-applet
 5409 ?        00:00:00 dhclient
 5576 ?        00:00:08 compiz.real
 5582 ?        00:00:00 sh
 5583 ?        00:00:00 compiz-decorato
 5585 ?        00:00:01 gtk-window-deco
 5612 ?        00:00:01 jockey-backend
 5701 ?        00:00:03 avant-window-na
 5703 ?        00:00:01 awn-applet-acti
 5709 ?        00:00:00 gnome-vfs-daemo
 5749 ?        00:00:52 firefox
 5792 ?        00:00:01 xfce4-terminal
 5809 ?        00:00:00 gnome-pty-helpe
 5810 pts/1    00:00:00 bash
 6111 ?        00:00:02 gdebi-gtk
 6139 pts/1    00:00:00 ps

```

After examining the output the only suspicious process I saw was number 5144(but I may be wrong)

---

