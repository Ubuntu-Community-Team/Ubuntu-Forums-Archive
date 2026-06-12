---
title: "difficulty trying to install NVIDIA driver on lucid"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Thystra on 2010-04-03
Hi,

I have a HP HDX 16 laptop with the 

```
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
```controller.  There is no hardware driver available for it under the restricted driver, as of yet.  

I followed the instructions here:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

to try and install the driver from Nvidia:

Version: 195.36.15 Certified
Release Date: 2010.03.19
Operating System: Linux 64-bit
Language: English (U.S.)
File Size: 40.0 MB 
NVIDIA-Linux-x86_64-195.36.15-pkg2.run

I followed the instructions in the guide, and all was well until editing the xorg.conf - as I seemed to be missing a lot of things that were indicated on the guide:

```
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

```I then tried to build/install the driver:

the last bit of the log:

```
  ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-19-generic/scripts/mo
   dule-common.lds --build-id -o /tmp/selfgz16322/NVIDIA-Linux-x86_64-195.36.15
   -pkg2/usr/src/nv/nvidia.ko /tmp/selfgz16322/NVIDIA-Linux-x86_64-195.36.15-pk
   g2/usr/src/nv/nvidia.o /tmp/selfgz16322/NVIDIA-Linux-x86_64-195.36
   .15-pkg2/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [53788.329236] __ratelimit: 36 callbacks suppressed
   [53788.329240] telepathy-haze[2060]: segfault at 108 ip 00007ffa5d852db7 sp
   00007fff1b3f7ae0 error 4 in libymsg.so.0.0.0[7ffa5d842000+34000]
   [53790.822206] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [53794.380072]  CIFS VFS: Error connecting to socket. Aborting operation
   [53794.380106]  CIFS VFS: cifs_mount failed w/return code = -110
   [53794.380476]  CIFS VFS: Error connecting to socket. Aborting operation
   [53794.380500]  CIFS VFS: cifs_mount failed w/return code = -110
   [53887.967728] nvidia: module license 'NVIDIA' taints kernel.
   [53887.967732] Disabling lock debugging due to kernel taint
   [53888.523578] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [53888.523586] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [53888.523589] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [53888.523592] NVRM: device(s).
   [53888.523598] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [53888.523601] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [53888.523603] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [53888.523609] NVRM: No NVIDIA graphics adapter probed!
   [54034.812960] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [54034.812968] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [54034.812971] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [54034.812974] NVRM: device(s).
   [54034.812980] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [54034.812983] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [54034.812985] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [54034.812991] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```any advice would be appreciated.  This is on lucid with kernel - 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux

Thanks.

---

### Post by Canezila on 2010-04-03
Hello Thystra,

I am having the same problems.  I am running Mythbuntu 10.4 but am also having problems with the nvidia.ko.... 

Brian



FOUND THE FIX:
**** Sorry that my copy and paste is messed up!****

Start with removing and purging nouveau* and then you you can install nvidia's driver without any problem errors or etc... 
Quote:
Code:

Code:
sudo apt-get purge nouveau*



> **myromance123 said:**
> *I used Ubuntu 10.04 Beta 1 with a 9400GT Nvidia Graphics Card, a GREAT BIG THANKS to Regenweald for giving me the solution :)

I had the problem of being unable to use the drivers from Administration>Hardware Drivers because after restarting, it would give me the same problems as did installing Nvidia's drivers from their site, which are the options of Exit to Console & Run Ubuntu in Low Graphics Mode etc...

After doing this,



I attempted to reinstall the driver from Nvidia's site (195.36.15) without restarting and it wouldn't register that the X server was not running even after doing several ```
sudo gdm service stop
```. So I forced shutdown.

Power on, came to the options of Exit To Console etc and chose Exit To Console and reattempted to install 195.36.15. This time no complaints about X server, installation started and the error 'The distribution-provided pre-install script failed! Continue installation anyway? ' came out as usual. Still continued on with the installation.

 After the installation completed, I did ```
sudo service gdm start
``` and it works!

Restarted the computer to see if it would stick, it still works :D
PS: Just thought I should write down what I went through incase there are others who experience this :)

---

### Post by Thystra on 2010-04-03
I was looking at it some more, it appears that 10.04 has the noveau driver installed by default.

 [53790.822206] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2

