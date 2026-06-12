---
title: "Remastersys 3.0.1-1 &amp; 11.10 - Can't get past login on Live CD"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by luvit on 2012-02-13
.
Hi, I heavily used Remastersys during 2008-2009 and found it quit simple, but for some reason, I've been struggling with Remastersys 3.0.1-1 & a clean install of 11.10. -- I've been reading for solutions for days & may be misunderstanding existing threads which contain fixes for my exact problem:

I cannot get past the GUI login screen on the Live CD.

[COLOR="Red"]After the break=bottom takes effect, I find /cdrom/ is empty/not mounted.
I can manually mount /dev/scd0 as /cdrom/, but this observation may be unrelated.
[/COLOR]
[LIST]
[*]Base OS............ clean install Ubuntu 11.10 with some uninstalled packages to get below 700MB
[*]Desktop.............. default desktop of 11.10 with compiz cube/rotate enabled / wall is disabled (Gnome3 with Unity?)
[*]Login Manager.. default login manager of 11.10
[*]Remastersys...... 3.0.0-1
[/LIST]
[color=red]_**casper.log**_[/color]
[img]https://lh4.googleusercontent.com/-i_IZZm_lcjI/TzlilAUawTI/AAAAAAAABQo/ONFikIVF4sk/s800/2012-02-13%252012.00.14.jpg[/img]

