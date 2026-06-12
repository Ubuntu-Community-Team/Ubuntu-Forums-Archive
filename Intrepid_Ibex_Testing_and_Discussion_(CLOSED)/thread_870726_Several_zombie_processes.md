---
title: "Several zombie processes"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by spamzilla on 2008-07-26
Recently, I've had a lot of zombie processes in System Monitor. Is this something I am just experiencing or is this happening to other people too?

---

### Post by Bachstelze on 2008-07-26
Nope, no zombies here. Maybe you should call Jill ;)

---

### Post by spamzilla on 2008-07-26
> **HymnToLife said:**
> Nope, no zombies here. Maybe you should call Jill ;)

I'm not even going to pretend to know what you mean!!

While off topic, Brest sounds like a fantastic place in France :P

---

### Post by Bachstelze on 2008-07-26
> **spamzilla said:**
> I'm not even going to pretend to know what you mean!!

Never played Resident Evil ? ;)

And yes, Brest is a very nice place indeed, but we're really getting off-topic now.

---

### Post by taavikko on 2008-07-26
```
ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   43 ?        00:00:00 kblockd/0
   45 ?        00:00:00 kacpid
   46 ?        00:00:00 kacpi_notify
  126 ?        00:00:00 kseriod
  163 ?        00:00:00 pdflush
  164 ?        00:00:00 pdflush
  165 ?        00:00:00 kswapd0
  206 ?        00:00:00 aio/0
  865 ?        00:00:00 aufsd
  866 ?        00:00:00 aufsd
  867 ?        00:00:00 aufsd
  868 ?        00:00:00 aufsd
  952 ?        00:00:00 cqueue
 1801 ?        00:00:00 ksuspend_usbd
 1804 ?        00:00:00 khubd
 1834 ?        00:00:01 ata/0
 1840 ?        00:00:00 ata_aux
 1843 ?        00:00:00 khpsbpkt
 1929 ?        00:00:00 knodemgrd_0
 1930 ?        00:00:01 scsi_eh_0
 1931 ?        00:00:00 scsi_eh_1
 1933 ?        00:00:00 scsi_eh_2
 1936 ?        00:00:00 scsi_eh_3
 1939 ?        00:00:00 scsi_eh_4
 2120 ?        00:00:00 kjournald
 2285 ?        00:00:00 udevd
 3322 ?        00:00:00 ipw2200/0
 3386 ?        00:00:00 kpsmoused
 3815 ?        00:00:00 kjournald
 3816 ?        00:00:00 kjournald
 3817 ?        00:00:00 kjournald
 3818 ?        00:00:00 kjournald
 4073 tty2     00:00:00 getty
 4241 ?        00:00:00 acpid
 4294 ?        00:00:00 kondemand/0
 4349 ?        00:00:00 syslogd
 4396 ?        00:00:00 dd
 4398 ?        00:00:00 klogd
 4419 ?        00:00:05 dbus-daemon
 4437 ?        00:00:01 NetworkManager
 4453 ?        00:00:00 NetworkManagerD
 4472 ?        00:00:00 avahi-daemon
 4473 ?        00:00:00 avahi-daemon
 4501 ?        00:00:00 cupsd
 4531 ?        00:00:00 dhcdbd
 4552 ?        00:00:03 hald
 4555 ?        00:00:00 console-kit-dae
 4618 ?        00:00:00 hald-runner
 4638 ?        00:00:00 hald-addon-inpu
 4643 ?        00:00:00 hald-addon-cpuf
 4644 ?        00:00:00 hald-addon-acpi
 4683 ?        00:00:01 hald-addon-stor
 4706 ?        00:00:00 gdm
 4711 ?        00:00:00 gdm
 4728 ?        00:00:00 system-tools-ba
 4757 ?        00:00:00 cron
 4802 tty1     00:00:00 getty
 4853 ?        00:00:00 dhclient
 5169 ?        00:00:00 gvfs-fuse-daemo
 5643 tty7     00:08:02 Xorg
 5666 ?        00:00:01 gconfd-2
 5668 ?        00:00:00 gnome-keyring-d
 5678 ?        00:00:00 x-session-manag
 5755 ?        00:00:00 dbus-daemon
 5757 ?        00:00:00 dbus-launch
 5764 ?        00:00:01 gnome-settings-
 5765 ?        00:00:00 gnome-keyring-d
 5772 ?        00:02:08 metacity
 5781 ?        00:00:00 gvfs-gphoto2-vo
 5782 ?        00:00:11 gnome-panel
 5783 ?        00:00:03 nautilus
 5786 ?        00:00:00 bonobo-activati
 5789 ?        00:00:00 gvfs-hal-volume
 5792 ?        00:00:01 padevchooser
 5793 ?        00:00:00 gnome-power-man <defunct>
 5794 ?        00:00:00 pactl <defunct>
 5795 ?        00:00:00 gnome-volume-ma <defunct>
 5796 ?        00:00:00 jockey-gtk <defunct>
 5800 ?        00:00:00 gvfsd
 5801 ?        00:00:01 gnome-power-man
 5808 ?        00:00:00 gvfs-fuse-daemo
 5811 ?        00:00:00 gnome-volume-ma
 5813 ?        00:03:45 pulseaudio
 5883 ?        00:00:00 gconf-helper
 5916 ?        00:00:13 gnome-screensav
 5919 ?        00:00:00 gvfsd-burn
 5922 ?        00:00:00 gvfsd-trash
 7238 ?        00:00:00 trackerd
 7277 ?        00:00:03 gnome-terminal
 7279 ?        00:00:00 gnome-pty-helpe
 7280 pts/0    00:00:00 bash
 7329 ?        00:01:34 transmission
11298 ?        00:00:07 firefox
11345 pts/0    00:00:00 ps

```