I tried to uninstall the package, but that just resulted in a corrupted display when I tried to exit X and go to the terminal to install the nvidia driver.  

I suspect that we will need to remove the noveau driver and then set up the nvidia driver.

---

### Post by Thystra on 2010-04-03
I'm not sure that is a good command - when I run it, it wants to remove a whole lot of things, including a couple 'essential' packages.  Did this happen to you? There has to be a better way

```

Note, selecting libdrm-nouveau1 for regex 'nouveau*'
Note, selecting nouveau-firmware for regex 'nouveau*'
Note, selecting libdrm-nouveau1-dbg for regex 'nouveau*'
Note, selecting xserver-xorg-video-nouveau for regex 'nouveau*'
The following packages were automatically installed and are no longer required:
  python-bugbuddy menu libgnome-bluetooth7 libsilcclient-1.1-3 libgmime-2.4-2
  telepathy-gabble python-evince python-mako python-avahi python-configglue
  python-ubuntuone-client ubuntuone-client intel-gpu-tools libnunit2.4-cil
  libotf0 libprotobuf5 python-pycurl gir1.0-clutter-gtk-0.10 obexd-client
  python-couchdb python-pygoocanvas python-louis liblouis-data
  liblaunchpad-integration1.0-cil empathy-common python-egenix-mxtools
  libsctp1 libestools1.2 libgupnp-1.0-3 libglademm-2.4-1c2a
  python-ubuntuone-storageprotocol libgoocanvas3 libindicate-gtk2
  python-indicate lksctp-tools python-totem-plparser libiso9660-7
  wireshark-common python-gnomekeyring libdotconf1.0 python-pyinotify
  xorg-docs-core libdvbpsi5 libmono-system-runtime2.0-cil festlex-cmu
  python-protobuf gstreamer0.10-gnonlin libx264-85 libvlc2 libgdu-gtk0
  libgdata-common libclutter-gtk-0.10-0 vlc-nox festvox-kallpc16k libqtcore4
  libgoocanvas-common liblouis0 libsmi2ldbl libnm-glib2 libmatroska0
  modemmanager libevent-1.4-2 python-telepathy libart2.0-cil python-rsvg
  libspeechd2 ubuntu-mono python-appindicator libflickrnet2.2-cil
  python-gtkspell libtotem-plparser17 libcap-ng0 libgupnp-igd-1.0-2 wireshark
  libc-ares2 libupower-glib1 liblua5.1-0 libanthy0 festival protobuf-compiler
  python-pexpect vlc-data libzephyr4 festlex-poslex libtar python-gnomeprint
  libnice0 gstreamer0.10-nice libloudmouth1-0 python-egenix-mxdatetime
  python-ibus libvlccore2 libvcdinfo0 libebml0 libgmime2.4-cil libprotoc5
  bcmwl-modaliases keyutils adium-theme-ubuntu libgssdp-1.0-2
  telepathy-mission-control-5 python-gtop
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support* acpid* aisleriot* alsa-base* alsa-utils* anacron* apparmor*
  apparmor-utils* apport* apport-gtk* aptdaemon* apturl* at* at-spi*
  avahi-daemon* avahi-utils* bluetooth* bluez* bluez-cups* bluez-utils*
  brasero* brasero-common* brltty* brltty-x11* camorama* capplets-data*
  checkbox* checkbox-gtk* cheese* cheese-common* compiz-core* compiz-plugins*
  computer-janitor-gtk* console-setup* consolekit* couchdb-bin* cron* cups*
  cups-driver-gutenprint* dbus* dbus-x11* desktopcouch* dmsetup* e2fsprogs*
  ekiga* empathy* eog* epiphany-browser* epiphany-browser-data* erlang-base*
  erlang-crypto* erlang-inets* erlang-mnesia* erlang-public-key*
  erlang-runtime-tools* erlang-ssl* erlang-syntax-tools* erlang-xmerl* evince*
  evolution* evolution-couchdb* evolution-data-server* evolution-exchange*
  evolution-indicator* evolution-plugins* evolution-webcal* f-spot*
  file-roller* firefox* firefox-3.0* firefox-3.0-gnome-support*
  firefox-branding* firefox-gnome-support* foo2zjs* foomatic-db*
  foomatic-db-engine* fprint-demo* friendly-recovery* ftp* gbrainy* gcalctool*
  gconf-defaults-service* gconf-editor* gconf2* gconf2-common* gdebi* gdm*
  gdm-guest-session* gedit* ghostscript-cups* ghostscript-x* gimp*
  gir1.0-gconf-2.0* gksu* glchess* glines* gnect* gnibbles* gnobots2*
  gnome-about* gnome-applets* gnome-applets-data* gnome-bluetooth*
  gnome-codec-install* gnome-control-center* gnome-disk-utility* gnome-games*
  gnome-games-common* gnome-keyring* gnome-mag* gnome-mahjongg* gnome-media*
  gnome-media-common* gnome-nettool* gnome-orca* gnome-panel*
  gnome-panel-data* gnome-pilot* gnome-pilot-conduits* gnome-power-manager*
  gnome-screensaver* gnome-session* gnome-session-bin* gnome-session-canberra*
  gnome-settings-daemon* gnome-sudoku* gnome-system-monitor*
  gnome-system-tools* gnome-terminal* gnome-terminal-data* gnome-user-guide*
  gnome-user-guide-en* gnome-user-share* gnome-utils* gnomine* gnotravex*
  gnotski* google-chrome-beta* gpsd* gpsdrive-scripts* gstreamer0.10-gnomevfs*
  gstreamer0.10-plugins-good* gstreamer0.10-pulseaudio* gtali* gucharmap*
  gvfs* gvfs-backends* gvfs-bin* gvfs-fuse* gwibber* gwibber-service* hal*
  hostname* hotkey-setup* hplip* hplip-cups* ia32-crossover-games-demo*
  ia32-crossover-pro* iagno* ibus* ibus-m17n* ibus-table* ifupdown*
  imagemagick* indicator-applet* indicator-applet-session* indicator-me*
  indicator-session* indicator-sound* initramfs-tools* initscripts*
  irqbalance* jockey-common* jockey-gtk* kbd* kismet* language-selector*
  language-support-translations-en* lftp* lib32nss-mdns* libasound2-plugins*
  libatspi1.0-0* libaudio2* libbonoboui2-0* libbrasero-media0* libcamel1.2-14*
  libcanberra-pulse* libcheese-gtk18* libcouchdb-glib-1.0-2* libcryptui0*
  libdesktopcouch-glib-1.0-2* libdrm-nouveau1* libebackend1.2-0*
  libebook1.2-9* libecal1.2-7* libedata-book1.2-2* libedata-cal1.2-6*
  libedataserver1.2-11* libedataserverui1.2-8* libegroupwise1.2-13*
  libexchange-storage1.2-3* libfprint0* libgail-gnome-module* libgconf2-4*
  libgconf2.0-cil* libgconfmm-2.6-1c2* libgdata6* libgdu0* libgegl-0.0-0*
  libgksu2-0* libglew1.5* libgnome-desktop-2-17* libgnome-media0*
  libgnome-pilot2* libgnome-speech7* libgnome-vfs2.0-cil*
  libgnome-window-settings1* libgnome2-0* libgnome2-common* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.24-cil* libgnomekbd-common* libgnomekbd4*
  libgnomepanel2.24-cil* libgnomeui-0* libgnomevfs2-0* libgnomevfs2-bin*
  libgnomevfs2-common* libgnomevfs2-extra* libgstfarsight0.10-0*
  libgtkhtml-editor0* libgtkhtml3.14-19* libgweather-common* libgweather1*
  libice6* libio-socket-ssl-perl* liblpint-bonobo0* libm17n-0* libmagickcore2*
  libmagickcore2-extra* libmagickwand2* libmetacity-private0*
  libnet-dbus-perl* libnss-mdns* liboobs-1-4* libopal3.6.6*
  libpanel-applet2-0* libpolkit-gtk-1-0* libpt2.6.5* libpt2.6.5-plugins*
  libpulse-browse0* libpulse-mainloop-glib0* libpulse0* libpurple0* libqtgui4*
  librpc-xml-perl* libsdl-image1.2* libsdl1.2debian*
  libsdl1.2debian-pulseaudio* libseed0* libsm6* libsoup-gnome2.4-1*
  libstartup-notification0* libtelepathy-farsight0* libubuntuone-1.0-1*
  libwebkit-1.0-2* libwnck22* libwww-mechanize-perl* libwww-perl* libxaw7*
  libxklavier16* libxml-parser-perl* libxml-sax-expat-perl* libxml-twig-perl*
  libxml-xpath-perl* libxmu6* libxres1* libxss1* libxt6* libxtst6* libxvmc1*
  libxxf86dga1* light-themes* lightsoff* linux-generic*
  linux-image-2.6.32-19-generic* linux-image-generic* linux-sound-base*
  logrotate* m17n-contrib* m17n-db* mangler* media-player-info* metacity*
  metacity-common* module-init-tools* mountall* mousetweaks* nautilus*
  nautilus-data* nautilus-sendto* nautilus-sendto-empathy* nautilus-share*
  netbase* network-manager* network-manager-gnome* network-manager-pptp*
  network-manager-pptp-gnome* notify-osd* ntfs-3g* ntp* ntpdate*
  obex-data-server* onboard* openoffice.org-base-core* openoffice.org-calc*
  openoffice.org-core* openoffice.org-draw* openoffice.org-emailmerge*
  openoffice.org-gnome* openoffice.org-gtk* openoffice.org-help-en-gb*
  openoffice.org-help-en-us* openoffice.org-impress* openoffice.org-math*
  openoffice.org-writer* openprinting-ppds* padevchooser* paman* paprefs*
  pavucontrol* pavumeter* pcmciautils* perlmagick* pidgin* pidgin-libnotify*
  pidgin-otr* pitivi* plymouth* plymouth-label* plymouth-theme-fade-in*
  plymouth-theme-ubuntu-logo* plymouth-theme-ubuntu-text* plymouth-x11*
  pm-utils* pm-utils-powersave-policy* policykit* policykit-1*
  policykit-1-gnome* powermgmt-base* ppp* pppconfig* pppoeconf* pptp-linux*
  procps* pulseaudio* pulseaudio-esound-compat* pulseaudio-module-bluetooth*
  pulseaudio-module-gconf* pulseaudio-module-x11* pulseaudio-module-zeroconf*
  pulseaudio-utils* pxljr* python-aptdaemon* python-aptdaemon-gtk*
  python-desktopcouch* python-desktopcouch-records* python-evolution*
  python-farsight* python-gconf* python-gnome2* python-gnome2-desktop*
  python-gnomeapplet* python-gnomedesktop* python-mediaprofiles*
  python-metacity* python-papyon* python-pyatspi* python-speechd*
  python-ubuntuone* python-uno* python-virtkey* python-webkit* python-wnck*
  quadrapassel* rhythmbox* rhythmbox-plugin-cdrecorder* rhythmbox-plugins*
  rhythmbox-ubuntuone-music-store* rss-glx* rsyslog* samba*
  screen-resolution-extra* screensaver-default-images* seahorse*
  seahorse-plugins* seed* simple-scan* smbfs* software-center*
  software-properties-gtk* speech-dispatcher* splix* sreadahead*
  startupmanager* swell-foop* system-config-printer-common*
  system-config-printer-gnome* system-tools-backends* tangogps*
  telepathy-butterfly* telepathy-haze* telepathy-salut* telnet* thunderbird*
  thunderbird-locale-en-gb* tomboy* totem* totem-common* totem-gstreamer*
  totem-mozilla* totem-plugins* transmission-gtk* tsclient* turboprint*
  ubufox* ubuntu-artwork* ubuntu-desktop* ubuntu-docs* ubuntu-minimal*
  ubuntu-standard* ubuntu-system-service* ubuntu-wallpapers*
  ubuntuone-client-gnome* udev* udisks* ufw* update-manager* update-notifier*
  upower* upstart* ureadahead* usb-creator-common* usb-creator-gtk*
  util-linux* vinagre* vino* vlc* vlc-plugin-pulse* wireless-crda*
  x-ttcidfont-conf* x11-apps* x11-common* x11-session-utils* x11-utils*
  x11-xfs-utils* x11-xkb-utils* x11-xserver-utils* xfonts-100dpi*
  xfonts-75dpi* xfonts-base* xfonts-encodings* xfonts-mathml* xfonts-scalable*
  xfonts-utils* xinit* xorg* xscreensaver-data* xscreensaver-gl*
  xserver-common* xserver-xorg* xserver-xorg-core* xserver-xorg-input-all*
  xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse*
  xserver-xorg-input-wacom* xserver-xorg-video-all* xserver-xorg-video-apm*
  xserver-xorg-video-ark* xserver-xorg-video-ati* xserver-xorg-video-chips*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev*
  xserver-xorg-video-i128* xserver-xorg-video-intel*
  xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-neomagic* xserver-xorg-video-nouveau*
  xserver-xorg-video-nv* xserver-xorg-video-openchrome*
  xserver-xorg-video-r128* xserver-xorg-video-radeon*
  xserver-xorg-video-rendition* xserver-xorg-video-s3*
  xserver-xorg-video-s3virge* xserver-xorg-video-savage*
  xserver-xorg-video-siliconmotion* xserver-xorg-video-sis*
  xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-tseng*
  xserver-xorg-video-v4l* xserver-xorg-video-vesa* xserver-xorg-video-vmware*
  xserver-xorg-video-voodoo* xterm* xulrunner-1.9*
  xulrunner-1.9-gnome-support* xulrunner-1.9.2* yelp*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 515 to remove and 0 not upgraded.
After this operation, 1,964MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

```

