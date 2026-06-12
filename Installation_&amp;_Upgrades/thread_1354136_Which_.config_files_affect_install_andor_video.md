---
title: "Which ./config files affect install and/or video"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2009-12-13
I did a clean install of Karmic for a 2nd time. The /home was the only file backed up (using Deja Dup). The Trash folder was excluded from the backup.

The install (2nd time in 40 days), was made with a Desktop CD. The install reported no errors and ran perfectly well until I "restored" the /home.

On reboot after restore, the GUI is crazy. Alt-F2 will not open a "terminal". The upper panel cuts off all applications. Using Places to open Nautilus opens Rhythmbox instead.

Below is a list off all my /home (less the obvious, Videos, Public, Documents and any folder I created)

Of these (sorry for a long list) HOW MANY relate to controlling Gnome/Nautilus/Desktop? Can they be deleted without harming the OS? Will they recreate themselves as necessary on re-boot?

mark@Lexington-karmic-19:~$ ls -al $HOME
total 3880
drwxr-xr-x 104 mark mark   4096 2009-12-13 12:15 .
drwxr-xr-x   5 root root   4096 2009-12-13 12:03 ..
drwx------   4 mark mark   4096 2009-12-12 14:53 .adobe

-rw-r--r--   1 mark mark    188 2009-09-30 08:37 .asoundrc
-rw-r--r--   1 mark mark    188 2009-06-12 23:38 .asoundrc~
-rw-r--r--   1 mark mark   2208 2009-11-03 12:16 .asoundrc.asoundconf
drwx------   2 mark mark   4096 2009-12-12 13:53 .audacity1.3-mark
drwx------   5 mark mark   4096 2009-12-12 14:53 .audacity-data
drwx------   4 mark mark   4096 2009-12-12 14:58 backup.mozilla
drwxr-xr-x   4 mark mark   4096 2009-12-12 14:53 bandwidth
-rw-------   1 mark mark  13406 2009-12-13 12:15 .bash_history
-rw-r--r--   1 mark mark    220 2008-11-17 09:54 .bash_logout
-rw-r--r--   1 mark mark   3115 2008-11-17 09:54 .bashrc

drwxr-xr-x   6 mark mark   4096 2009-12-12 14:53 .bibus
drwxr-xr-x   4 mark mark   4096 2009-12-12 14:55 bin
-rw-r--r--   1 mark mark    289 2009-02-07 16:28 .bitpim
drwx------   5 mark mark   4096 2009-12-12 14:53 .bitpim-files

drwx------   9 mark mark   4096 2009-12-11 14:47 .cache
drwx------   2 mark mark   4096 2009-12-12 14:53 .checkbox
drwx------   3 mark mark   4096 2009-12-11 16:34 .compiz
drwxr-xr-x  28 mark mark   4096 2009-12-12 15:37 .config

drwx------   2 mark mark   4096 2009-12-09 16:18 .cups
drwx------   3 mark mark   4096 2009-12-12 14:53 .dbus
drwxr-xr-x   8 mark mark   4096 2009-12-12 15:03 ddtmp
drwxrwxrwx  17 mark mark   4096 2009-12-12 19:42 Desktop

-rw-r--r--   1 mark mark     59 2009-12-13 11:55 .dmrc
-rw-r--r--   1 mark mark     28 2009-11-16 10:11 .dmrc.ENCV3U
drwxr-xr-x  67 mark mark  12288 2009-12-12 15:01 Documents
drwx------   2 mark mark   4096 2009-12-12 14:53 Downloads
drwxrwxrwx   2 mark mark   4096 2009-12-12 14:53 .dumps
drwx------   4 mark mark   4096 2009-12-12 14:53 .dvdcss
drwxr-x---   2 mark mark   4096 2009-12-12 14:53 .easytag
-rw-------   1 mark mark     16 2008-11-17 10:03 .esd_auth

drwxr-xr-x   9 mark mark   4096 2009-12-12 14:58 .evolution
-rw-r--r--   1 mark mark    167 2009-11-08 14:15 examples.desktop

drwxr-xr-x   2 mark mark   4096 2009-12-12 14:53 .fontconfig