Zombies are lurking here also.
Maybe the "g-volume-manager" Is the reason why, Memorycards- and sticks are not mounting properly.

Always double-mounts, in nautilus listview"bookmarks"

---

### Post by Bachstelze on 2008-07-26
Blame Gnome, I guess...

```
firas@nobue mplayer % ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        S<     0:01 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0] 
    6 ?        S<     0:00 [migration/1]
    7 ?        S<     0:02 [ksoftirqd/1]
    8 ?        S<     0:00 [watchdog/1] 
    9 ?        S<     0:00 [events/0]   
   10 ?        S<     0:00 [events/1]   
   11 ?        S<     0:00 [khelper]    
   48 ?        S<     0:00 [kblockd/0]  
   49 ?        S<     0:00 [kblockd/1]  
   51 ?        S<     0:00 [kacpid]     
   52 ?        S<     0:00 [kacpi_notify]
  159 ?        S<     0:00 [kseriod]     
  204 ?        S      0:00 [pdflush]     
  205 ?        S      0:01 [pdflush]     
  206 ?        S<     0:00 [kswapd0]     
  247 ?        S<     0:00 [aio/0]       
  248 ?        S<     0:00 [aio/1]       
  913 ?        S<     0:00 [aufsd]       
  914 ?        S<     0:00 [aufsd]       
  915 ?        S<     0:00 [aufsd]       
  916 ?        S<     0:00 [aufsd]       
  982 ?        S<     0:00 [cqueue]      
 1904 ?        S<     0:00 [ksuspend_usbd]
 1909 ?        S<     0:00 [khubd]        
 1932 ?        S<     0:00 [ata/0]        
 1935 ?        S<     0:06 [ata/1]        
 1936 ?        S<     0:00 [khpsbpkt]     
 1937 ?        S<     0:00 [ata_aux]      
 2046 ?        S<     0:11 [scsi_eh_0]    
 2047 ?        S<     0:00 [scsi_eh_1]    
 2050 ?        S<     0:00 [scsi_eh_2]    
 2051 ?        S<     0:00 [scsi_eh_3]    
 2062 ?        S<     0:00 [scsi_eh_4]    
 2063 ?        S<     0:00 [scsi_eh_5]    
 2074 ?        S<     0:00 [scsi_eh_6]    
 2075 ?        S<     0:00 [scsi_eh_7]    
 2119 ?        S<     0:00 [knodemgrd_0]  
 2207 ?        S<     0:00 [scsi_eh_8]    
 2209 ?        S<     0:02 [usb-storage]  
 2313 ?        S<     0:09 [md0_raid5]    
 2474 ?        S<     0:01 [kjournald]    
 2609 ?        S<s    0:00 /sbin/udevd --daemon
 3996 ?        S<     0:00 [kpsmoused]         
 4271 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --sysl
 4313 ?        S<     0:00 [kjournald]                                                                          
 4320 ?        S<     0:00 [xfslogd/0]                                                                          
 4321 ?        S<     0:00 [xfslogd/1]                                                                          
 4322 ?        S<     0:00 [xfsdatad/0]                                                                         
 4323 ?        S<     0:00 [xfsdatad/1]                                                                         
 4324 ?        S<     0:00 [xfs_mru_cache]                                                                      
 4325 ?        S<     0:00 [xfsbufd]                                                                            
 4335 ?        S<     0:00 [xfsaild]                                                                            
 4336 ?        S<     0:00 [xfssyncd]                                                                           
 4690 tty4     Ss+    0:00 /sbin/getty 38400 tty4                                                               
 4691 tty5     Ss+    0:00 /sbin/getty 38400 tty5                                                               
 4696 tty2     Ss     0:00 /bin/login --                                                                        
 4697 tty3     Ss+    0:00 /sbin/getty 38400 tty3                                                               
 4706 tty6     Ss+    0:00 /sbin/getty 38400 tty6                                                               
 4864 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket                         
 4895 ?        Ss     0:00 /sbin/syslogd -u syslog                                                              
 4943 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg                                    
 4944 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg                                                   
 4962 ?        Ss     0:00 /bin/dbus-daemon --system                                                            
 5250 ?        Ss     0:00 /usr/sbin/exim4 -bd -q30m                                                            
 5270 ?        Ss     0:00 /usr/sbin/hald                                                                       
 5273 ?        Ssl    0:00 /usr/sbin/console-kit-daemon                                                         
 5274 ?        S      0:00 hald-runner                                                                          
 5357 ?        S      0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event3 /dev/input/event1 
 5371 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket                     
 5401 ?        S      0:00 hald-addon-storage: polling /dev/sde (every 2 sec)                                   
 5404 ?        S      0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)                                   
 5407 ?        S      0:00 hald-addon-storage: polling /dev/sdg (every 2 sec)                                   
 5410 ?        S      0:00 hald-addon-storage: polling /dev/sdh (every 2 sec)                                   
 5413 ?        S      0:10 hald-addon-storage: polling /dev/scd0 (every 2 sec)                                  
 5435 ?        Ss     0:00 /usr/sbin/atd                                                                        
 5460 ?        Ss     0:00 /usr/sbin/cron                                                                       
 5476 tty1     Ss+    0:00 /sbin/getty 38400 tty1                                                               
 5892 tty2     S+     0:00 -zsh                                                                                 
 5924 ?        Ss     0:00 /usr/bin/kdm                                                                         
 5926 tty7     SLs+  18:41 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-C3iVqd                  
 5935 ?        S      0:00 -:0                                                                                  
 5940 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session                   
 5941 ?        S      0:00 dbus-launch --autolaunch ec892096e614f857472f3f4c488850f8 --binary-syntax --close-std
 5948 ?        Ss     0:00 /usr/bin/ck-launch-session /usr/bin/startkde                                         
 5976 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/startkde                      
 5989 ?        S      0:00 /bin/sh /usr/bin/startkde                                                            
 6072 ?        S      0:00 dbus-launch --sh-syntax --exit-with-session                                          
 6073 ?        Ss     0:02 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session                   
 6078 ?        Ss     0:00 kdeinit4: kdeinit4 Run up                                                            
 6079 ?        S      0:00 klauncher                                                                            
 6081 ?        S      0:23 kded4                                                                                
 6086 ?        S      0:00 kwrapper4 ksmserver                                                                  
 6087 ?        Sl     0:00 ksmserver                                                                            
 6089 ?        SL     0:34 kwin -session 10d36f6275000121689669400000063850000_1217016922_661567
 6092 ?        S      0:04 /usr/bin/knotify4
 6093 ?        Sl     1:52 /usr/bin/plasma
 6097 ?        Sl     0:03 /usr/bin/krunner
 6099 ?        Sl     0:00 /usr/bin/nepomukserver
 6111 ?        S      0:00 /usr/bin/nepomukservicestub nepomukstorage
 6112 ?        S      0:00 /usr/bin/nepomukservicestub nepomukontologyloader
 6113 ?        S      0:00 /usr/bin/nepomukservicestub nepomukfilewatch
 6114 ?        S      0:11 pidgin --session 10d36f6275000121690090200000063850021 --display :0.0
 6116 ?        S      0:02 /usr/bin/klipper
 6118 ?        S      0:00 /usr/bin/korgac -icon korgac
 6153 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 14
 6172 ?        Sl     0:58 /usr/bin/konsole
 6174 pts/1    Ss     0:00 /bin/zsh
 6181 pts/1    S+     0:00 ssh izumi
 6222 ?        S      2:04 /usr/bin/kontact
 6227 ?        S      0:00 /usr/bin/kwalletd
 7069 ?        S      0:04 kdeinit4: kio_imap4 [k up
 7189 ?        S      0:00 kdeinit4: kio_file [kd up
 7568 pts/2    Ss     0:00 /bin/zsh
 7575 pts/2    S+     0:00 ssh iori
 7585 pts/3    Ss     0:03 /bin/zsh
 8513 ?        Ss     0:00 /usr/sbin/sshd
 9124 ?        S      0:00 /bin/sh -c firefox
 9125 ?        Sl     8:40 /usr/lib/firefox-3.0.1/firefox
 9319 ?        S      0:19 /usr/bin/kate --use
 9325 pts/4    SL+    1:02 mplayer /data/anime/Freedom/Animeforever/[AF-F_Y-F]_Freedom_-_06_[H264-AC3][1DEB7F7E]
 9538 ?        S      0:00 kdeinit4: kio_smtp [kd up
 9546 pts/3    R+     0:00 ps ax
 9753 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda1 /mnt -o rw,umask=000
 9758 pts/4    Ss     0:02 /bin/zsh
11058 ?        Ss     0:00 ssh-agent -s
```