[color=red]_**remastersys.log**_[/color]
```
Distribution Mode Selected
Enabling remastersys-firstboot
Checking filesystem type of the Working Folder as it must be a valid linux filesystem for permissions
/media/isobuildpart/remastersys is on an ext4 filesystem
Making sure popularity contest is not installed
Installing the Ubiquity GTK frontend
Checking if the /media/isobuildpart/remastersys folder has been created
Creating /media/isobuildpart/remastersys folder tree
Creating /media/isobuildpart/remastersys/ISOTMP folder tree
Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient
Cleaning up files not needed for the live in /media/isobuildpart/remastersys/dummysys
Cleaning up passwd, group, shadow and gshadow files for the live system
Making sure adduser and autologin functions of casper are set properly
Copying memtest86+ for the live system
Creating isolinux setup for the live system
Checking the ARCH of the system and setting the README.diskdefines file
Creating filesystem.manifest and filesystem.manifest-desktop
Creating the casper.conf file.
Checking and setting user-setup-apply for the live system
Setting up casper and ubiquity options for dist mode
Creating a new initial ramdisk for the live system
Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires
Adding stage 2 files/folders that the livecd requires
------------------------------------------------------
Mount information
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sdc3 on /media/isobuildpart type ext4 (rw,nosuid,nodev,uhelper=udisks)
------------------------------------------------------
Disk size information
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             3.8G  2.1G  1.6G  57% /
udev                  995M  8.0K  995M   1% /dev
tmpfs                 402M  836K  401M   1% /run
none                  5.0M  8.0K  5.0M   1% /run/lock
none                 1005M  120K 1005M   1% /run/shm
/dev/sdc3             3.0G  1.1G  1.8G  37% /media/isobuildpart
------------------------------------------------------
Casper Script info
total 140
-rwxr-xr-x 1 root root  297 2011-11-08 10:40 01integrity_check
-rwxr-xr-x 1 root root  467 2011-11-08 10:40 05mountpoints
-rwxr-xr-x 1 root root  571 2011-11-08 10:40 07remove_oem_config
-rwxr-xr-x 1 root root 3375 2011-11-08 10:40 10adduser
-rwxr-xr-x 1 root root  400 2011-11-08 10:40 12fstab
-rwxr-xr-x 1 root root  830 2011-11-08 10:40 13swap
-rwxr-xr-x 1 root root 1431 2011-11-08 10:40 14locales
-rwxr-xr-x 1 root root 2554 2011-11-08 10:40 15autologin
-rwxr-xr-x 1 root root  577 2011-11-08 10:40 18hostname
-rwxr-xr-x 1 root root 8721 2011-11-08 10:40 19keyboard
-rwxr-xr-x 1 root root  546 2011-11-08 10:40 20xconfig
-rwxr-xr-x 1 root root  531 2011-11-08 10:40 22gnome_panel_data
-rwxr-xr-x 1 root root  867 2011-11-08 10:40 22screensaver
-rwxr-xr-x 1 root root  577 2011-11-08 10:40 22serialtty
-rwxr-xr-x 1 root root  410 2011-11-08 10:40 22sslcert
-rwxr-xr-x 1 root root  380 2011-11-08 10:40 23etc_modules
-rwxr-xr-x 1 root root 3295 2011-11-08 10:40 23networking
-rwxr-xr-x 1 root root 2102 2011-11-08 10:47 24preseed
-rwxr-xr-x 1 root root 1996 2011-11-08 10:40 25configure_init
-rwxr-xr-x 1 root root  644 2011-11-08 10:40 26disable_user_menu
-rwxr-xr-x 1 root root 1421 2011-11-08 10:40 30accessibility
-rwxr-xr-x 1 root root 1152 2011-11-08 10:40 31disable_update_notifier
-rwxr-xr-x 1 root root  463 2011-11-08 10:40 32disable_hibernation
-rwxr-xr-x 1 root root  369 2011-11-08 10:40 33enable_apport_crashes
-rwxr-xr-x 1 root root  928 2011-11-08 10:40 34disable_kde_services
-rwxr-xr-x 1 root root  562 2011-11-08 10:40 35fix_language_selector
-rwxr-xr-x 1 root root  407 2011-11-08 10:40 36disable_trackerd
-rwxr-xr-x 1 root root  908 2011-11-08 10:40 40install_driver_updates
-rwxr-xr-x 1 root root  518 2011-11-08 10:40 41apt_cdrom
-rwxr-xr-x 1 root root  847 2011-11-08 10:40 43disable_updateinitramfs
-rwxr-xr-x 1 root root  640 2011-11-08 10:40 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  214 2011-11-08 10:40 48kubuntu_disable_restart_notifications
-rwxr-xr-x 1 root root  169 2011-11-08 10:40 49kubuntu_mobile_session
------------------------------------------------------
/etc/remastersys.conf info

#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/media/isobuildpart"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES=""


# Here you can change the livecd/dvd username
LIVEUSER="lbl"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="luvitsblacklabel"


# Here you can change the name of the ISO file that is created
CUSTOMISO="luvitsblacklabel-2-11-2012.iso"

# Here you can change the mksquashfs options
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"


# Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show 
BACKUPSHOWINSTALL="1"


# Here you can change the url for the usb-creator info
LIVECDURL=""
------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM
 
export USERNAME="lbl"
export USERFULLNAME="Live session user"
export HOST="lbl"
export BUILD_SYSTEM="Ubuntu"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
colord:x:102:105:colord colour management daemon,,,:/var/lib/colord:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
lightdm:x:104:108:Light Display Manager:/var/lib/lightdm:/bin/false
avahi-autoipd:x:105:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:113:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:113:123::/home/saned:/bin/false
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
colord:x:105:
scanner:x:106:colord
messagebus:x:107:
lightdm:x:108:
nopasswdlogin:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
avahi:x:113:
netdev:x:114:
bluetooth:x:115:
lpadmin:x:116:
ssl-cert:x:117:
admin:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
sambashare:x:124:
nogroup:x:65534:
------------------------------------------------------
/etc/X11/default-display-manager info
/usr/sbin/lightdm
------------------------------------------------------
/etc/skel info
/etc/skel
/etc/skel/.gnome2
/etc/skel/.gnome2/nautilus-scripts
/etc/skel/.gnome2/keyrings
/etc/skel/.local
/etc/skel/.local/share
/etc/skel/.local/share/zeitgeist
/etc/skel/.local/share/zeitgeist/activity.sqlite-journal
/etc/skel/.local/share/zeitgeist/fts.index
/etc/skel/.local/share/zeitgeist/fts.index/iamchert
/etc/skel/.local/share/zeitgeist/fts.index/position.baseA
/etc/skel/.local/share/zeitgeist/fts.index/position.baseB
/etc/skel/.local/share/zeitgeist/fts.index/record.baseA
/etc/skel/.local/share/zeitgeist/fts.index/flintlock
/etc/skel/.local/share/zeitgeist/fts.index/record.DB
/etc/skel/.local/share/zeitgeist/fts.index/record.baseB
/etc/skel/.local/share/zeitgeist/fts.index/termlist.DB
/etc/skel/.local/share/zeitgeist/fts.index/termlist.baseB
/etc/skel/.local/share/zeitgeist/fts.index/postlist.baseB
/etc/skel/.local/share/zeitgeist/fts.index/termlist.baseA
/etc/skel/.local/share/zeitgeist/fts.index/postlist.baseA
/etc/skel/.local/share/zeitgeist/datasources.pickle
/etc/skel/.local/share/icc
/etc/skel/.local/share/icc/edid-0a613af5b7e318a95c78081392dcebcf.icc
/etc/skel/.local/share/applications
/etc/skel/.local/share/applications/mimeapps.list
/etc/skel/.local/share/webkit
/etc/skel/.local/share/webkit/icondatabase
/etc/skel/.local/share/webkit/icondatabase/WebpageIcons.db
/etc/skel/.local/share/gvfs-metadata
/etc/skel/.local/share/gvfs-metadata/home-0bb9fefb.log
/etc/skel/.local/share/gvfs-metadata/label-luvitsblacklabel
/etc/skel/.local/share/gvfs-metadata/uuid-3439a1b3-303a-49db-a501-35f809da0c3c-ec4cf464.log
/etc/skel/.local/share/gvfs-metadata/trash:
/etc/skel/.local/share/gvfs-metadata/uuid-2c5c4b6d-25ab-44ab-9aa0-208b20baf51f-84edc016.log
/etc/skel/.local/share/gvfs-metadata/uuid-9004e0df-85bc-4769-b551-11726168e800-6d26c05c.log
/etc/skel/.local/share/gvfs-metadata/uuid-2c5c4b6d-25ab-44ab-9aa0-208b20baf51f
/etc/skel/.local/share/gvfs-metadata/uuid-45539849-08ae-4a0c-b35a-782306684c15-7498b598.log
/etc/skel/.local/share/gvfs-metadata/home
/etc/skel/.local/share/gvfs-metadata/root-299b06ba.log
/etc/skel/.local/share/gvfs-metadata/label-luvitsblacklabel-81468945.log
/etc/skel/.local/share/gvfs-metadata/trash:-d6296f3d.log
/etc/skel/.local/share/gvfs-metadata/uuid-45539849-08ae-4a0c-b35a-782306684c15
/etc/skel/.local/share/gvfs-metadata/uuid-9848B05948B037B8-dd06e847.log
/etc/skel/.local/share/gvfs-metadata/root
/etc/skel/.local/share/.converted-launchers
/etc/skel/.local/share/gsettings-data-convert
/etc/skel/.gconf
/etc/skel/.gconf/desktop
/etc/skel/.gconf/desktop/%gconf.xml
/etc/skel/.gconf/desktop/unity-2d
/etc/skel/.gconf/desktop/unity-2d/%gconf.xml
/etc/skel/.gconf/desktop/unity-2d/launcher
/etc/skel/.gconf/desktop/unity-2d/launcher/%gconf.xml
/etc/skel/.gconf/desktop/gnome
/etc/skel/.gconf/desktop/gnome/accessibility
/etc/skel/.gconf/desktop/gnome/accessibility/keyboard
/etc/skel/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml
/etc/skel/.gconf/desktop/gnome/accessibility/%gconf.xml
/etc/skel/.gconf/desktop/gnome/url-handlers
/etc/skel/.gconf/desktop/gnome/url-handlers/about
/etc/skel/.gconf/desktop/gnome/url-handlers/about/%gconf.xml
/etc/skel/.gconf/desktop/gnome/url-handlers/%gconf.xml
/etc/skel/.gconf/desktop/gnome/url-handlers/http
/etc/skel/.gconf/desktop/gnome/url-handlers/http/%gconf.xml
/etc/skel/.gconf/desktop/gnome/url-handlers/https
/etc/skel/.gconf/desktop/gnome/url-handlers/https/%gconf.xml
/etc/skel/.gconf/desktop/gnome/url-handlers/unknown
/etc/skel/.gconf/desktop/gnome/url-handlers/unknown/%gconf.xml
/etc/skel/.gconf/desktop/gnome/sound
/etc/skel/.gconf/desktop/gnome/sound/%gconf.xml
/etc/skel/.gconf/desktop/gnome/%gconf.xml
/etc/skel/.gconf/desktop/gnome/applications
/etc/skel/.gconf/desktop/gnome/applications/%gconf.xml
/etc/skel/.gconf/desktop/gnome/applications/browser
/etc/skel/.gconf/desktop/gnome/applications/browser/%gconf.xml
/etc/skel/.gconf/desktop/gnome/peripherals
/etc/skel/.gconf/desktop/gnome/peripherals/mouse
/etc/skel/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml
/etc/skel/.gconf/desktop/gnome/peripherals/%gconf.xml
/etc/skel/.gconf/desktop/gnome/background
/etc/skel/.gconf/desktop/gnome/background/%gconf.xml
/etc/skel/.gconf/desktop/gnome/interface
/etc/skel/.gconf/desktop/gnome/interface/%gconf.xml
/etc/skel/.gconf/apps
/etc/skel/.gconf/apps/file-roller
/etc/skel/.gconf/apps/file-roller/%gconf.xml
/etc/skel/.gconf/apps/file-roller/ui
/etc/skel/.gconf/apps/file-roller/ui/%gconf.xml
/etc/skel/.gconf/apps/file-roller/listing
/etc/skel/.gconf/apps/file-roller/listing/%gconf.xml
/etc/skel/.gconf/apps/compiz-1
/etc/skel/.gconf/apps/compiz-1/general
/etc/skel/.gconf/apps/compiz-1/general/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/general/screen0
/etc/skel/.gconf/apps/compiz-1/general/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/general/screen0/options
/etc/skel/.gconf/apps/compiz-1/general/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins
/etc/skel/.gconf/apps/compiz-1/plugins/td
/etc/skel/.gconf/apps/compiz-1/plugins/td/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/td/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/td/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/td/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/td/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cube
/etc/skel/.gconf/apps/compiz-1/plugins/cube/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cube/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/cube/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cube/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/cube/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/cubeaddon/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/gnomecompat/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/showmouse/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/unityshell/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/rotate
/etc/skel/.gconf/apps/compiz-1/plugins/rotate/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/rotate/screen0
/etc/skel/.gconf/apps/compiz-1/plugins/rotate/screen0/%gconf.xml
/etc/skel/.gconf/apps/compiz-1/plugins/rotate/screen0/options
/etc/skel/.gconf/apps/compiz-1/plugins/rotate/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/nautilus
/etc/skel/.gconf/apps/nautilus/%gconf.xml
/etc/skel/.gconf/apps/nautilus/preferences
/etc/skel/.gconf/apps/nautilus/preferences/%gconf.xml
/etc/skel/.gconf/apps/nautilus/list_view
/etc/skel/.gconf/apps/nautilus/list_view/%gconf.xml
/etc/skel/.gconf/apps/update-manager
/etc/skel/.gconf/apps/update-manager/%gconf.xml
/etc/skel/.gconf/apps/%gconf.xml
/etc/skel/.gconf/apps/gedit-2
/etc/skel/.gconf/apps/gedit-2/%gconf.xml
/etc/skel/.gconf/apps/gedit-2/preferences
/etc/skel/.gconf/apps/gedit-2/preferences/%gconf.xml
/etc/skel/.gconf/apps/gedit-2/preferences/ui
/etc/skel/.gconf/apps/gedit-2/preferences/ui/%gconf.xml
/etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar
/etc/skel/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml
/etc/skel/.gconf/apps/gedit-2/plugins
/etc/skel/.gconf/apps/gedit-2/plugins/%gconf.xml
/etc/skel/.gconf/apps/nm-applet
/etc/skel/.gconf/apps/nm-applet/%gconf.xml
/etc/skel/.gconf/apps/update-notifier
/etc/skel/.gconf/apps/update-notifier/%gconf.xml
/etc/skel/.gconf/apps/gnome-terminal
/etc/skel/.gconf/apps/gnome-terminal/profiles
/etc/skel/.gconf/apps/gnome-terminal/profiles/%gconf.xml
/etc/skel/.gconf/apps/gnome-terminal/profiles/Default
/etc/skel/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
/etc/skel/.gconf/apps/gnome-terminal/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1
/etc/skel/.gconf/apps/compizconfig-1/profiles
/etc/skel/.gconf/apps/compizconfig-1/profiles/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/general/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/zoom/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/scale/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/switcher/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitymtgrabhandles/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/fade/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/staticswitcher/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/water/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/workarounds/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/cube/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/opengl/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/bailer/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/obs/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wobbly/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/decor/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/gnomecompat/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/mousepoll/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/composite/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/annotate/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/snap/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/commands/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/debugspew/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/resize/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/wall/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/detection/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/blur/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/clone/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/unitydialog/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/screenshot/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/animation/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/rotate/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/ezoom/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/place/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/move/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/session/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/vpswitch/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0/options
/etc/skel/.gconf/apps/compizconfig-1/profiles/Default/plugins/core/screen0/options/%gconf.xml
/etc/skel/.gconf/apps/compizconfig-1/%gconf.xml
/etc/skel/.gconf/apps/deja-dup
/etc/skel/.gconf/apps/deja-dup/s3
/etc/skel/.gconf/apps/deja-dup/s3/%gconf.xml
/etc/skel/.gconf/apps/deja-dup/%gconf.xml
/etc/skel/.gconf/apps/metacity
/etc/skel/.gconf/apps/metacity/general
/etc/skel/.gconf/apps/metacity/general/%gconf.xml
/etc/skel/.gconf/apps/metacity/%gconf.xml
/etc/skel/.gconf/apps/metacity/global_keybindings
/etc/skel/.gconf/apps/metacity/global_keybindings/%gconf.xml
/etc/skel/.gconf/apps/metacity/window_keybindings
/etc/skel/.gconf/apps/metacity/window_keybindings/%gconf.xml
/etc/skel/.gconf/apps/brasero
/etc/skel/.gconf/apps/brasero/%gconf.xml
/etc/skel/.gconf/apps/brasero/display
/etc/skel/.gconf/apps/brasero/display/%gconf.xml
/etc/skel/.config
/etc/skel/.config/enchant
/etc/skel/.config/enchant/en_US.dic
/etc/skel/.config/enchant/en_US.exc
/etc/skel/.config/software-center
/etc/skel/.config/software-center/softwarecenter.cfg
/etc/skel/.config/autostart
/etc/skel/.config/autostart/indicator-weather.desktop
/etc/skel/.config/autostart/indicator-multiload.desktop
/etc/skel/.config/dconf
/etc/skel/.config/compiz-1
/etc/skel/.config/compiz-1/compizconfig
/etc/skel/.config/compiz-1/compizconfig/done_upgrades
/etc/skel/.config/compiz-1/compizconfig/config
/etc/skel/.config/gedit
/etc/skel/.config/gedit/accels
/etc/skel/.config/nautilus
/etc/skel/.config/nautilus/desktop-metadata
/etc/skel/.config/bleachbit
/etc/skel/.config/gnome-session
/etc/skel/.config/gnome-session/saved-session
/etc/skel/.config/ibus
/etc/skel/.config/ibus/bus
/etc/skel/.config/gnome-disk-utility
/etc/skel/.config/gnome-disk-utility/ata-smart-ignore
/etc/skel/.config/google-chrome
/etc/skel/.config/google-chrome/Safe Browsing Download
/etc/skel/.config/google-chrome/First Run
/etc/skel/.config/google-chrome/Safe Browsing Csd Whitelist
/etc/skel/.config/google-chrome/Safe Browsing Bloom Filter 2
/etc/skel/.config/google-chrome/Temp
/etc/skel/.config/google-chrome/Dictionaries
/etc/skel/.config/google-chrome/Safe Browsing Bloom
/etc/skel/.config/google-chrome/Local State
/etc/skel/.config/google-chrome/Service State
/etc/skel/.config/google-chrome/chrome_shutdown_ms.txt
/etc/skel/.config/google-chrome/Default
/etc/skel/.config/google-chrome/Default/Favicons
/etc/skel/.config/google-chrome/Default/Bookmarks
/etc/skel/.config/google-chrome/Default/Local Storage
/etc/skel/.config/google-chrome/Default/Local Storage/chrome-extension_eemcgdkfndhakfknompkggombfjjjeno_0.localstorage
/etc/skel/.config/google-chrome/Default/History
/etc/skel/.config/google-chrome/Default/Login Data
/etc/skel/.config/google-chrome/Default/QuotaManager
/etc/skel/.config/google-chrome/Default/User StyleSheets
/etc/skel/.config/google-chrome/Default/User StyleSheets/Custom.css
/etc/skel/.config/google-chrome/Default/Preferences
/etc/skel/.config/google-chrome/Default/Web Data
/etc/skel/.config/google-chrome/Default/Shortcuts
/etc/skel/.config/google-chrome/Default/Extensions
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fr
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sr
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pt_PT
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pt_PT/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hr
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/nl
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/nl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pt_BR
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pt_BR/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/zh_CN
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/zh_CN/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/bg
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/bg/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/lt
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/lt/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ru
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ru/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/id
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/id/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/uk
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/uk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/zh_TW
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/zh_TW/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en_US
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en_US/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/it
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/it/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/lv
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/lv/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/es_419
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/es_419/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sv
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sv/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/da
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/da/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/es
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/es/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/de
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/de/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pl
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/pl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/et
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/et/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/th
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/th/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sk
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/el
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/el/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ko
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ko/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hu
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hu/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ar
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ar/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ro
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ro/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hi
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/hi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fil
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fil/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/tr
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/tr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/he
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/he/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en_GB
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/en_GB/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/vi
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/vi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ja
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ja/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sl
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/sl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fi
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/fi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/cs
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/cs/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/no
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/no/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ca
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/_locales/ca/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/128.png
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/manifest.json
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/32.png
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/48.png
/etc/skel/.config/google-chrome/Default/Extensions/coobgpohoikkiipiblmjeljniedjpjpf/0.0.0.17_0/16.png
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fr
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sr
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pt_PT
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pt_PT/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hr
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/nl
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/nl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/en
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/en/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pt_BR
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pt_BR/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/zh_CN
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/zh_CN/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/bg
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/bg/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/lt
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/lt/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ru
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ru/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/id
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/id/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/uk
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/uk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/zh_TW
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/zh_TW/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/it
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/it/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/lv
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/lv/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sv
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sv/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/da
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/da/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/es
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/es/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/de
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/de/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pl
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/pl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/th
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/th/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sk
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/el
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/el/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ko
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ko/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hu
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hu/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ar
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ar/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ro
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ro/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hi
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/hi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fil
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fil/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/tr
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/tr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/he
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/he/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/vi
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/vi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ja
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ja/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sl
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/sl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fi
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/fi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/cs
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/cs/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/no
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/no/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ca
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/_locales/ca/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/128.png
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/manifest.json
/etc/skel/.config/google-chrome/Default/Extensions/blpcfgokakmgnkcojhhkbfbldkacnbeo/4.2.3_0/__MACOSX
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/se
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/se/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fr
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sr
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pt_PT
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pt_PT/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hr
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/nl
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/nl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/en
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/en/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pt_BR
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pt_BR/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/zh_CN
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/zh_CN/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/bg
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/bg/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/lt
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/lt/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ru
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ru/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/id
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/id/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/uk
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/uk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/zh_TW
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/zh_TW/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/it
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/it/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/lv
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/lv/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/da
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/da/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/es
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/es/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/de
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/de/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pl
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/pl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/th
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/th/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sk
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sk/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/el
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/el/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ko
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ko/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hu
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hu/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ar
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ar/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ro
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ro/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hi
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/hi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fil
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fil/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/tr
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/tr/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/vi
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/vi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ja
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ja/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sl
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/sl/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fi
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/fi/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/cs
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/cs/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/no
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/no/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ca
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/_locales/ca/messages.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/128.png
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/manifest.json
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/__MACOSX
/etc/skel/.config/google-chrome/Default/Extensions/pjkljhegncpnkpknbcohdijeoejaedia/7_0/__MACOSX/_locales
/etc/skel/.config/google-chrome/Default/Network Action Predictor
/etc/skel/.config/google-chrome/Default/History Provider Cache
/etc/skel/.config/google-chrome/Default/databases
/etc/skel/.config/google-chrome/Default/databases/Databases.db
/etc/skel/.config/google-chrome/PepperFlash
/etc/skel/.config/google-chrome/Safe Browsing Download Whitelist
/etc/skel/.config/update-notifier
/etc/skel/.config/yelp
------------------------------------------------------
lsb-release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
------------------------------------------------------
remastersys version info
REMASTERSYSVERSION="3.0.1-1"
 
------------------------------------------------------
ISOTMP info
/media/isobuildpart/remastersys/ISOTMP:
total 20
drwxr-xr-x 2 root root 4096 2012-02-13 11:31 casper
drwxr-xr-x 2 root root 4096 2012-02-13 11:30 install
drwxr-xr-x 2 root root 4096 2012-02-13 11:30 isolinux
drwxr-xr-x 2 root root 4096 2012-02-13 11:30 preseed
-rw-r--r-- 1 root root  197 2012-02-13 11:30 README.diskdefines

/media/isobuildpart/remastersys/ISOTMP/casper:
total 699484
-rw-r--r-- 1 root root     39810 2012-02-13 11:30 filesystem.manifest
-rw-r--r-- 1 root root     39778 2012-02-13 11:30 filesystem.manifest-desktop
-rw-r--r-- 1 root root 691585024 2012-02-13 11:35 filesystem.squashfs
-rw-r--r-- 1 root root  19961351 2012-02-13 11:31 initrd.gz
-rw-r--r-- 1 root root       197 2012-02-13 11:30 README.diskdefines
-rw-r--r-- 1 root root   4632128 2012-02-13 11:31 vmlinuz

/media/isobuildpart/remastersys/ISOTMP/install:
total 176
-rw-r--r-- 1 root root 176764 2012-02-13 11:30 memtest

/media/isobuildpart/remastersys/ISOTMP/isolinux:
total 604
-rw-r--r-- 1 root root  24576 2012-02-13 11:30 isolinux.bin
-rw-r--r-- 1 root root    898 2012-02-13 11:30 isolinux.cfg
-rwxr-xr-x 1 root root 429403 2012-02-13 11:30 splash.png
-rw-r--r-- 1 root root 155792 2012-02-13 11:30 vesamenu.c32

/media/isobuildpart/remastersys/ISOTMP/preseed:
total 4
-rwxr-xr-x 1 root root 212 2012-02-13 11:30 custom.seed
------------------------------------------------------
/media/isobuildpart/remastersys/tmpusers info
user
------------------------------------------------------
Command-line options = dist
------------------------------------------------------
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Removing remastersys-firstboot from system startup
Making disk compatible with Ubuntu Startup Disk Creator.
Creating md5sum.txt for the livecd/dvd
Creating luvitsblacklabel-2-11-2012.iso in /media/isobuildpart/remastersys
Creating luvitsblacklabel-2-11-2012.iso.md5 in /media/isobuildpart/remastersys
/media/isobuildpart/remastersys/luvitsblacklabel-2-11-2012.iso which is 685M in size is ready to be burned or tested in a virtual machine.
```
.