---

### Post by dino99 on 2010-04-03
hello guys,

i dont know about that card but keep in mind that you might follow Lucid guide rather than nvidia guide. your xorg.conf can introduce trouble so erase it then use: system -- admin -- hardware driver to see if 195.36 is activated or not ( nvidia-current & nvidia-settings & nvidia-common & nvidia-current-modaliases have to be installed)

---

### Post by Thystra on 2010-04-03
Thanks dino, that did the trick!  for some reason I guess they weren't installed by default.

---

### Post by tatsuno on 2010-04-08
Thanks dino99!!

I was also struggling with nvidia problems in Lucid - every now and then the system was giving error loading kernel module and booting in low res. I noticed that the driver was not properly activated in hardware drivers, and this did the trick!

Thanks again.

---

### Post by tatsuno on 2010-04-08
Hi dino99,

Too bad, after several boots, today I got the same error again, and back to low resolution :(

Fortunately, whenever I reboot I get my nice native resolution again, but this is so weird. I checked hardware drivers and the nvidia-current is active, both when I am in low res and high res.

Could you please help me?

Thank you.

---

### Post by thatsPipe on 2010-04-09
Either it is my machine or the packages are not all properly compiled in Lucid but I've been getting version mismatch errors between libGL.so and libGLcore.so ever since I upgraded(One says its 195.36.15 and the other 195.36.08 ) I can remove the symbolic links and create new ones to the proper versions and things will work until I update, at which point the symbolic links are reset and I have to once again manual set them to the correct files.


I have no idea where the 195.36.08 version is coming or what is setting the symbolic link /usr/lib/libGL.so.1 to point to the 195.36.08 version instead of the 195.36.15 version. Anyone else running into this problem?

---

### Post by sdowney717 on 2010-04-09
I had to blacklist the nouveau driver in blacklist.conf
otherwise it cause a proplem as it tries to load with the nvidia driver.

Also, you can just boot to console terminal, at the menu skipping x gnome GDM entirely
install the nvidia driver in console window
sudo ./nvidiafile.run
follow onscreen prompts, let it adjust the xorg automatically
then 
sudo reboot

yes, you get symbolic errors but it works anyway

---

### Post by dino99 on 2010-04-09
hello bugs hunters  #-o

you have to know that Lucid like all Ubuntu is made for human beings, so repo brings you all you need.

If you are experienced enough you can install from sources (third party) and tweak as you like, but be ready to help yourself with issues.

If you are lazy like myself and clever a little bit, only use your distro repo (without exotic packages from custom ppa or third party, of course dont mix distro into the same sources.list: ie karmic+lucid or lucid+sid or else).

So, first make some room if needed, Ubuntu will thanks you  [-o<

use the magic commands:

sudo apt-get clean / autoclean /autoremove
sudo apt-get install -f

you can remove the broken/outdated links by installing/running gconf-cleaner

):P

---