---

### Post by spamzilla on 2008-07-26
> **taavikko said:**
> 
Zombies are lurking here also.
Maybe the "g-volume-manager" Is the reason why, Memorycards- and sticks are not mounting properly.

Always double-mounts, in nautilus listview"bookmarks"

Ah yes, my external hd and DVD's are double mounting

```

 ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:03 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:01 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   48 ?        00:00:01 kblockd/0
   49 ?        00:00:00 kblockd/1
   51 ?        00:00:00 kacpid
   52 ?        00:00:00 kacpi_notify
  132 ?        00:00:00 kseriod
  179 ?        00:00:07 kswapd0
  220 ?        00:00:00 aio/0
  221 ?        00:00:00 aio/1
  884 ?        00:00:00 aufsd
  885 ?        00:00:00 aufsd
  886 ?        00:00:00 aufsd
  887 ?        00:00:00 aufsd
  978 ?        00:00:00 cqueue
 1831 ?        00:00:00 ksuspend_usbd
 1832 ?        00:00:00 khubd
 1893 ?        00:00:01 ata/0
 1896 ?        00:00:01 ata/1
 1897 ?        00:00:00 ata_aux
 1959 ?        00:00:02 scsi_eh_0
 1960 ?        00:00:00 scsi_eh_1
 2021 ?        00:00:00 scsi_eh_2
 2022 ?        00:00:00 scsi_eh_3
 2150 ?        00:00:00 kjournald
 2309 ?        00:00:00 udevd
 3403 ?        00:00:00 kpsmoused
 3422 ?        00:00:00 btaddconn
 3423 ?        00:00:00 btdelconn
 3440 ?        00:00:05 iwl4965
 3486 ?        00:00:00 iwl4965/0
 3488 ?        00:00:00 iwl4965/1
 3938 ?        00:00:03 kjournald
 4319 tty4     00:00:00 getty
 4320 tty5     00:00:00 getty
 4325 tty2     00:00:00 getty
 4326 tty3     00:00:00 getty
 4327 tty6     00:00:00 getty
 4511 ?        00:00:00 acpid
 4574 ?        00:00:12 kondemand/0
 4575 ?        00:00:00 kondemand/1
 4641 ?        00:00:00 syslogd
 4690 ?        00:00:00 dd
 4692 ?        00:00:00 klogd
 4715 ?        00:00:28 dbus-daemon
 4737 ?        00:00:00 avahi-daemon
 4738 ?        00:00:00 avahi-daemon
 4785 ?        00:00:00 cupsd
 4841 ?        00:00:00 nmbd
 4842 ?        00:00:00 nmbd
 4844 ?        00:00:00 smbd
 4865 ?        00:00:00 winbindd
 4883 ?        00:00:00 smbd
 4884 ?        00:00:01 dhcdbd
 4892 ?        00:00:00 winbindd
 4908 ?        00:00:02 hald
 4911 ?        00:00:00 console-kit-dae
 4912 ?        00:00:00 hald-runner
 4994 ?        00:00:00 hald-addon-inpu
 4999 ?        00:00:00 hald-addon-cpuf
 5000 ?        00:00:00 hald-addon-acpi
 5027 ?        00:00:06 hald-addon-stor
 5063 ?        00:00:00 gdm
 5086 ?        00:00:00 system-tools-ba
 5107 ?        00:01:35 daemon.py
 5158 ?        00:00:00 atd
 5186 ?        00:00:00 cron
 5258 tty1     00:00:00 getty
 5282 ?        00:00:03 gconfd-2
 5404 ?        00:00:00 gvfs-fuse-daemo
 5580 ?        00:00:01 wpa_supplicant
16551 ?        00:00:23 firefox
20074 ?        00:00:01 pdflush
20113 ?        00:00:00 pdflush
21522 ?        00:00:05 python
21761 ?        00:04:03 mencoder
22195 ?        00:00:00 gdm
22224 tty7     00:04:52 Xorg
22244 ?        00:00:00 gnome-keyring-d
22255 ?        00:00:00 x-session-manag
22338 ?        00:00:00 dbus-daemon
22339 ?        00:00:00 dbus-launch
22343 ?        00:00:00 gnome-keyring-d
22345 ?        00:00:05 gnome-settings-
22346 ?        00:00:13 metacity
22349 ?        00:00:13 gnome-panel
22351 ?        00:00:00 gvfs-gphoto2-vo
22353 ?        00:00:00 gvfs-hal-volume
22355 ?        00:00:00 gvfsd
22361 ?        00:00:00 gvfs-fuse-daemo
22364 ?        00:00:00 pulseaudio
22368 ?        00:00:00 gconf-helper
22370 ?        00:00:12 nautilus
22372 ?        00:00:00 gnome-login-sou <defunct>
22374 ?        00:00:00 bonobo-activati
22380 ?        00:00:00 gvfsd-trash
22386 ?        00:00:11 tray.py
[B]22389 ?        00:00:00 jockey-gtk <defunct>
22390 ?        00:00:00 pactl <defunct>[/B]
[B]22391 ?        00:00:00 gnome-at-visual <defunct>
22393 ?        00:00:00 gnome-power-man <defunct>
22396 ?        00:00:00 xdg-user-dirs-g <defunct>
22400 ?        00:00:00 gnome-volume-ma <defunct[/B]>
22402 ?        00:00:00 update-notifier
22406 ?        00:00:00 gvfsd-burn
22411 ?        00:00:01 gnome-power-man
22415 ?        00:00:00 gnome-volume-ma
22423 ?        00:00:23 gnome-screensav
22434 ?        00:00:00 mixer_applet2
22545 ?        00:00:00 gnome-terminal
22548 ?        00:00:00 gnome-pty-helpe
22550 pts/0    00:00:00 bash
22551 ?        00:00:00 sh <defunct>
22578 pts/0    00:00:00 ps
25671 ?        00:00:04 pidgin

```

