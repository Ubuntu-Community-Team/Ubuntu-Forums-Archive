---
title: "UUE Update Broke Gnome"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by JBAlaska on 2007-09-10
I have a problem with Ubuntu Ultimate 1.4, Shortly after the UUE update repo came back online **deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all** I got a update notification. This morning I allowed the update and things went to hell in a hurry. 

Update manager said it could not do all the updates and to d/l a partial (Or words to that effect), so I started the update and got a huge amount of errors and broken dependency's (apt.log attached) All seem to be related to KDE as I have it installed to run a few apps I like, but am using Gnome.

Oddly enough when I restarted my computer, KDE was the only thing fully working, XGL and Gnome are both broken and I can only access Gnome in failsafe mode or through my root session.

I'm not one to give up and re-install, so I've been at it for 19 hours now trying to fix things. I've come along way towards getting Gnome to start normally, but I've come to the point where I need some help.

**My before trying to fix things xsession-errors.log;**

```
/usr/X11R6/bin/xsetroot:  unknown color "#1010600"
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "john"
/etc/gdm/Xsession: Beginning session setup...
startkde: Starting up...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 10361
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 0 want 85496 got 76480 (diff-requested 85496)
OggS-SEEK: at 85696 want 520 got 0 (diff-requested -85176)
*** attempt to put segment in horiz list twice
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
There are already artsd objects registered, looking if they are active...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KProcess): WARNING: _attachPty() 15
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 0 want 119288 got 106048 (diff-requested 119288)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetMIMEDescription
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 119360 want 520 got 0 (diff-requested -118840)

Error: Can't add object reference (probably artsd is already running).
       If you are sure it is not already running, remove the relevant files:

       /tmp/ksocket-john/Arts_SoundServerV2
       /tmp/ksocket-john/Arts_SoundServer
       /tmp/ksocket-john/Arts_SimpleSoundServer
       /tmp/ksocket-john/Arts_PlayObjectFactory
       /tmp/ksocket-john/Arts_AudioManager

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetMIMEDescription
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetMIMEDescription
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
KFileMetaInfo: WARNING: KTxtPlugin was created for application/x-shellscript but doesn't call addMimeTypeInfo for it!
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800007
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800007
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x260005a
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
kwin: X_SetInputFocus(0x2a00007): BadMatch (invalid parameter attributes)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
kwin: X_SetInputFocus(0x2a00007): BadMatch (invalid parameter attributes)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800a7b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800a7b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800a7b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2800a7b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800a7b
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
OggS-SEEK: at 0 want 64504 got 50752 (diff-requested 64504)
OggS-SEEK: at 64064 want 520 got 0 (diff-requested -63544)
kwin: X_SetInputFocus(0x2800007): BadMatch (invalid parameter attributes)
kwin: X_SetInputFocus(0x2800007): BadMatch (invalid parameter attributes)
OggS-SEEK: at 0 want 68088 got 65088 (diff-requested 68088)
OggS-SEEK: at 68160 want 520 got 0 (diff-requested -67640)
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2800007
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1a002ba
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
OggS-SEEK: at 16064 want 520 got 0 (diff-requested -15544)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1a0001f
OggS-SEEK: at 16192 want 520 got 0 (diff-requested -15672)
kaccess: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
ksmserver: Fatal IO error: client killed
knotify: Fatal IO error: client killed
kded: Fatal IO error: client killed
kwin: Fatal IO error: client killed
DCOP aborting call from 'konqueror-10391' to 'kded'
WARNING: DCOPReply<>: cast to 'bool' error
konqueror: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
klauncher: Exiting on signal 1
klauncher: Fatal IO error: client killed
kicker: sighandler called
kicker: Fatal IO error: client killed
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
kicker: sighandler called
*** kdesktop got signal 15 (Exiting)
*** kdesktop got signal 1 (Exiting)
kdesktop: Fatal IO error: client killed

```

**My current xsessions-errors log;**

