---
title: "Installation Problems"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by bobkars on 2007-04-06
I'm upgrading a machine from SuSE to Ubuntu 6.10 on an AMD 64.

I have tried several ways (alternate, desktop, etc) to get this installed but it keeps failing during the process.  The MD5SUM is correct on the CDl.  I've finally got a log dump of the problem and it seems to indicate a CD drive problem so I tried a different CD drive but I get the same problem.  Help.....


pertinent part of file:
Apr  6 19:13:05 in-target:   tangerine-icon-theme tango-icon-theme tango-icon-theme-common tcpdump telnet
Apr  6 19:13:05 in-target:   time tomboy totem totem-gstreamer totem-mozilla tsclient ttf-arabeyes
Apr  6 19:13:05 in-target:   ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
Apr  6 19:13:05 in-target:   ttf-bitstream-vera ttf-devanagari-fonts ttf-freefont ttf-gentium
Apr  6 19:13:05 in-target:   ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
Apr  6 19:13:05 in-target:   ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-opensymbol
Apr  6 19:13:05 in-target:   ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts
Apr  6 19:13:05 in-target:   ttf-thai-tlwg ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds
Apr  6 19:13:05 in-target:   ubuntu-standard unattended-upgrades unzip update-manager update-notifier
Apr  6 19:13:05 in-target:   usplash usplash-theme-ubuntu vbetool vino vnc-common w3m wget whois wvdial
Apr  6 19:13:05 in-target:   x-ttcidfont-conf xbitmaps xcursor-themes xfonts-100dpi xfonts-75dpi
Apr  6 19:13:05 in-target:   xfonts-base xfonts-scalable xkeyboard-config xml-core xorg xsane
Apr  6 19:13:05 in-target:   xsane-common xscreensaver-data xscreensaver-gl xsltproc xterm xvncviewer
Apr  6 19:13:05 in-target:   yelp zenity zip
Apr  6 19:14:00 kernel: [  753.911971] warning: many lost ticks.
Apr  6 19:14:00 kernel: [  753.911974] Your time source seems to be instable or some driver is hogging interupts
Apr  6 19:14:00 kernel: [  753.911984] rip _spin_unlock_irqrestore+0x8/0x10
Apr  6 19:15:17 kernel: [  830.914358] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr  6 19:15:17 kernel: [  830.914366] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Apr  6 19:15:17 kernel: [  830.914369] ide: failed opcode was: unknown
Apr  6 19:15:18 kernel: [  831.961058] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr  6 19:15:18 kernel: [  831.961065] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Apr  6 19:15:18 kernel: [  831.961067] ide: failed opcode was: unknown
Apr  6 19:15:18 kernel: [  831.961071] end_request: I/O error, dev hdb, sector 177708
Apr  6 19:15:18 kernel: [  831.961075] Buffer I/O error on device hdb, logical block 44427
Apr  6 19:15:19 kernel: [  832.807268] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr  6 19:15:19 kernel: [  832.807274] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Apr  6 19:15:19 kernel: [  832.807277] ide: failed opcode was: unknown
Apr  6 19:15:19 kernel: [  832.807280] end_request: I/O error, dev hdb, sector 177712
Apr  6 19:15:19 kernel: [  832.807285] Buffer I/O error on device hdb, logical block 44428
Apr  6 19:15:20 kernel: [  833.935968] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr  6 19:15:20 kernel: [  833.935974] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Apr  6 19:15:20 kernel: [  833.935977] ide: failed opcode was: unknown
Apr  6 19:15:20 kernel: [  833.935980] end_request: I/O error, dev hdb, sector 177708
Apr  6 19:15:20 kernel: [  833.935985] Buffer I/O error on device hdb, logical block 44427
Apr  6 19:19:23 in-target: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/pool/main/e/ekiga/ekiga_2.0.3-0ubuntu3_amd64.deb  MD5Sum mismatch
Apr  6 19:19:23 in-target: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Apr  6 19:19:23 in-target: 0 upgraded, 655 newly installed, 0 to remove and 0 not upgraded.
Apr  6 19:19:23 in-target: Need to get 0B/449MB of archives.
Apr  6 19:19:23 in-target: After unpacking 1625MB of additional disk space will be used.
Apr  6 19:19:23 in-target: tasksel: aptitude failed (100)
Apr  6 19:19:23 main-menu[3052]: WARNING **: Configuring 'pkgsel' failed with error code 1 
Apr  6 19:19:23 main-menu[3052]: WARNING **: Menu item 'pkgsel' failed. 
Apr  6 19:20:10 main-menu[3052]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Apr  6 19:20:10 debconf: Setting debconf/priority to medium
Apr  6 19:20:11 main-menu[3052]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Apr  6 19:20:11 main-menu[3052]: INFO: Falling back to the package description for console-setup-udeb 
Apr  6 19:20:23 main-menu[3052]: INFO: Falling back to the package description for console-setup-udeb 
Apr  6 19:20:23 main-menu[3052]: INFO: Menu item 'save-logs' selected

---

### Post by bobkars on 2007-04-06
Forgot to mention one other thing.  I did have it operating once but I reinstalled it right after that because I wanted to set up the partitions differently  However, i can't even get it to work with the default partitions now.

---