---

### Post by taavikko on 2008-07-26
> **HymnToLife said:**
> Blame Gnome, I guess...


You'r guess is as good as mine.
But, I'm an idiot, so I use gnome.

I updated week a go. from Hardy via 
"sudo do-release-uprgade --devel-release"
That may or may not be the reason, why zombies lurk around here.
After all, Alpha release.

---

### Post by Bachstelze on 2008-07-26
(As a side-node, [font="Courier New"]ps ax[/font] will show you the status of the processes, see my output.)

---

### Post by ronacc on 2008-07-26
I too have an invasion of zombies , see screenshot . and on the "double mount" when I insert a cd/dvd not only does it mount it twice I also get a warning that it can't mount it ????  see screenshot1 .

---

### Post by spamzilla on 2008-07-26
> **ronacc said:**
> I too have an invasion of zombies , see screenshot . and on the "double mount" when I insert a cd/dvd not only does it mount it twice I also get a warning that it can't mount it ????  see screenshot1 .

Yeah I get the same thing (just tested) and then the DVD / EXT HD will open up in 2 different windows. When I try to unmount, only one of the duplicate devices will unmount.

---

### Post by ronacc on 2008-07-26
file a bug report on th zombies and one on the double mount and I'll confirm .

---

### Post by spamzilla on 2008-07-26
> **ronacc said:**
> file a bug report on th zombies and one on the double mount and I'll confirm .