/usr/X11R6/bin/xsetroot:  unknown color "#1010600"
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "john"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/AMD64-Ubuntu:/tmp/.ICE-unix/8180
Initializing gnome-mount extension
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Initializing nautilus-share extension
Password:

(update-notifier:8284): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
----------------------------------------------------------------------------------------------------------------------

Gnome will not quite boot and I can't figure out these last errors. I can boot my main session to KDE and my root session to Gnome normally. I attached my apt.log below showing the original errors and broken dependency's from the update. It would have been faster to just re-install, but I'm trying to learn this OS inside out, although I'm stuck at this point and sure could use some help.

Ironically I had just finished installing Acronis True Image and was going to make a image backup after I did this last update...Crap LOL.

**apt.log:**
```
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing kdelibs-data as dep of kdelibs4c2a
Installing samba-common as dep of smbclient
Installing libmtp5 as dep of rhythmbox
Installing koffice-libs as dep of krita
Installing koffice-data as dep of koffice-libs
Installing libfreetype6 as dep of libcairo2
Installing libavcodeccvs51 as dep of ffmpeg
Installing libavutilcvs49 as dep of libavcodeccvs51
Installing libfaac0 as dep of libavcodeccvs51
Installing liblame0 as dep of libavcodeccvs51
Installing libneon26 as dep of gstreamer0.10-plugins-bad
Installing gimp-data as dep of gimp
Installing libgimp2.0 as dep of gimp
Installing python-xlib as dep of istanbul
Installing libquicktime0 as dep of kino
Starting
Starting 2
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kcontrol
  Considering kcontrol 8 as a solution to konqueror 6
  Removing konqueror rather than change kcontrol
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to ksplash 4
  Removing ksplash rather than change kdebase-data
Investigating kexi
Package kexi has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kexi 4
  Removing kexi rather than change koffice-libs
Investigating kspread
Package kspread has broken dep on kexi
  Considering kexi 4 as a solution to kspread 3
  Removing kspread rather than change kexi
Investigating kpersonalizer
Package kpersonalizer has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to kpersonalizer 2
  Removing kpersonalizer rather than change kdebase-data
Investigating koshell
Package koshell has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to koshell 1
  Removing koshell rather than change koffice-libs
Investigating kdebase
Package kdebase has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kdebase 1
  Removing kdebase rather than change kcontrol
Investigating kthesaurus
Package kthesaurus has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kthesaurus 1
  Removing kthesaurus rather than change koffice-libs
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating kpresenter
Package kpresenter has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kpresenter 1
  Removing kpresenter rather than change koffice-libs
Investigating kformula
Package kformula has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kformula 1
  Removing kformula rather than change koffice-libs
Investigating kugar
Package kugar has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kugar 1
  Removing kugar rather than change koffice-libs
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 4 as a solution to ksplash-engine-moodin 1
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 1
  Removing kdm rather than change kdebase-bin
Investigating kword
Package kword has broken dep on kspread
  Considering kspread 3 as a solution to kword 1
  Removing kword rather than change kspread
Investigating kchart
Package kchart has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kchart 1
  Removing kchart rather than change koffice-libs
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 6 as a solution to konq-plugins 1
  Removing konq-plugins rather than change konqueror
Investigating karbon
Package karbon has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to karbon 1
  Removing karbon rather than change koffice-libs
Investigating kplato
Package kplato has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kplato 1
  Removing kplato rather than change koffice-libs
Investigating kivio
Package kivio has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kivio 1
  Removing kivio rather than change koffice-libs
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 1 as a solution to kubuntu-default-settings 0
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 6 as a solution to kmplayer-konq-plugins 0
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating koffice
Package koffice has broken dep on karbon
  Considering karbon 1 as a solution to koffice 0
  Removing koffice rather than change karbon
Investigating gimp-svg
Package gimp-svg has broken dep on gimp
  Considering gimp 5 as a solution to gimp-svg 0
  Removing gimp-svg rather than change gimp
Investigating kde-core
Package kde-core has broken dep on kdebase
  Considering kdebase 1 as a solution to kde-core 0
  Removing kde-core rather than change kdebase
Investigating kubuntu-konqueror-shortcuts
Package kubuntu-konqueror-shortcuts has broken dep on konqueror
  Considering konqueror 6 as a solution to kubuntu-konqueror-shortcuts 0
  Removing kubuntu-konqueror-shortcuts rather than change konqueror
Investigating kdeaddons
Package kdeaddons has broken dep on konq-plugins
  Considering konq-plugins 1 as a solution to kdeaddons 0
  Removing kdeaddons rather than change konq-plugins
Investigating tksmb
Package tksmb has broken dep on smbfs
  Considering smbfs 1 as a solution to tksmb 0
  Removing tksmb rather than change smbfs
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 0
  Removing kde-systemsettings rather than change kcontrol
Investigating ubuntustudio-graphics
Package ubuntustudio-graphics has broken dep on gimp-svg
  Considering gimp-svg 0 as a solution to ubuntustudio-graphics 0
  Removing ubuntustudio-graphics rather than change gimp-svg
Done
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing amarok as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing amarok-xine as dep of amarok
Installing libifp4 as dep of amarok
Installing libnjb5 as dep of amarok
Installing libtunepimp5 as dep of amarok
Installing libofa0 as dep of libtunepimp5
Installing hwdb-client-kde as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing k3b as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libk3b2 as dep of k3b
Installing kaffeine-xine as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kaffeine as dep of kaffeine-xine
Installing kamera as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kcontrol as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kcron as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-systemsettings as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdenetwork-filesharing as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing perl-suid as dep of kdenetwork-filesharing
Installing kdm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdnssd as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kghostview as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmailcvt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmail as dep of kmailcvt
Installing libkmime2 as dep of kmail
Installing libksieve0 as dep of kmail
Installing libmimelib1c2a as dep of kmail
Installing kdepim-kio-plugins as dep of kmail
Installing kmix as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmplayer-konq-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing konq-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kooka as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libkscan1 as dep of kooka
Installing kpdf as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kpf as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kppp as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing krdc as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing krfb as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksnapshot as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksplash as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksplash-engine-moodin as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksvg as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-default-settings as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing language-selector-qt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libarts1-akode as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libqt-perl as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libsmokeqt1 as dep of libqt-perl
Installing qca-tls as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apport-qt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
Installing digikam as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libexiv2-0.12 as dep of digikam
Installing libkexiv2-0 as dep of digikam
Installing libkipi0 as dep of digikam
Installing gtk-qt-engine as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gwenview as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing karm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing katapult as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-guidance-powermanager as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-icons-mono as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdebluetooth as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing liblockdev1 as dep of kdebluetooth
Installing libopenobex1 as dep of kdebluetooth
Installing qobex as dep of kdebluetooth
Installing kdepim-wizards as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdepim-kresources as dep of kdepim-wizards
Installing kexi as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kipi-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmilo as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing konqueror as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kontact as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-docs as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-konqueror-shortcuts as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kwalletmanager as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing scim-qtimm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing skim as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libskim0 as dep of skim
Installing speedcrunch as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libqt4-qt3support as dep of speedcrunch
Installing libqt4-sql as dep of libqt4-qt3support
Starting
Starting 2
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Re-Instated kaffeine-xine
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to ksplash 5
  Removing ksplash rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kcontrol
  Considering kcontrol 8 as a solution to konqueror 5
  Removing konqueror rather than change kcontrol
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 5 as a solution to ksplash-engine-moodin 4
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 4
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-default-settings 2
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 2
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to konq-plugins 2
  Removing konq-plugins rather than change konqueror
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 2
  Removing kde-systemsettings rather than change kcontrol
Investigating kubuntu-konqueror-shortcuts
Package kubuntu-konqueror-shortcuts has broken dep on konqueror
  Considering konqueror 5 as a solution to kubuntu-konqueror-shortcuts 0
  Removing kubuntu-konqueror-shortcuts rather than change konqueror
Investigating kexi
Package kexi has broken dep on koffice-libs
  Considering koffice-libs 4 as a solution to kexi 0
  Removing kexi rather than change koffice-libs
Investigating kaffeine
Package kaffeine has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kaffeine -1
  Holding Back kaffeine rather than change kaffeine-xine
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kubuntu-desktop 9999
  Added kcontrol to the remove list
Package kubuntu-desktop has broken dep on kde-systemsettings
  Considering kde-systemsettings 2 as a solution to kubuntu-desktop 9999
  Added kde-systemsettings to the remove list
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-desktop 9999
  Added kdm to the remove list
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added kmplayer-konq-plugins to the remove list
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added konq-plugins to the remove list
Package kubuntu-desktop has broken dep on ksplash
  Considering ksplash 5 as a solution to kubuntu-desktop 9999
  Added ksplash to the remove list
Package kubuntu-desktop has broken dep on ksplash-engine-moodin
  Considering ksplash-engine-moodin 4 as a solution to kubuntu-desktop 9999
  Added ksplash-engine-moodin to the remove list
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 2 as a solution to kubuntu-desktop 9999
  Added kubuntu-default-settings to the remove list
  Fixing kubuntu-desktop via keep of kcontrol
  Fixing kubuntu-desktop via keep of kde-systemsettings
  Fixing kubuntu-desktop via keep of kdm
  Fixing kubuntu-desktop via keep of kmplayer-konq-plugins
  Fixing kubuntu-desktop via keep of konq-plugins
  Fixing kubuntu-desktop via keep of ksplash
  Fixing kubuntu-desktop via keep of ksplash-engine-moodin
  Fixing kubuntu-desktop via keep of kubuntu-default-settings
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to ksplash 5
  Removing ksplash rather than change kdebase-data
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 5 as a solution to ksplash-engine-moodin 4
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 4
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-default-settings 2
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 2
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to konq-plugins 2
  Removing konq-plugins rather than change konqueror
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 2
  Removing kde-systemsettings rather than change kcontrol
Investigating kaffeine-xine
Package kaffeine-xine has broken dep on kaffeine
  Considering kaffeine -1 as a solution to kaffeine-xine 1
  Holding Back kaffeine-xine rather than change kaffeine
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kubuntu-desktop 9999
  Added kcontrol to the remove list
Package kubuntu-desktop has broken dep on kde-systemsettings
  Considering kde-systemsettings 2 as a solution to kubuntu-desktop 9999
  Added kde-systemsettings to the remove list
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-desktop 9999
  Added kdm to the remove list
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added kmplayer-konq-plugins to the remove list
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added konq-plugins to the remove list
Package kubuntu-desktop has broken dep on ksplash
  Considering ksplash 5 as a solution to kubuntu-desktop 9999
  Added ksplash to the remove list
Package kubuntu-desktop has broken dep on ksplash-engine-moodin
  Considering ksplash-engine-moodin 4 as a solution to kubuntu-desktop 9999
  Added ksplash-engine-moodin to the remove list
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 2 as a solution to kubuntu-desktop 9999
  Added kubuntu-default-settings to the remove list
  Fixing kubuntu-desktop via keep of kcontrol
  Fixing kubuntu-desktop via keep of kde-systemsettings
  Fixing kubuntu-desktop via keep of kdm
  Fixing kubuntu-desktop via keep of kmplayer-konq-plugins
  Fixing kubuntu-desktop via keep of konq-plugins
  Fixing kubuntu-desktop via keep of ksplash
  Fixing kubuntu-desktop via keep of ksplash-engine-moodin
  Fixing kubuntu-desktop via keep of kubuntu-default-settings
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 9999
  Added kdebase-data to the remove list
  Fixing kcontrol via keep of kdebase-data
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 9999
  Added kdebase-bin to the remove list
  Fixing kdm via keep of kdebase-bin
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 9999
  Added konqueror to the remove list
  Fixing kmplayer-konq-plugins via keep of konqueror
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
 Try to Re-Instate kdebase-data
 Try to Re-Instate kdebase-bin
Re-Instated kdebase-bin (4 vs 4)
Investigating kicker
Package kicker has broken dep on kdebase-data
  Considering kdebase-data 9999 as a solution to kicker 9
  Holding Back kicker rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to konqueror 9999
  Added kdebase-kio-plugins to the remove list
Package konqueror has broken dep on kdesktop
  Considering kdesktop 12 as a solution to konqueror 9999
  Added kdesktop to the remove list
  Fixing konqueror via keep of kdebase-kio-plugins
  Fixing konqueror via keep of kdesktop
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 9999 as a solution to kdm 9999
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-default-settings 9999
  Removing kubuntu-default-settings rather than change kdm
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 9999 as a solution to kubuntu-desktop 9999
 Try to Re-Instate kdebase-kio-plugins
 Try to Re-Instate kdesktop
Re-Instated kdesktop (2 vs 2)
 Try to Re-Instate kicker
Investigating konqueror
Package konqueror has broken dep on kdesktop
  Considering kdesktop 9999 as a solution to konqueror 9999
  Removing konqueror rather than change kdesktop
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 9999 as a solution to kmplayer-konq-plugins 9999
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 9999 as a solution to konq-plugins 9999
  Removing konq-plugins rather than change konqueror
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 9999 as a solution to kubuntu-desktop 9999
Done
ERROR:root:failed to mark 'kubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)
ERROR:root:Dist-upgrade failed: 'Can't upgrade required meta-packages'
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing kdelibs-data as dep of kdelibs4c2a
Installing samba-common as dep of smbclient
Installing libmtp5 as dep of rhythmbox
Installing koffice-libs as dep of krita
Installing koffice-data as dep of koffice-libs
Installing libfreetype6 as dep of libcairo2
Installing libavcodeccvs51 as dep of ffmpeg
Installing libavutilcvs49 as dep of libavcodeccvs51
Installing libfaac0 as dep of libavcodeccvs51
Installing liblame0 as dep of libavcodeccvs51
Installing gimp-data as dep of gimp
Installing libgimp2.0 as dep of gimp
Installing warzone2100-data as dep of warzone2100
Installing python-xlib as dep of istanbul
Installing libntfs-3g2 as dep of ntfs-3g
Installing libquicktime0 as dep of kino
Starting
Starting 2
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kcontrol
  Considering kcontrol 8 as a solution to konqueror 6
  Removing konqueror rather than change kcontrol
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to ksplash 4
  Removing ksplash rather than change kdebase-data
Investigating kexi
Package kexi has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kexi 4
  Removing kexi rather than change koffice-libs
Investigating kspread
Package kspread has broken dep on kexi
  Considering kexi 4 as a solution to kspread 3
  Removing kspread rather than change kexi
Investigating kpersonalizer
Package kpersonalizer has broken dep on kdebase-data
  Considering kdebase-data 36 as a solution to kpersonalizer 2
  Removing kpersonalizer rather than change kdebase-data
Investigating koshell
Package koshell has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to koshell 1
  Removing koshell rather than change koffice-libs
Investigating kdebase
Package kdebase has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kdebase 1
  Removing kdebase rather than change kcontrol
Investigating gimp-svg
Package gimp-svg has broken dep on gimp
  Considering gimp 6 as a solution to gimp-svg 1
  Removing gimp-svg rather than change gimp
Investigating kthesaurus
Package kthesaurus has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kthesaurus 1
  Removing kthesaurus rather than change koffice-libs
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating kpresenter
Package kpresenter has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kpresenter 1
  Removing kpresenter rather than change koffice-libs
Investigating kformula
Package kformula has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kformula 1
  Removing kformula rather than change koffice-libs
Investigating kugar
Package kugar has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kugar 1
  Removing kugar rather than change koffice-libs
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 4 as a solution to ksplash-engine-moodin 1
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 1
  Removing kdm rather than change kdebase-bin
Investigating kword
Package kword has broken dep on kspread
  Considering kspread 3 as a solution to kword 1
  Removing kword rather than change kspread
Investigating kchart
Package kchart has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kchart 1
  Removing kchart rather than change koffice-libs
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 6 as a solution to konq-plugins 1
  Removing konq-plugins rather than change konqueror
Investigating karbon
Package karbon has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to karbon 1
  Removing karbon rather than change koffice-libs
Investigating kplato
Package kplato has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kplato 1
  Removing kplato rather than change koffice-libs
Investigating kivio
Package kivio has broken dep on koffice-libs
  Considering koffice-libs 54 as a solution to kivio 1
  Removing kivio rather than change koffice-libs
Investigating ubuntustudio-graphics
Package ubuntustudio-graphics has broken dep on gimp-svg
  Considering gimp-svg 1 as a solution to ubuntustudio-graphics 0
  Removing ubuntustudio-graphics rather than change gimp-svg
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 1 as a solution to kubuntu-default-settings 0
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 6 as a solution to kmplayer-konq-plugins 0
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating koffice
Package koffice has broken dep on karbon
  Considering karbon 1 as a solution to koffice 0
  Removing koffice rather than change karbon
Investigating kde-core
Package kde-core has broken dep on kdebase
  Considering kdebase 1 as a solution to kde-core 0
  Removing kde-core rather than change kdebase
Investigating kubuntu-konqueror-shortcuts
Package kubuntu-konqueror-shortcuts has broken dep on konqueror
  Considering konqueror 6 as a solution to kubuntu-konqueror-shortcuts 0
  Removing kubuntu-konqueror-shortcuts rather than change konqueror
Investigating kdeaddons
Package kdeaddons has broken dep on konq-plugins
  Considering konq-plugins 1 as a solution to kdeaddons 0
  Removing kdeaddons rather than change konq-plugins
Investigating tksmb
Package tksmb has broken dep on smbfs
  Considering smbfs 1 as a solution to tksmb 0
  Removing tksmb rather than change smbfs
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 0
  Removing kde-systemsettings rather than change kcontrol
Done
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing amarok as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing amarok-xine as dep of amarok
Installing libifp4 as dep of amarok
Installing libnjb5 as dep of amarok
Installing libtunepimp5 as dep of amarok
Installing libofa0 as dep of libtunepimp5
Installing hwdb-client-kde as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing k3b as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libk3b2 as dep of k3b
Installing kaffeine-xine as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kaffeine as dep of kaffeine-xine
Installing kamera as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kcontrol as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kcron as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-systemsettings as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdenetwork-filesharing as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing perl-suid as dep of kdenetwork-filesharing
Installing kdm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdnssd as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kghostview as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmailcvt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmail as dep of kmailcvt
Installing libkmime2 as dep of kmail
Installing libksieve0 as dep of kmail
Installing libmimelib1c2a as dep of kmail
Installing kdepim-kio-plugins as dep of kmail
Installing kmix as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmplayer-konq-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing konq-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kooka as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libkscan1 as dep of kooka
Installing kpdf as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kpf as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kppp as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing krdc as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing krfb as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksnapshot as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksplash as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksplash-engine-moodin as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ksvg as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-default-settings as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing language-selector-qt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libarts1-akode as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libqt-perl as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libsmokeqt1 as dep of libqt-perl
Installing qca-tls as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apport-qt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
Installing digikam as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libexiv2-0.12 as dep of digikam
Installing libkexiv2-0 as dep of digikam
Installing libkipi0 as dep of digikam
Installing gtk-qt-engine as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gwenview as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing karm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing katapult as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-guidance-powermanager as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kde-icons-mono as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdebluetooth as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing liblockdev1 as dep of kdebluetooth
Installing libopenobex1 as dep of kdebluetooth
Installing qobex as dep of kdebluetooth
Installing kdepim-wizards as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kdepim-kresources as dep of kdepim-wizards
Installing kexi as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kipi-plugins as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kmilo as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing konqueror as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kontact as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-docs as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kubuntu-konqueror-shortcuts as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kwalletmanager as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing scim-qtimm as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing skim as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libskim0 as dep of skim
Installing speedcrunch as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libqt4-qt3support as dep of speedcrunch
Installing libqt4-sql as dep of libqt4-qt3support
Starting
Starting 2
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Re-Instated kaffeine-xine
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to ksplash 5
  Removing ksplash rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kcontrol
  Considering kcontrol 8 as a solution to konqueror 5
  Removing konqueror rather than change kcontrol
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 5 as a solution to ksplash-engine-moodin 4
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 4
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-default-settings 2
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 2
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to konq-plugins 2
  Removing konq-plugins rather than change konqueror
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 2
  Removing kde-systemsettings rather than change kcontrol
Investigating kubuntu-konqueror-shortcuts
Package kubuntu-konqueror-shortcuts has broken dep on konqueror
  Considering konqueror 5 as a solution to kubuntu-konqueror-shortcuts 0
  Removing kubuntu-konqueror-shortcuts rather than change konqueror
Investigating kexi
Package kexi has broken dep on koffice-libs
  Considering koffice-libs 4 as a solution to kexi 0
  Removing kexi rather than change koffice-libs
Investigating kaffeine
Package kaffeine has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kaffeine -1
  Holding Back kaffeine rather than change kaffeine-xine
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kubuntu-desktop 9999
  Added kcontrol to the remove list
Package kubuntu-desktop has broken dep on kde-systemsettings
  Considering kde-systemsettings 2 as a solution to kubuntu-desktop 9999
  Added kde-systemsettings to the remove list
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-desktop 9999
  Added kdm to the remove list
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added kmplayer-konq-plugins to the remove list
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added konq-plugins to the remove list
Package kubuntu-desktop has broken dep on ksplash
  Considering ksplash 5 as a solution to kubuntu-desktop 9999
  Added ksplash to the remove list
Package kubuntu-desktop has broken dep on ksplash-engine-moodin
  Considering ksplash-engine-moodin 4 as a solution to kubuntu-desktop 9999
  Added ksplash-engine-moodin to the remove list
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 2 as a solution to kubuntu-desktop 9999
  Added kubuntu-default-settings to the remove list
  Fixing kubuntu-desktop via keep of kcontrol
  Fixing kubuntu-desktop via keep of kde-systemsettings
  Fixing kubuntu-desktop via keep of kdm
  Fixing kubuntu-desktop via keep of kmplayer-konq-plugins
  Fixing kubuntu-desktop via keep of konq-plugins
  Fixing kubuntu-desktop via keep of ksplash
  Fixing kubuntu-desktop via keep of ksplash-engine-moodin
  Fixing kubuntu-desktop via keep of kubuntu-default-settings
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 8
  Removing kcontrol rather than change kdebase-data
Investigating ksplash
Package ksplash has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to ksplash 5
  Removing ksplash rather than change kdebase-data
Investigating ksplash-engine-moodin
Package ksplash-engine-moodin has broken dep on ksplash
  Considering ksplash 5 as a solution to ksplash-engine-moodin 4
  Removing ksplash-engine-moodin rather than change ksplash
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 4
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-default-settings 2
  Removing kubuntu-default-settings rather than change kdm
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 2
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to konq-plugins 2
  Removing konq-plugins rather than change konqueror
Investigating kde-systemsettings
Package kde-systemsettings has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kde-systemsettings 2
  Removing kde-systemsettings rather than change kcontrol
Investigating kaffeine-xine
Package kaffeine-xine has broken dep on kaffeine
  Considering kaffeine -1 as a solution to kaffeine-xine 1
  Holding Back kaffeine-xine rather than change kaffeine
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kcontrol
  Considering kcontrol 8 as a solution to kubuntu-desktop 9999
  Added kcontrol to the remove list
Package kubuntu-desktop has broken dep on kde-systemsettings
  Considering kde-systemsettings 2 as a solution to kubuntu-desktop 9999
  Added kde-systemsettings to the remove list
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 4 as a solution to kubuntu-desktop 9999
  Added kdm to the remove list
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added kmplayer-konq-plugins to the remove list
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 2 as a solution to kubuntu-desktop 9999
  Added konq-plugins to the remove list
Package kubuntu-desktop has broken dep on ksplash
  Considering ksplash 5 as a solution to kubuntu-desktop 9999
  Added ksplash to the remove list
Package kubuntu-desktop has broken dep on ksplash-engine-moodin
  Considering ksplash-engine-moodin 4 as a solution to kubuntu-desktop 9999
  Added ksplash-engine-moodin to the remove list
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 2 as a solution to kubuntu-desktop 9999
  Added kubuntu-default-settings to the remove list
  Fixing kubuntu-desktop via keep of kcontrol
  Fixing kubuntu-desktop via keep of kde-systemsettings
  Fixing kubuntu-desktop via keep of kdm
  Fixing kubuntu-desktop via keep of kmplayer-konq-plugins
  Fixing kubuntu-desktop via keep of konq-plugins
  Fixing kubuntu-desktop via keep of ksplash
  Fixing kubuntu-desktop via keep of ksplash-engine-moodin
  Fixing kubuntu-desktop via keep of kubuntu-default-settings
Investigating kcontrol
Package kcontrol has broken dep on kdebase-data
  Considering kdebase-data 32 as a solution to kcontrol 9999
  Added kdebase-data to the remove list
  Fixing kcontrol via keep of kdebase-data
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 12 as a solution to kdm 9999
  Added kdebase-bin to the remove list
  Fixing kdm via keep of kdebase-bin
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to kmplayer-konq-plugins 9999
  Added konqueror to the remove list
  Fixing kmplayer-konq-plugins via keep of konqueror
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
 Try to Re-Instate kdebase-data
 Try to Re-Instate kdebase-bin
Re-Instated kdebase-bin (4 vs 4)
Investigating kicker
Package kicker has broken dep on kdebase-data
  Considering kdebase-data 9999 as a solution to kicker 9
  Holding Back kicker rather than change kdebase-data
Investigating konqueror
Package konqueror has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to konqueror 9999
  Added kdebase-kio-plugins to the remove list
Package konqueror has broken dep on kdesktop
  Considering kdesktop 12 as a solution to konqueror 9999
  Added kdesktop to the remove list
  Fixing konqueror via keep of kdebase-kio-plugins
  Fixing konqueror via keep of kdesktop
Investigating kdm
Package kdm has broken dep on kdebase-bin
  Considering kdebase-bin 9999 as a solution to kdm 9999
  Removing kdm rather than change kdebase-bin
Investigating kubuntu-default-settings
Package kubuntu-default-settings has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-default-settings 9999
  Removing kubuntu-default-settings rather than change kdm
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 9999 as a solution to kubuntu-desktop 9999
 Try to Re-Instate kdebase-kio-plugins
 Try to Re-Instate kdesktop
Re-Instated kdesktop (2 vs 2)
 Try to Re-Instate kicker
Investigating konqueror
Package konqueror has broken dep on kdesktop
  Considering kdesktop 9999 as a solution to konqueror 9999
  Removing konqueror rather than change kdesktop
Investigating kmplayer-konq-plugins
Package kmplayer-konq-plugins has broken dep on konqueror
  Considering konqueror 9999 as a solution to kmplayer-konq-plugins 9999
  Removing kmplayer-konq-plugins rather than change konqueror
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 9999 as a solution to konq-plugins 9999
  Removing konq-plugins rather than change konqueror
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on kaffeine-xine
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
  Considering kaffeine-xine 1 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kdm
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
  Considering kdm 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kmplayer-konq-plugins
  Considering kmplayer-konq-plugins 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on konq-plugins
  Considering konq-plugins 9999 as a solution to kubuntu-desktop 9999
Package kubuntu-desktop has broken dep on kubuntu-default-settings
  Considering kubuntu-default-settings 9999 as a solution to kubuntu-desktop 9999
Done
ERROR:root:failed to mark 'kubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)
ERROR:root:Dist-upgrade failed: 'Can't upgrade required meta-packages'

```

---

