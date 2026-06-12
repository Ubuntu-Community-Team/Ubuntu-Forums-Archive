---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by poignantprick on 2012-04-19
This is it. I have done my best to be as self-reliant as possible. Almost two months ago I encountered massive difficulties, and I have tried various distros, and ran into problems with each one. I am a total _novice_. I'm going to skip the sob story. Maybe I will start a blog, and cry about it on there. Right now all I want is a stable OS. Most of the time everything goes well until I update the fresh install.

So I have a fresh install of 11.10. I ran the update manager. That didn't work. So I did what I always do, and followed some breadcrumbs around forums. I tried several things that looked like similar issues, but nothing worked. I ran updates and upgrade in terminal, and here is what I am getting.

brambo@brambo-Aspire-5552G:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Reading package lists... Done
brambo@brambo-Aspire-5552G:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic software-center
The following packages will be upgraded:
  accountsservice acpid aisleriot alsa-utils app-install-data-partner
  appmenu-qt apport apport-gtk apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data apturl apturl-common at-spi2-core bamfdaemon banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab
  bind9-host binutils bluez bluez-alsa bluez-cups bluez-gstreamer brasero
  brasero-cdrkit brasero-common brltty bzip2 checkbox checkbox-gtk colord
  command-not-found command-not-found-data compiz compiz-core compiz-gnome
  compiz-plugins-default compiz-plugins-main-default cups cups-bsd cups-client
  cups-common cups-ppdc deja-dup desktop-file-utils dnsutils empathy
  empathy-common eog evince evince-common evolution-data-server
  evolution-data-server-common file-roller firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en gbrainy gcalctool gconf2
  gconf2-common gedit gedit-common ghostscript ghostscript-cups ghostscript-x
  gir1.2-atspi-2.0 gir1.2-gconf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-totem-1.0 gir1.2-unity-4.0 gir1.2-webkit-3.0
  gnome-accessibility-themes gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-desktop3-data gnome-font-viewer
  gnome-games-common gnome-icon-theme gnome-keyring gnome-mahjongg
  gnome-online-accounts gnome-orca gnome-power-manager gnome-screenshot
  gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log
  gnome-system-monitor gnome-utils-common gnomine gstreamer0.10-gconf
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  gzip hpijs hplip hplip-cups hplip-data ifupdown indicator-datetime
  indicator-session indicator-sound initramfs-tools initramfs-tools-bin
  initscripts isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base language-selector-common language-selector-gnome
  libaccountsservice0 libapt-inst1.3 libapt-pkg4.11 libarchive1
  libasound2-plugins libatk-adaptor libatspi2.0-0 libbamf0 libbamf3-0
  libbind9-60 libbluetooth3 libbrasero-media3-1 libbrlapi0.5 libbz2-1.0
  libc-bin libc-dev-bin libc6 libc6-dev libcamel-1.2-29 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module
  libcanberra-pulse libcanberra0 libcolord1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3-gnutls
  libdecoration0 libdns69 libebackend-1.2-1 libebook1.2-12 libecal1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver1.2-15
  libedataserverui-3.0-1 libevince3-3 libfreetype6 libgail-3-0
  libgail-3-common libgck-1-0 libgconf2-4 libgcr-3-1 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglu1-mesa libgnome-bluetooth8
  libgnome-control-center1 libgnome-desktop-3-2 libgnutls26 libgoa-1.0-0
  libgrip0 libgs9 libgs9-common libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libgudev-1.0-0 libgweather-3-0 libgweather-common libgwibber-gtk2
  libgwibber2 libhpmud0 libicu44 libimobiledevice2 libisc62 libisccc60
  libisccfg62 libjasper1 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2
  liblightdm-gobject-1-0 liblwres60 libmetacity-private0
  libmono-zeroconf1.0-cil libmysqlclient16 libnautilus-extension1
  libnm-glib-vpn1 libnm-glib4 libnm-util2 libnotify0.4-cil libnux-1.0-0
  libnux-1.0-common libpam-gnome-keyring libpam-modules libpam-modules-bin
  libpam-runtime libpam0g libpng12-0 libpulse-mainloop-glib0 libpulse0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer libsane-hpaio
  libsmbclient libssl1.0.0 libsyncdaemon-1.0-1 libt1-5 libtiff4 libtotem0
  libubuntuone-1.0-1 libubuntuone1.0-cil libudev0 libunity-2d-private0
  libunity-core-4.0-4 libunity6 libusbmuxd1 libv4l-0 libvorbis0a libvorbisenc2
  libvorbisfile3 libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxml2 lightdm linux-libc-dev
  metacity metacity-common mobile-broadband-provider-info modemmanager
  mousetweaks multiarch-support mysql-common nautilus nautilus-data
  nautilus-sendto-empathy network-manager nux-tools onboard openssl pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils python-apport python-aptdaemon
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-brlapi python-cups python-cupshelpers
  python-gobject python-gobject-cairo python-httplib2 python-launchpadlib
  python-libxml2 python-pam python-papyon python-pkg-resources
  python-problem-report python-pyatspi2 python-software-properties
  python-ubuntuone-client python-uno qdbus samba-common samba-common-bin
  seahorse shotwell simple-scan smbclient sni-qt software-properties-common
  software-properties-gtk system-config-printer-common
  system-config-printer-gnome system-config-printer-udev sysv-rc
  sysvinit-utils telepathy-indicator thunderbird thunderbird-globalmenu
  thunderbird-gnome-support tomboy totem totem-common totem-mozilla
  totem-plugins ttf-opensymbol tzdata ubuntu-docs ubuntuone-client
  ubuntuone-client-gnome ubuntuone-couch udev unity unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread unity-common
  unity-lens-applications unity-services uno-libs3 update-manager
  update-manager-core update-notifier update-notifier-common upstart ure
  usbmuxd vinagre vino x11-common xorg xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-openchrome xul-ext-ubufox