A bug report has already been filed on the zombie issue

[https://bugs.launchpad.net/ubuntu/+bug/250696](https://bugs.launchpad.net/ubuntu/+bug/250696)

double mounting bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/252120](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/252120)

I used your image of that mount error as I don't have anything at hand to reproduce that error - I hope you don't mind :)

---

### Post by ronacc on 2008-07-26
I don't mind at all I would have used it in my comfirmation if you hadn't included someting similar "a picture is worth a thousand words".

edit:   your  bug 252120 is now also marked as a dupe of #251991 added my confirmation to both originals .

---

### Post by echo6 on 2008-07-27
I have it here also, guess we will have to wait for an update to the volume-manager or whatever it is that's causing the problem.

---

### Post by Gina on 2008-07-27
Me too. AMD 64
 
And the double mount bug - I've added confirmation to both bug reports

---

### Post by ronacc on 2008-07-27
I've noticed another wrinkle to this , not only does it double mount cd/dvd's or usb sticks it WONT mount other local hard drives as user , if I "switch user" to root I can mount them ( and yes they double mount also) and switch back to normal user and access them ????

---

### Post by Gina on 2008-07-28
Still only in the first hour or so of testing Alpha 3 - I can't open partitions other than / in normal user mode in Nautilus.

---

### Post by ronacc on 2008-07-28
It looks like they have some permissions screwedup somewhere what with the double mount wont mount and gksudo sometimes trashing the system , they may all be part of the same oops. atleast the devs are looking at the double mount bug report , the original report of that is #251991 , they just asked for the output of lshal to be posted , I posted it but I had to increase the scrollback on bash to 4096 to get all of it , that seems rather verbose .

---

### Post by ace214 on 2008-07-28
> **ronacc said:**
> I too have an invasion of zombies , see screenshot . and on the "double mount" when I insert a cd/dvd not only does it mount it twice I also get a warning that it can't mount it ????  see screenshot1 .

I'm getting the same errors. The dvds play fine though...

---

### Post by chrisccoulson on 2008-07-28
The zombie's are all being left by gnome-session:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/252702]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/252702")

---

