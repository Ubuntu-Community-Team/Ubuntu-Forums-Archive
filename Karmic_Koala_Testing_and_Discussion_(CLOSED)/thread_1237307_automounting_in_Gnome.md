---
title: "automounting in Gnome"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skeve on 2009-08-11
Somehow automounting of CD/DVD disks and USB storage devices doesn't work anymore in Gnome, while KDE environment mounts those devices without any problems. So when I plug in some USB-flash in Gnome I need to use Dolphin to mount it automatically.
What could be the cause of this problem?

---

### Post by miegiel on 2009-08-11
> **skeve said:**
> Somehow automounting of CD/DVD disks and USB storage devices doesn't work anymore in Gnome, while KDE environment mounts those devices without any problems. So when I plug in some USB-flash in Gnome I need to use Dolphin to mount it automatically.
What could be the cause of this problem?

Did you check the auto mount settings in ```
gconf-editor
```

---

### Post by skeve on 2009-08-11
which options do you mean?
I checked /apps/nautilus/preferences - media_automount and media_automount_open options are on

upd.
/desktop/gnome/volume_manager/automount_drives on
/desktop/gnome/volume_manager/automount_media on

---

### Post by miegiel on 2009-08-12
> **skeve said:**
> which options do you mean?
I checked /apps/nautilus/preferences - media_automount and media_automount_open options are on

upd.
/desktop/gnome/volume_manager/automount_drives on
/desktop/gnome/volume_manager/automount_media on

Yeah, I think it was those. I'm not having any USB mounting problems here, that's why I thought it might be a wrong setting. The *ubuntu-desktop* package for karmic is being worked on atm (there was an update this morning for me), maybe that's causing your problems. Check if there are any bug reports. I [_read something_]("http://ubuntuforums.org/showthread.php?t=1211009&page=2") the other day of someone having problems with his acer timeline and monting CD/DVDs in jaunty, but that might not be related at all.

---

### Post by skeve on 2009-08-13
thanks for the info. this update didn't change the situation here :(
I'll look into the Acer's problem, but at the first glance these problems are not connected. maybe I'm wrong, though

---

### Post by wayne_cat on 2009-08-13
ok ... this will be fixed soon. The bug is now a papercut  ... from the bug report:

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448)

```
Changed in hundredpapercuts:
importance:     Undecided &#8594; High
milestone:      none &#8594; round-10
status:         New &#8594; Triaged
```and here it is:

[https://edge.launchpad.net/hundredpapercuts/+milestone/round-10](https://edge.launchpad.net/hundredpapercuts/+milestone/round-10)

---

### Post by skeve on 2009-08-14
Ok, thanks, that's good to know.
But my problem happens not only when starting a GNOME session, but none of the plugged-in devices mount anytime during the session. To mount any of these devices I have to start dolphin and only after that the device becomes visible and mountable

---

### Post by skeve on 2009-08-25
The problem still remains here. I checked PolicyKit and hal configuration, but couldn't find anything.
Please, help!

---

### Post by kansasnoob on 2009-08-25
No problem mounting external drives here with the installation of 'pmount'.

I first discovered that pkg either in Gutsy or Hardy, although I've read that hal may be getting "replaced" or something along those lines and pmount depends on hal so I'll have to cross that bridge when I get to it:)

---

### Post by skeve on 2009-08-26
nope, pmount didn't help either :(

---

### Post by taavikko on 2009-08-26
Does this happen on a new user aswell?
Add user "sudo adduser test" then login to that account and test.

---

### Post by taavikko on 2009-08-26
> **kansasnoob said:**
>  I've read that hal may be getting "replaced" or something along those lines and pmount depends on hal so I'll have to cross that bridge when I get to it:)