drwxr-xr-x   3 mark mark   4096 2009-12-12 14:53 .freeguide
-rw-r--r--   1 mark mark     59 2009-12-11 18:20 .gammurc
drwx------   5 mark mark   4096 2009-12-13 11:59 .gconf
drwx------   2 mark mark   4096 2009-12-13 12:17 .gconfd

drwx------  22 mark mark   4096 2009-12-12 14:53 .gimp-2.6
-rw-r-----   1 mark mark      0 2009-12-13 12:02 .gksu.lock
drwx------  18 mark mark   4096 2009-12-13 12:12 .gnome2
drwx------   2 mark mark   4096 2008-11-17 10:03 .gnome2_private
drwx------   2 mark mark   4096 2009-12-13 11:56 .gnupg
drwx------   6 mark mark   4096 2009-12-12 14:59 .google
drwxr-xr-x  10 mark mark   4096 2009-12-12 15:02 google-earth
drwxr-xr-x   3 mark mark   4096 2009-12-12 14:53 .gourmet
drwx------   2 mark mark   4096 2009-12-12 14:01 .gpilotd
-rw-r--r--   1 mark mark      4 2009-11-30 15:45 .gpilotd.pid
drwxr-xr-x   2 mark mark   4096 2009-12-12 15:14 .gstreamer-0.10
-rw-r--r--   1 mark mark    104 2009-12-13 12:08 .gtk-bookmarks
dr-x------   2 mark mark      0 2009-12-13 11:56 .gvfs

drwxr-----   2 mark mark   4096 2009-12-12 14:53 .hplip
-rw-r--r--   1 mark mark    458 2009-10-13 17:55 .huludesktop
-rw-------   1 mark mark  76185 2009-12-13 11:56 .ICEauthority
drwxr-xr-x   2 mark mark   4096 2008-11-18 12:39 .icons

drwx------   3 mark mark   4096 2009-12-12 14:54 .java
drwx------   2 mark mark   4096 2009-12-12 14:02 .kbluetooth4
drwx------   3 mark mark   4096 2009-12-12 14:54 .kde
-rw-r--r--   1 mark mark   3003 2009-02-28 14:05 .kinorc
drwx------   2 mark mark   4096 2009-12-12 14:53 .kompozer

-rw-r--r--   1 mark mark   1698 2009-02-04 02:30 le-web.key
drwx------   3 mark mark   4096 2009-12-12 14:53 .Livestation
drwx------   3 mark mark   4096 2009-12-12 14:58 .local
drwx------   3 mark mark   4096 2009-12-12 14:56 .macromedia
-rw-r--r--   1 mark mark   3146 2008-12-14 09:07 .mailcap
drwx------   3 mark mark   4096 2009-12-12 14:53 .mcop
-rw-------   1 mark mark     31 2009-03-02 18:05 .mcoprc
drwx------   3 mark mark   4096 2009-12-12 14:53 .mission-control
drwx------   4 mark mark   4096 2009-12-13 12:03 .mozilla
drwx------   3 mark mark   4096 2009-12-11 12:48 .mozilla-thunderbird

drwxr-xr-x   2 mark mark  24576 2009-12-12 15:01 .nautilus
-rw-r--r--   1 mark mark   1052 2009-12-07 14:29 .nvidia-settings-rc
drwxr-xr-x   3 mark mark   4096 2009-12-12 14:56 .openoffice.org
drwx------   2 mark mark   4096 2009-12-12 14:02 .openoffice.org-20090918
-rw-r--r--   1 mark mark     74 2009-11-02 12:22 .padminrc

drwx------   2 mark mark   4096 2009-12-12 14:53 .pdfedit
drwxr-xr-x   2 mark mark   4096 2009-12-12 14:53 pdf-files

drwxr-xr-x   3 mark mark   4096 2009-12-12 14:53 Picasa
-rw-r--r--   1 mark mark     74 2009-09-16 07:59 Picasa.ini
drwxr-xr-x   4 mark mark   4096 2009-12-12 14:57 .picasa renamed

drwx------   3 mark mark   4096 2009-12-12 14:53 .pki

-rw-r--r--   1 mark mark     37 2009-05-09 12:11 .printer-groups.xml
-rw-r--r--   1 mark mark    675 2008-11-17 09:54 .profile