---

### Post by luvit on 2012-02-13
[quote=fragadelic]
Your login issue is probably due to the amount of stuff in /etc/skel.

What is the output of "sudo du -sh /etc/skel" on your original system.
[/quote]

Hi, Tony.
Thanks, I did inspect skel, but I may not have had a clear understanding. Here is the output:
```
$ sudo du -sh /etc/skel
[sudo] password for user: 
14M	/etc/skel
```

---

### Post by luvit on 2012-02-13
[quote=fragadelic]
Did you use remastersys to populate /etc/skel or did you put things there on your own?

[/quote]
i strictly used the button from the Remastersys GUI

---

### Post by luvit on 2012-02-13
[quote=fragadelic]
The only thing I see there is that it can't connect to dbus.* The other things are normal.

What happens when you try to boot up and if this is from virtual box then I won't look at it any further and you need to try it with real media.* If you have tried it with real media then I need more info from letting it fully boot up.* Hit CTRL-ALT-F1 and see what you can see from there.* If your live user is logged in, then your issue is that you have screwed something up with your login manager config and need to fix it.* Also check that you have the default session chosen properly.* These are things that have nothing to do with remastersys but rather how you setup your system.

Post results of what I asked here and I'll see if I can guide through what you need to do to fix it.

[/quote]
i understand, but i'm already using real media on a HP 8530p.
my live username lbl should not be logged-in. i did not choose an existing username. my live username is: lbl
- i'm not sure by what you mean by "check that you have the default session chosen properly".
-- i'd be happy to look into this, if you can articulate how to do so.
.
.
below is a pic of ALT F1 before I even interact with the login screen.