[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

---

### Post by ad_267 on 2009-08-26
Not a very helpful comment, but KDE doesn't actually automount drives at all. You have to open the drive with dolphin before it will mount. Very stupid behaviour I think.

See [https://bugs.kde.org/show_bug.cgi?id=164053](https://bugs.kde.org/show_bug.cgi?id=164053)

---

### Post by skeve on 2009-08-26
> **taavikko said:**
> Does this happen on a new user aswell?
Add user "sudo adduser test" then login to that account and test.
yes, it does. newly created user has the same problem

---

### Post by skeve on 2009-08-26
> **ad_267 said:**
> Not a very helpful comment, but KDE doesn't actually automount drives at all. You have to open the drive with dolphin before it will mount. Very stupid behaviour I think.

See [https://bugs.kde.org/show_bug.cgi?id=164053](https://bugs.kde.org/show_bug.cgi?id=164053)
I can agree with you here. But at least dolphin shows the device wich can be mounted, while nautilus doesn't do it at all. So when I'm using Gnome desktop I still need to run dolphin to discover and mount a device...

---

### Post by taavikko on 2009-08-26
> **skeve said:**
> yes, it does. newly created user has the same problem

start session via liveCD and test the function desired.
If it happens on there, it means that there's some confusion with libs.

---

### Post by skeve on 2009-08-26
> **taavikko said:**
> start session via liveCD and test the function desired.
If it happens on there, it means that there's some confusion with libs.

ok, I'm gonna need to download one :)
it's really hard to pinpoint the moment when this mounting thing went wrong, because I've been using ubuntu on this machine since 8.04 and constantly upgraded it to the most current version.
I do believe that booting from liveCD will help, but that won't help me with the current situation. It would really be a "windows way" if I need to reinstall the whole system to make a small thing work...

---

### Post by taavikko on 2009-08-26
> **skeve said:**
> ok, I'm gonna need to download one :)
it's really hard to pinpoint the moment when this mounting thing went wrong, because I've been using ubuntu on this machine since 8.04 and constantly upgraded it to the most current version.
I do believe that booting from liveCD will help, but that won't help me with the current situation. It would really be a "windows way" if I need to reinstall the whole system to make a small thing work...

Just to rule out one thing, if liveCD works.

So you have both gnome/kde installed?

remove any leftover cruft
```
sudo aptitude purge `dpkg -l |grep ^rc | awk '{print $2}'`
```

run
```
sudo ldconfig
```
to refresh libraries.

---

### Post by skeve on 2009-08-26
ok, I've removed the old stuff, but still no difference.
Now I really need to try the current liveCD

Meanwhile, is there a way to restore all the original config files of hal, udev, devicekit-disks, gvfs, policykit and all other packages which can interfere with a mounting process?

---

### Post by taavikko on 2009-08-26
> **skeve said:**
> ok, I've removed the old stuff, but still no difference.
Now I really need to try the current liveCD


Check if there's is some obsolete packages which might interfere.
```
aptitude search ~o
```


One might use "sudo aptitude reinstall <pgk>"
to test if it helps on restoring defaults (atleast purge then install)

Other than that, I'm stumped...

---

### Post by skeve on 2009-08-26
There's about 40-50 obsolete packages, should I remove them?

As for 'aptitude reinstall' - does it restore the original configs? I thought that if I changed some config files in /etc/udev or /usr/share/polkit-1/actions or somewhere else they would remain unchanged after reinstalling...

---

### Post by taavikko on 2009-08-26
> **skeve said:**
> There's about 40-50 obsolete packages, should I remove them?


They should be marked obsolete automatically. and should be safe to remove.
BEWARE: locally installed .debs are detected also by that! including libdvdcss2

If in doubt, paste the output.

---

### Post by skeve on 2009-08-26
> **taavikko said:**
> They should be marked obsolete automatically. and should be safe to remove.
BEWARE: locally installed .debs are detected also by that! including libdvdcss2

If in doubt, paste the output.

Yeah, some of these packages were installed locally.
Anyway, at the first glance none of them has anything to do with the mounting process:

```

i   airsnort                                      - WLAN sniffer                                           
i   bluetooth-alsa                                - Bluetooth audio for Linux                              
i   bluez-audio                                   - Bluetooth audio support                                
i   dhcdbd                                        - D-Bus interface to the ISC DHCP client                 
i   dontzap                                       - Command line tool to set the DontZap option in xorg.con
i   googleearth                                   - Google Earth, a 3D map/planet viewer                   
i   juk-kde4                                      - music organizer and player for KDE 4                   
i   kandy                                         - KDE mobile phone utility                               
i   kdeprint                                      - print system for KDE                                   
i   kedit                                         - basic text editor for KDE                              
i   khexedit                                      - KDE hex editor                                         
i   kmilo-kde4                                    - laptop special keys support for KDE 4                  
i   knetworkconf-kde4                             - KDE 4 network configuration tool                       
i   kode-kde4                                     - Helper library for programmatic generation of C++ code 
i   kppp-kde4                                     - modem dialer for KDE 4                                 
i   ksvg                                          - SVG viewer for KDE                                     
i   ktnef-kde4                                    - KDE 4 TNEF viewer                                      
i   libavahi-core5                                - Avahi's embeddable mDNS/DNS-SD library                 
i   libbind9-30                                   - BIND9 Shared Library used by BIND                      
i   libbluetooth2                                 - Library to use the BlueZ Linux Bluetooth stack         
i   libboost-filesystem1.35.0                     - filesystem operations (portable paths, iteration over d
i   libboost-filesystem1.37.0                     - filesystem operations (portable paths, iteration over d
i   libboost-python1.35.0                         - Boost.Python Library                                   
i   libboost-python1.37.0                         - Boost.Python Library                                   
i A libboost-system1.35.0                         - Operating system (e.g. diagnostics support) library    
i   libboost-system1.37.0                         - Operating system (e.g. diagnostics support) library    
i   libboost-thread1.35.0                         - portable C++ multi-threading                           
i   libboost-thread1.37.0                         - portable C++ multi-threading                           
i   libbtctl4                                     - GObject Bluetooth library                              
i   libcamel1.2-11                                - The Evolution MIME message handling library            
i   libdirectfb-1.0-0                             - direct frame buffer graphics - shared libraries        
i   libdjvulibre15                                - Runtime support for the DjVu image format              
i   libdns32                                      - DNS Shared Library used by BIND                        
i A libdns35                                      - DNS Shared Library used by BIND                        
i   libedataserver1.2-9                           - Utility library for evolution data servers             
i   libexiv2-2                                    - EXIF/IPTC metadata manipulation library                
i   libgnome-desktop-2                            - Utility library for loading .desktop files - runtime fi
i   libgnomebt0                                   - GNOME Bluetooth library                                
i   libgnutls13                                   - the GNU TLS library - runtime library                  
i   libgucharmap6                                 - Unicode browser widget library (shared library)        
i   libhunspell-1.1-0                             - spell checker and morphological analyzer (shared librar
i   libisc32                                      - ISC Shared Library used by BIND                        
i   libisccc30                                    - Command Channel Library used by BIND                   
i   libisccfg30                                   - Config File Handling Library used by BIND              
i A libkcal2b                                     - KDE calendaring library                                
i A libkdepim1a                                   - KDE PIM library                                        
i A libkmime2                                     - KDE MIME interface library                             
i A libktnef1                                     - Library for handling KTNEF email attachments           
i   libltdl3                                      - A system independent dlopen wrapper for GNU libtool    
i   liblwres30                                    - Lightweight Resolver Library used by BIND              
i   libmagick10                                   - image manipulation library                             
i   libmtp7                                       - Media Transfer Protocol (MTP) library                  
i   libnm-util0                                   - network management framework (shared library)          
i   libntfs-3g23                                  - ntfs-3g filesystem in userspace (FUSE) library         
i   libntfs-3g49                                  - ntfs-3g filesystem in userspace (FUSE) library         
i   libopenal0a                                   - OpenAL is a portable library for 3D spatialized audio  
i   libopencdk10                                  - Open Crypto Development Kit (OpenCDK) (runtime)        
i   libopenexr2ldbl                               - runtime files for the OpenEXR image library            
i   libopensync1exp3                              - Synchronisation framework for email/pdas/and more      
i   libparted1.7-1                                - The GNU Parted disk partitioning shared library        
i   libpoppler-glib2                              - PDF rendering library (GLib-based shared library)      
i   libpoppler2                                   - PDF rendering library                                  
i   librra0-tools                                 - Library for synchronisation with Windows Mobile devices
i A libsbc0                                       - Subband codec (SBC) library                            
i   libsgutils1                                   - Utilities for working with generic SCSI devices (shared
i   libsmbios1                                    - Provide access to (SM)BIOS information -- dynamic libra
i   libtorrent-rasterbar2                         - C++ bittorrent library by Rasterbar Software           
i   libtotem-plparser10                           - Totem Playlist Parser library - runtime version        
i   libxklavier12                                 - X Keyboard Extension high-level API                    
i   libzephyr3                                    - Project Athena's notification service - non-Kerberos li
i A linux-image-2.6.31-4-generic                  - Linux kernel image for version 2.6.31 on x86/x86_64    
i A linux-restricted-modules-common               - Non-free Linux 2.6.28 modules helper script            
i   medibuntu-keyring                             - GnuPG key of the Medibuntu repository                  
i   mozilla-firefox-locale-ru-ru                  - Mozilla Firefox Russian language/region package        
i   networkstatus                                 - KDE network status monitor                             
i   o3read                                        - standalone converter for OpenOffice.org documents      
i   q7z                                           - A P7Zip GUI for Linux, which attempts to simplify data 
i   qmpdclient                                    - An MPD client written in Qt 4.                         
i   readahead                                     - read files into the page cache                         
i   truecrypt                                     - TrueCrypt                                              
i   ttf-bitstream-vera                            - The Bitstream Vera family of free TrueType fonts       
i   uniconvertor                                  - Universal vector graphics translator

```

---

### Post by lifeform23 on 2009-08-27
I am also having problems with automount for usb flash drives.  I can mount the drive manually, but no auto mount. Strangely enough my other Ubuntu machine (also running Jaunty but the 64bit version) has no problem whatsoever mounting the same usb key.

---

### Post by taavikko on 2009-08-28
[http://ubuntuforums.org/showthread.php?t=1251445](http://ubuntuforums.org/showthread.php?t=1251445)

---

### Post by skeve on 2009-08-28
Well, I tried booting from today's liveCD and automounting works ok here.

After checking with 'devkit-disks --monitor' I saw

```
added: /org/freedesktop/DeviceKit/Disks/devices/sdc
added: /org/freedesktop/DeviceKit/Disks/devices/sdc1

```

and that's it.
After starting dolphin and clicking on the device icon there's another string:

```
changed:     /org/freedesktop/DeviceKit/Disks/devices/sdc1
```

---

