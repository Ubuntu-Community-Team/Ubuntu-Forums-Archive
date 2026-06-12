---
title: "No administrator password prompts in LM 17.1 Mate Edition"
date: 2015-05-13
forum: MINT
---

### Post by Muhammad_Ahmad_Mujtaba on 2015-05-13
Hi, I am using Linux Mint 17.1 on my laptop machine. I have been facing issues regarding system administration access including common apps e.g. Mint Update manager, Gparted, USB Formatter, USB Image Maker - specifically all nearly those apps which on startup requires administrator access. For all those apps, no password prompt for administrator shows and app fails to start. It is annoying. If I run them from terminal under sudo command eg 
sudo gparted
Everything goes fine, it opens and I can do my work. But under GUI is quite troubling. Furthermore, If I enable ROOT and login through it then all apps work quite right but for native user - my account, apps don't accesses my restricted administrator data because of no GUI for password prompt widget or dialog.
I am using Linux Mint 17.1 Mate Edition - x64.

---

### Post by ajgreeny on 2015-05-13
As you have used sudo to open some of those GUI apps you may have now done some damage, and caused problems with file and folder ownership in your home, where everything should be owned by you.

You should never use sudo for a GUI application; if Mint is working the same way as Ubuntu you should always use **gksudo** (which you will have to install first) or if you want to stick with what you already have, use **sudo -H** not just **sudo**.

I do not know a great deal about mate except that it is a fork of gnome-2, but I am aware that it is similar to Ubuntu when using gnome-2.
Ubuntu is now moving towards a system of using pkexec policy files for root permissions of GUI apps, but for the moment let's not go down that road.

Now let's check your home and view permissions with **ls -la** in terminal to check that all is as it should be.

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-05-14
Hi, thanks for telling me safe tips. I will use gksudo from now on,

plus this is output of "**ls -la**"

