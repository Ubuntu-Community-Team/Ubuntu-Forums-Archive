---
title: "Too many proccess running?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by terrordrone on 2008-03-21
Im on a new install of gutsy
im really impressed with the speed, usabitility etc
ive installed a lot of new softwares...  Listen, vlc , thunderbird, usplash , etc

ive stopped apache2, mysql etc running on start up

but still its sluggish

this is the output of ps -A


 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  161 ?        00:00:00 kseriod
  189 ?        00:00:00 pdflush
  190 ?        00:00:00 pdflush
  191 ?        00:00:01 kswapd0
  242 ?        00:00:00 aio/0
  243 ?        00:00:00 aio/1
 2167 ?        00:00:00 ata/0
 2168 ?        00:00:00 ata/1
 2187 ?        00:00:00 ata_aux
 2191 ?        00:00:00 ksuspend_usbd
 2192 ?        00:00:00 khubd
 2248 ?        00:00:00 khpsbpkt
 2328 ?        00:00:00 scsi_eh_0
 2329 ?        00:00:00 scsi_eh_1
 2369 ?        00:00:00 knodemgrd_0
 2567 ?        00:00:00 kjournald
 2828 ?        00:00:00 udevd
 3897 ?        00:00:00 kmmcd
 3909 ?        00:00:00 kpsmoused
 4202 ?        00:00:00 ntos_wq/0
 4203 ?        00:00:00 ntos_wq/1
 4204 ?        00:00:00 ndis_wq
 4205 ?        00:00:00 wrapndis_wq/0
 4206 ?        00:00:00 wrapndis_wq/1
 4427 ?        00:00:00 mount.ntfs
 4430 ?        00:00:00 mount.ntfs
 4433 ?        00:00:00 mount.ntfs
 4436 ?        00:00:04 mount.ntfs
 4680 tty4     00:00:00 getty
 4681 tty5     00:00:00 getty
 4683 tty2     00:00:00 getty
 4685 tty3     00:00:00 getty
 4687 tty1     00:00:00 getty
 4688 tty6     00:00:00 getty
 4912 ?        00:00:00 acpid
 4951 ?        00:00:00 kondemand/0
 4952 ?        00:00:00 kondemand/1
 5032 ?        00:00:00 syslogd
 5090 ?        00:00:00 dd
 5092 ?        00:00:00 klogd
 5115 ?        00:00:00 dbus-daemon
 5133 ?        00:00:00 NetworkManager
 5149 ?        00:00:00 NetworkManagerD
 5164 ?        00:00:00 system-tools-ba
 5165 ?        00:00:00 dbus-daemon
 5186 ?        00:00:00 hald
 5187 ?        00:00:00 hald-runner
 5250 ?        00:00:00 hald-addon-keyb
 5251 ?        00:00:00 hald-addon-keyb
 5252 ?        00:00:00 hald-addon-keyb
 5253 ?        00:00:00 hald-addon-keyb
 5256 ?        00:00:00 hald-addon-cpuf
 5257 ?        00:00:00 hald-addon-acpi
 5267 ?        00:00:00 hald-addon-keyb
 5330 ?        00:00:00 console-kit-dae
 5420 ?        00:00:00 avahi-daemon
 5421 ?        00:00:00 avahi-daemon
 5438 ?        00:00:00 dhcdbd
 5463 ?        00:00:00 hcid
 5477 ?        00:00:00 bluetoothd-serv
 5479 ?        00:00:00 bluetoothd-serv
 5488 ?        00:00:00 krfcommd
 5498 ?        00:00:01 hald-addon-stor
 5512 ?        00:00:00 gdm
 5530 ?        00:00:00 gdm
 5547 tty7     00:02:18 Xorg
 5555 ?        00:00:00 atd
 5571 ?        00:00:00 cron
 5910 ?        00:00:00 gnome-keyring-d
 5913 ?        00:00:00 x-session-manag
 5948 ?        00:00:00 ssh-agent
 5950 ?        00:00:00 gconfd-2
 5954 ?        00:00:00 dbus-daemon
 5956 ?        00:00:00 gnome-settings-
 5960 ?        00:00:00 compiz
 5965 ?        00:00:04 gnome-panel
 5969 ?        00:00:12 nautilus
 6016 ?        00:00:00 bonobo-activati
 6019 ?        00:00:00 gnome-volume-ma
 6035 ?        00:00:00 gnome-vfs-daemo
 6054 ?        00:00:02 gtk-window-deco
 6055 ?        00:00:07 compiz.real
 6056 ?        00:00:03 gnome-screensav
 6062 ?        00:00:00 vino-session
 6064 ?        00:00:00 bluetooth-apple
 6071 ?        00:00:00 update-notifier
 6078 ?        00:00:00 evolution-alarm
 6080 ?        00:00:09 trackerd
 6085 ?        00:00:00 nm-applet
 6088 ?        00:00:00 gnome-power-man
 6096 ?        00:00:00 trashapplet
 6108 ?        00:00:00 mapping-daemon
 6125 ?        00:00:00 evolution-excha
 6143 ?        00:00:00 evolution-data-
 6165 ?        00:00:00 deskbar-applet
 6167 ?        00:00:00 mixer_applet2
 6210 ?        00:00:00 firefox
 6222 ?        00:00:00 run-mozilla.sh
 6226 ?        00:02:51 firefox-bin
 6246 ?        00:00:01 pidgin
 6250 ?        00:00:00 alltray
 6253 ?        00:00:00 thunderbird
 6264 ?        00:00:00 run-mozilla.sh
 6268 ?        00:00:33 thunderbird-bin
 6607 ?        00:00:00 sh
 6608 ?        00:00:00 gnome-terminal
 6613 ?        00:00:00 gnome-pty-helpe
 6614 pts/0    00:00:00 bash
 6632 pts/0    00:00:00 ps



I think thats a lot of processes
and also there are a few k* proccess... are they KDE processes?

are there any of the procces that i can stop?

---

### Post by kostkon on 2008-03-21
It looks good for me. I can see that you have two instances of *Firefox* running. Although, I may be wrong.

Run top and check for any processes that may eat a lot of resources.

By the way, what graphics card do you have? If you have an Nvidia/ATI one, which driver do you use for it?

---

### Post by terrordrone on 2008-03-21
i had only one instance of firefox

im on a laptop..  so its intel gma 950 i guess

---