[img]https://lh5.googleusercontent.com/-LvZFZxpksWM/Tzma7LpPylI/AAAAAAAABQw/uAuDt6HHw40/s800/IMAG1580.jpg[/img]

---

### Post by luvit on 2012-02-13
[quote=fragadelic]
what happens if you try to create the username lbl on your normal system?

I'm wondering if it is too short.

[/quote]

i did try this earlier with longer 5 character names ( I have burned a lot of CDs over a few days, with same results).
To your point, I have done the following:

i created two administrative accounts that were 3 letters long.
abc - with no password
def - with a 6 character password.
-- both of these accounts allowed me to login.

now, here is something interesting which you may be able to answer.

1) on my installed system's login screen, i see the following;
PC name in the upperleft corner, and i scroll up and down to select a username.

2) on my live CDs login screen, i see something a little different:
My username in the upper left corner (i.e. lbl), and i have to type-in the login name prior to being prompted with a password.
That is, I always have to type lbl during my login.

hope this helps.
.

---

### Post by luvit on 2012-02-14
.
[quote=fragadelic]
If you are using lightdm, I need to see all the contents of your /etc/lightdm/* files from the system you are remastering.[/quote]

user@ubuntu8530p:/$ ls -l /etc/lightdm
total 12
-rw-r--r-- 1 root root *66 2011-10-12 10:32 lightdm.conf
-rw-r--r-- 1 root root 715 2011-09-28 03:56 unity-greeter.conf
-rw-r--r-- 1 root root 320 2011-10-07 08:41 users.conf
user@ubuntu8530p:/$ 

[color=red]**lightdm.conf**[/color]
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
```


[color=red]**unity-greeter.conf**[/color]
```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```


[color=red]**users.conf**[/color]
```
#
# User accounts configuration
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin
```

[color=red][b]Thanks, so much for your help, so far!
I see my min user id is below 1000. lol.[/b][/color]
.

---

### Post by luvit on 2012-02-14
.
[quote=fragadelic]
Those look ok.* Is there any way you can put the iso up somewhere so I can download it and take a look at it myself?
[/quote]

sent you a PM on your site with the link.
thank you, sir!
.
**edit:**
[quote=fragadelic]
Got the PM and link.* I will download it this evening if I get a chance and take a look to see what I can come up with.
[/quote]
.
**edit:**
[quote=fragadelic]
Appears as though the lbl user is being created.* It sets the live username for the host which is why you see lbl in the upper left corner.

Try this - clear out /etc/skel and do a remaster again.* Let me know if that one works.

I think the .local/share/gvfs* might be causing an issue.[/quote]

.
awe.. i cleared out skel, reburned, and the issue still exists.
lol?
.

---

### Post by luvit on 2012-02-15
.
[quote=fragadelic]
Please attach the remastersys.log from your latest remaster.
[/quote]

Here 'tis.. [http://dl.dropbox.com/u/12104470/remastersys-2-15-2012.log](http://dl.dropbox.com/u/12104470/remastersys-2-15-2012.log)
Thanks, again!
.

---