```

total 544
drwxr-xr-x 92 ahmad ahmad  4096 May 14 15:33 .
drwxr-xr-x  3 root  root   4096 Apr 12 20:26 ..
drwx------  3 ahmad ahmad  4096 Feb 15 00:26 .adobe
drwxr-x---  3 ahmad ahmad  4096 Mar 15 17:17 .android
drwxr-xr-x  4 ahmad ahmad  4096 Mar 12 11:51 .AndroidStudio
drwxr-xr-x  2 ahmad ahmad  4096 Apr 22 07:01 .anyRemote
-rw-r--r--  1 ahmad ahmad    43 Apr 20 20:06 .aspell.en.prepl
-rw-r--r--  1 ahmad ahmad    22 Apr 20 20:06 .aspell.en.pws
drwxr-xr-x  3 ahmad ahmad  4096 Apr 14 13:35 .audacity-data
drwxr-xr-x  2 ahmad ahmad  4096 Apr 16 19:30 Audiobooks
drwxr-xr-x  5 ahmad ahmad  4096 Apr 14 03:00 .avast
-rw-------  1 ahmad ahmad   654 May 14 13:24 .bash_history
-rw-r--r--  1 ahmad ahmad   220 Feb 15 00:07 .bash_logout
drwxr-xr-x 30 ahmad ahmad  4096 May 14 13:06 .cache
drwxr-xr-x  6 ahmad ahmad  4096 Feb 26 01:03 .clamtk
drwxr-xr-x  3 ahmad ahmad  4096 Mar 19 12:46 .codeblocks
drwxr-xr-x  3 ahmad ahmad  4096 Mar 15 00:31 CodeBlocks
drwxr-xr-x 71 ahmad ahmad  4096 May 14 13:06 .config
drwxr-xr-x  2 ahmad ahmad  4096 Jul 10  2012 .conky
-rw-r--r--  1 ahmad ahmad  2760 Apr 16 13:49 .conkyrc
drwxr-xr-x  4 ahmad ahmad  4096 Apr 23 17:54 .copy
drwxr-xr-x  3 ahmad ahmad  4096 Apr 23 17:06 Copy
drwx------  3 ahmad ahmad  4096 Feb 15 00:14 .dbus
drwxr-xr-x  3 ahmad ahmad  4096 May 14 02:26 Desktop
-rw-------  1 ahmad ahmad    48 May 14 13:06 .dmrc
drwxr-xr-x 11 ahmad ahmad  4096 May 13 18:38 Documents
drwx------  2 ahmad ahmad  4096 Feb 20 12:22 .dosbox
drwxr-xr-x  2 ahmad ahmad  4096 Apr 21 17:15 Dosbox
drwxr-xr-x  3 ahmad ahmad  4096 May 14 13:22 Downloads
drwx------  5 ahmad ahmad  4096 Mar 11 00:39 .dropbox
drwx------  3 ahmad ahmad  4096 Mar 11 06:59 Dropbox
drwxr-xr-x  3 ahmad ahmad  4096 Feb 16 21:43 .dropbox-dist
drwxr-xr-x  9 ahmad ahmad  4096 Apr 24 19:59 EclipseWorkspace
drwx------  2 ahmad ahmad  4096 Mar 24 23:20 .elinks
drwx------  2 ahmad ahmad  4096 Mar  4 10:55 .emacs.d
drwx------  2 ahmad ahmad  4096 Apr 23 15:33 .encrypted_family_data
-rw-r--r--  1 ahmad ahmad  6737 Feb 18 23:03 .face
drwxr-xr-x  2 ahmad ahmad  4096 Mar 16 14:16 .FBReader
drwx------  2 ahmad ahmad  4096 Mar 21 20:09 .filezilla
drwxr-xr-x  3 ahmad ahmad  4096 Feb 21 20:44 .fltk
drwxr-xr-x  2 ahmad ahmad  4096 May 11 13:14 .fonts
drwxr-xr-x  3 ahmad ahmad  4096 Mar  2 23:57 .frozenbyte
drwxr-xr-x  2 ahmad ahmad  4096 Feb 20 08:29 .furiusisomount
drwxr-xr-x  4 ahmad ahmad  4096 Apr 23 14:26 Games
drwx------  4 ahmad ahmad  4096 May 14 13:06 .gconf
drwxr-xr-x  3 ahmad ahmad  4096 Apr 10 15:12 .Genymobile
drwxr-xr-x 24 ahmad ahmad  4096 Apr 16 13:27 .gimp-2.8
-rw-r-----  1 ahmad ahmad     0 May 13 22:36 .gksu.lock
drwx------  3 ahmad ahmad  4096 Feb 15 12:37 .gnome
drwx------  5 ahmad ahmad  4096 May 12 07:20 .gnome2
drwx------  2 ahmad ahmad  4096 Feb 15 00:14 .gnome2_private
drwxr-xr-x  3 ahmad ahmad  4096 Feb 27 16:08 .google
drwxr-xr-x  2 ahmad ahmad  4096 Apr 18 21:49 .gstreamer-0.10
-rw-------  1 ahmad ahmad   112 Apr 23 17:06 .gtk-bookmarks
-rw-r--r--  1 ahmad ahmad   940 Feb 27 16:20 .gtk-recordmydesktop
-rw-------  1 ahmad ahmad 68812 May 14 13:06 .ICEauthority
drwxr-xr-x  3 ahmad ahmad  4096 Apr 23 17:05 .icons
drwxr-xr-x  3 ahmad ahmad  4096 Mar  1 23:40 .java
drwx------  3 ahmad ahmad  4096 Mar  4 10:55 .kde
drwxr-xr-x  3 ahmad ahmad  4096 Apr 14 11:52 .kingsoft
drwxr-xr-x  4 ahmad ahmad  4096 May 14 13:32 .lastpass
drwx------  2 ahmad ahmad  4096 Apr 14 13:20 .links2
drwxr-xr-x  5 ahmad ahmad  4096 Feb 15 00:14 .linuxmint
drwx------  3 ahmad ahmad  4096 Feb 15 00:14 .local
drwx------  3 ahmad ahmad  4096 Feb 15 00:26 .macromedia
drwx------  8 ahmad ahmad  4096 Mar  4 21:20 Mail
drwxr-xr-x  2 ahmad ahmad  4096 Apr 17 14:56 MEGAsync
drwxr-xr-x  2 ahmad ahmad  4096 Feb 19 20:17 Miscellaneous
drwxr-xr-x  4 ahmad ahmad  4096 Feb 15 00:14 .mozilla
drwxr-xr-x  2 ahmad ahmad  4096 Mar  1 14:08 .mplayer
drwxr-xr-x  6 ahmad ahmad  4096 May 11 10:17 Music
drwxr-xr-x  7 ahmad ahmad  4096 Mar  1 23:42 .nbi
drwxr-xr-x  3 ahmad ahmad  4096 Mar  1 23:42 .netbeans
drwxr-xr-x 10 ahmad ahmad  4096 Mar 24 23:38 netbeans-8.0.2
drwxr-xr-x  3 ahmad ahmad  4096 Mar 12 22:22 NetBeansProjects
drwxr-xr-x  4 ahmad ahmad  4096 Apr 13 11:38 Operating Systems
-rw-r--r--  1 ahmad ahmad     0 May 14 15:33 output.txt
-rw-r--r--  1 ahmad ahmad   226 Feb 15 01:06 .pam_environment
drwxr-xr-x 11 ahmad ahmad  4096 May 14 02:28 Pictures
drwx------  3 ahmad ahmad  4096 Feb 15 12:37 .pki
drwxr-xr-x 14 ahmad ahmad  4096 Mar 24 15:23 .PlayOnLinux
lrwxrwxrwx  1 ahmad ahmad    37 Feb 26 00:39 PlayOnLinux's virtual drives -> /home/ahmad/.PlayOnLinux//wineprefix/
drwxr-xr-x  2 ahmad ahmad  4096 Feb 18 22:21 Podcasts
-rw-r--r--  1 ahmad ahmad   675 Feb 15 00:07 .profile
drwx------  3 ahmad ahmad  4096 Apr 11 00:53 projects
drwxr-xr-x  2 ahmad ahmad  4096 Mar 16 00:27 Public
-rw-------  1 ahmad ahmad   256 Apr 21 02:17 .pulse-cookie
drwx------  6 ahmad ahmad  4096 May 13 13:40 .purple
drwxr-xr-x  3 ahmad ahmad  4096 Apr 12 12:54 Shared Folder
drwxr-xr-x  3 ahmad ahmad  4096 Apr 16 21:41 .shutter
drwx------  7 ahmad ahmad  4096 Apr 19 22:15 .Skype
drwxr-xr-x  9 ahmad ahmad  4096 May 12 07:09 Software
-rwxr-xr-x  1 ahmad ahmad    46 Mar 27 19:44 .start-conky
drwxr-xr-x  2 ahmad ahmad  4096 Apr 21 02:27 .steam
lrwxrwxrwx  1 ahmad ahmad    30 Apr 21 02:27 .steampath -> /home/ahmad/.steam/bin32/steam
lrwxrwxrwx  1 ahmad ahmad    28 Apr 21 02:27 .steampid -> /home/ahmad/.steam/steam.pid
drwx------  8 ahmad ahmad  4096 Mar 14 12:12 .sylpheed-2.0
drwxr-xr-x  3 ahmad ahmad  4096 Mar 21 11:00 .TelegramDesktop
drwxr-xr-x  2 ahmad ahmad  4096 Feb 15 00:14 Templates
drwxr-xr-x  5 ahmad ahmad  4096 Apr 13 15:28 .themes
drwx------  4 ahmad ahmad  4096 Mar  3 17:53 .thumbnails
drwx------  4 ahmad ahmad  4096 Mar  4 20:31 .thunderbird
drwxr-xr-x  2 ahmad ahmad  4096 May 11 12:52 Torrents
drwxr-xr-x  4 ahmad ahmad  4096 Mar  9 10:00 .ViberPC
drwxr-xr-x 15 ahmad ahmad  4096 Apr 24 23:21 Videos
drwxr-xr-x  5 ahmad ahmad  4096 Apr 13 11:36 VirtualBox VMs
drwxr-xr-x  2 ahmad ahmad  4096 Mar  7 08:56 .wakeup
drwxr-xr-x  4 ahmad ahmad  4096 Apr 23 15:21 .wine
drwxr-xr-x  2 ahmad ahmad  4096 Feb 27 01:17 .winff
-rw-------  1 ahmad ahmad   129 May 14 13:06 .Xauthority
drwx------  3 ahmad ahmad  4096 Mar 25 19:27 .xchat2
-rw-r--r--  1 ahmad ahmad   587 Mar 21 20:01 .xchm
-rw-r--r--  1 ahmad ahmad    37 Mar 20 22:23 .Xmodmap
-rw-r--r--  1 ahmad ahmad 31593 May 14 15:33 .xsession-errors
drwxr-xr-x 32 ahmad ahmad  4096 May 13 21:16 Zohaib Data

```

---