drwx------   2 mark mark   4096 2009-12-13 11:56 .pulse
drwxr-xr-x   4 mark mark   4096 2009-12-12 14:53 pulse-backup
-rw-------   1 mark mark    256 2008-11-17 10:03 .pulse-cookie
drwx------   2 mark mark   4096 2009-12-12 14:53 .qt
-rw-------   1 mark mark  45327 2009-12-12 15:34 .recently-used
-rw-------   1 mark mark  25157 2009-12-12 19:42 .recently-used.xbel
-rw-r--r--   1 mark mark      0 2009-11-03 15:48 .recently-used.xbel.1YJW2U
-rw-r--r--   1 mark mark 327680 2009-05-08 18:39 .recently-used.xbel.2G5ITU
-rw-r--r--   1 mark mark 300574 2009-10-10 20:47 .recently-used.xbel.3M1L1U
-rw-r--r--   1 mark mark 336249 2009-05-10 15:30 .recently-used.xbel.B2SOTU
-rw-r--r--   1 mark mark 372736 2009-10-02 13:30 .recently-used.xbel.EG680U
-rw-r--r--   1 mark mark 384009 2009-07-20 21:04 .recently-used.xbel.FZ1JXU
-rw-r--r--   1 mark mark 296083 2009-11-04 12:15 .recently-used.xbel.H6CC3U
-rw-r--r--   1 mark mark 364544 2009-10-05 11:08 .recently-used.xbel.L78I1U
-rw-r--r--   1 mark mark 300574 2009-10-10 20:47 .recently-used.xbel.RMV21U
-rw-r--r--   1 mark mark 336249 2009-05-10 15:30 .recently-used.xbel.VTWWTU
-rw-r--r--   1 mark mark 134668 2009-05-29 20:46 .recently-used.xbel.Y2FYUU
-rw-r--r--   1 mark mark    237 2009-12-03 08:45 .registry

drwxrwx---   3 mark mark   4096 2009-12-12 14:53 .sane
drwx------   2 mark mark   4096 2009-12-12 14:53 .screenlets
drwx------   3 mark mark   4096 2009-12-12 14:53 .Skype
drwx------   4 mark mark   4096 2009-12-12 14:53 Skype4Py-1.0.31.0
drwxr-xr-x   2 mark mark   4096 2009-12-12 14:53 skysentials-1.0.1
drwxr-xr-x   3 mark mark   4096 2009-12-12 15:01 sl
drwx------   2 mark mark   4096 2009-02-15 13:10 .ssh

drwx------   3 mark mark   4096 2009-12-12 14:53 .streamtuner
-rw-r--r--   1 mark mark      0 2008-11-17 10:06 .sudo_as_admin_successful

drwxr-xr-x   2 mark mark   4096 2008-11-18 12:39 .themes
drwx------   4 mark mark   4096 2009-12-11 13:46 .thumbnails
drwx------   4 mark mark   4096 2009-12-12 15:02 .tvbrowser

drwxr-xr-x   2 mark mark   4096 2009-12-12 14:53 .update-manager-core
drwx------   2 mark mark   4096 2009-12-12 14:53 .update-notifier
drwx------   2 mark mark   4096 2009-12-12 14:53 .ure

-rw-------   1 mark mark   1471 2009-02-26 16:03 .viminfo
drwx------   4 mark mark   4096 2009-12-12 14:53 .wally
-rw-r--r--   1 mark mark    589 2009-11-21 09:05 .Wammu
drwx------   2 mark mark   4096 2009-12-12 14:03 .wapi
drwxr-xr-x   4 mark mark   4096 2009-12-12 15:00 .wine
-rw-------   1 mark mark    123 2009-11-08 11:12 .Xauthority
drwx------   2 mark mark   4096 2009-12-12 14:53 .xine
drwxr-xr-x   2 mark mark   4096 2009-12-12 14:53 .xinput.d
-rw-r--r--   1 mark mark    129 2009-03-29 17:17 .xscreensaver-getimage.cache
-rw-------   1 mark mark  11002 2009-12-13 12:17 .xsession-errors
-rw-------   1 mark mark   8947 2009-12-12 19:42 .xsession-errors.old

---