389 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/278 MB of archives.
After this operation, 12.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libutouch-grail1': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


I'm running on an aspire 5552G-7641
AMD Phenom 2 X4 N970
AMD Radeon HD 6650M
4 GB DDR3 Mem

I really am very new to computers. Any directions have to be pretty specific.

Thanks in advance to anyone that can help me not throw this laptop against the wall.

---

### Post by zvacet on 2012-04-21
```
sudo apt-get --reinstall install libutouch-grail1
```

---

### Post by poignantprick on 2012-04-21
Well, I did that, and it froze before it did anything.

I hit Alt+Ctrl+F2 and started getting a read out that I had seen before. I found this link:
[http://ubuntuforums.org/showthread.php?t=1942369&highlight=hard+drive+failed+command+read+fpdma](http://ubuntuforums.org/showthread.php?t=1942369&highlight=hard+drive+failed+command+read+fpdma)
The user posted pictures that are the same basic, if not exact, errors.

I followed some directions I found on there for SMART tools.

Here is the read out. I am worried I have a bad hard drive. Can you make heads or tails out of it?

Also, I don't know how to make one of those scrolling window for the readout. Sorry about the long post...


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  645) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 158) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   083   083   062    Pre-fail  Always       -       14221548
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   158   158   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       2255
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       1982
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1838
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       200
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       10518
194 Temperature_Celsius     0x0002   161   161   000    Old_age   Always       -       34 (Min/Max 11/43)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       166
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       51
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 354 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 354 occurred at disk power-on lifetime: 1952 hours (81 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 25 b1 8a e0  Error: UNC 3 sectors at LBA = 0x008ab125 = 9089317

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 40 08 20 b1 8a e0 00      00:00:17.400  READ DMA EXT
  25 40 08 18 b1 8a e0 00      00:00:17.400  READ DMA EXT
  25 40 08 10 b1 8a e0 00      00:00:17.400  READ DMA EXT
  25 40 03 0d b1 8a e0 00      00:00:17.400  READ DMA EXT
  25 40 05 08 b1 8a e0 00      00:00:17.400  READ DMA EXT

Error 353 occurred at disk power-on lifetime: 1951 hours (81 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 25 b1 8a e0  Error: UNC 3 sectors at LBA = 0x008ab125 = 9089317

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 40 08 20 b1 8a e0 00      00:00:25.000  READ DMA EXT
  25 40 08 18 b1 8a e0 00      00:00:25.000  READ DMA EXT
  25 40 08 10 b1 8a e0 00      00:00:25.000  READ DMA EXT
  25 40 03 0d b1 8a e0 00      00:00:25.000  READ DMA EXT
  25 40 05 08 b1 8a e0 00      00:00:25.000  READ DMA EXT

Error 352 occurred at disk power-on lifetime: 1951 hours (81 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 64 95 8a e0  Error: UNC 4 sectors at LBA = 0x008a9564 = 9082212

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 40 08 60 95 8a e0 00      00:00:09.800  READ DMA EXT
  25 40 08 58 95 8a e0 00      00:00:09.800  READ DMA EXT
  25 40 08 50 95 8a e0 00      00:00:09.800  READ DMA EXT
  25 40 08 48 95 8a e0 00      00:00:09.800  READ DMA EXT
  25 40 08 40 95 8a e0 00      00:00:09.800  READ DMA EXT

Error 351 occurred at disk power-on lifetime: 1877 hours (78 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 b2 48 24 e0  Error: UNC 6 sectors at LBA = 0x002448b2 = 2377906

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 03 08 b0 48 24 e0 00      00:29:46.300  READ DMA
  ef 03 45 94 47 24 e0 00      00:29:46.300  SET FEATURES [Set transfer mode]
  c6 03 10 94 47 24 e0 00      00:29:46.300  SET MULTIPLE MODE
  10 03 01 94 47 24 e0 00      00:29:46.300  RECALIBRATE [OBS-4]
  91 03 3f 94 47 24 af 00      00:29:46.300  INITIALIZE DEVICE PARAMETERS [OBS-6]

Error 350 occurred at disk power-on lifetime: 1877 hours (78 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 b2 48 24 e0  Error: UNC 6 sectors at LBA = 0x002448b2 = 2377906

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 03 08 b0 48 24 e0 00      00:29:42.400  READ DMA
  ef 03 45 94 47 24 e0 00      00:29:42.400  SET FEATURES [Set transfer mode]
  c6 03 10 94 47 24 e0 00      00:29:42.400  SET MULTIPLE MODE
  10 03 01 94 47 24 e0 00      00:29:42.400  RECALIBRATE [OBS-4]
  91 03 3f 94 47 24 af 00      00:29:42.400  INITIALIZE DEVICE PARAMETERS [OBS-6]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1982         4801
# 2  Short offline       Completed without error       00%        26         -
# 3  Short offline       Completed without error       00%        26         -
# 4  Short offline       Completed without error       00%        25         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

