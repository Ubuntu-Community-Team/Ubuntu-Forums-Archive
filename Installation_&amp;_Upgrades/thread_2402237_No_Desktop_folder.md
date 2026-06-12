---
title: "No Desktop folder"
date: 2018-09-27
forum: Installation &amp; Upgrades
---

### Post by trash1464 on 2018-09-27
After a clean install of 18.04.1 LTS, I now longer have a desktop folder in Nautilus only a Home folder. Everything in the Home folder is also duplicated on the actual desktop. Is this the new default configuration for Gnome?

---

### Post by ajgreeny on 2018-09-27
No it's not.

Somehow you seem to have the complete content of /home/user in your Desktop folder.

Let's see the output of ```
ls -la
ls -la Desktop
``` to see more details, and then once we know, we can hopefully tell you what to move to where.

---

### Post by trash1464 on 2018-09-27
> **ajgreeny said:**
> No it's not.

Somehow you seem to have the complete content of /home/user in your Desktop folder.

Let's see the output of ```
ls -la
ls -la Desktop
``` to see more details, and then once we know, we can hopefully tell you what to move to where.

```
rich@rich-Linux:~$ ls -la
total 14688
drwxrwxrwx 100 rich rich    12288 Sep 27 11:06  .
drwxr-xr-x   4 root root     4096 Apr 24 01:34  ..
drwxr-xr-x   5 rich rich     4096 Feb  6  2010  .adobe
drwxrwxr-x  12 rich rich     4096 Aug 17  2016  .AfterShot
drwxrwxr-x  11 rich rich     4096 Jun 14  2015  .AfterShotPro
drwxrwxr-x  12 rich rich     4096 Aug 17  2016 '.AfterShot Pro 3'
-rw-rw-r--   1 rich rich      262 Feb  2  2018  .apport-ignore.xml
drwx------   2 rich rich     4096 Mar 24  2018  .aptitude
-rw-rw-r--   1 rich rich      163 Jun 24  2017  .asunder
-rw-rw-r--   1 rich rich        9 Jun 24  2017  .asunder_album_artist
-rw-rw-r--   1 rich rich        4 Jun 24  2017  .asunder_album_genre
-rw-rw-r--   1 rich rich       61 Jun 24  2017  .asunder_album_title
drwxr-xr-x   3 rich rich     4096 May 13  2014  .avidemux
drwxrwxr-x  10 rich rich     4096 Apr 23  2013  .azureus
-rw-------   1 rich rich    12164 Sep 27 14:30  .bash_history
-rw-r--r--   1 rich rich      220 Sep 20 16:36  .bash_logout
-rw-r--r--   1 rich rich     3771 Sep 20 16:36  .bashrc
drwx------  31 rich rich     4096 Sep 27 10:31  .cache
drwxr-xr-x   8 rich rich     4096 Sep 24 15:25  .cddb
drwxr-xr-x   3 rich rich     4096 Jun 24  2017  .cddbslave
drwxr-xr-x   6 rich rich     4096 Nov  5  2016  .clamtk
drwx------   3 rich rich     4096 Mar 29  2013  .compiz
drwxr-xr-x   3 rich rich     4096 Oct 13  2011  .compiz-1
drwxr-xr-x  84 rich rich     4096 Sep 27 10:15  .config
drwxr-xr-x   2 rich rich     4096 Jul 25  2009  .cups
drwxr-xr-x   3 rich rich     4096 Jul 25  2009  .dbus
-rw-r--r--   1 rich rich       94 Jul 13  2015  .dmrc
drwxrwxrwx  49 rich rich     4096 Sep 27 13:01  Documents
drwxr-xr-x   2 rich rich     4096 Nov 14  2009  .DownloadManager
drwx------   2 rich rich     4096 Sep 26 16:09  Downloads
drwx------   5 rich rich     4096 Jan 16  2017  .dropbox
drwxr-xr-x   3 rich rich     4096 Jan 10  2017  .dropbox-dist
drwxr-xr-x  88 rich rich     4096 Jun 20  2011  .dvdcss
drwxrwxr-x   2 rich rich     4096 Apr 25  2013  .electricsheep
drwxr-xr-x   5 rich rich     4096 Aug 14 15:32  .enigma
-rw-r--r--   1 rich rich      978 Aug 14 15:32  .enigmarc.xml
-rw-rw----   1 rich rich       16 Jul  6  2012  .esd_auth
-rw-r--r--   1 rich rich    15591 Oct 20  2012  .face
drwxr-xr-x   2 rich rich     4096 Oct  7  2016  .filezilla
drwx------   3 rich rich     4096 Feb 25  2017  .fltk
drwxr-xr-x   2 rich rich     4096 Oct 20  2010  .foffrc
drwxr-xr-x   2 rich rich    20480 Mar 29  2013  .fontconfig
-rw-rw-r--   1 rich rich      453 Jan 29  2017  .FSPViewer
drwxr-xr-x   5 rich rich     4096 Sep 27 12:16  .gconf
drwxr-xr-x   2 rich rich     4096 Oct 23  2012  .gconfd
drwxr-xr-x   4 rich rich     4096 Jul 26  2009  .gegl-0.0
drwxr-xr-x   3 rich rich     4096 Feb 10  2011  .gftp
drwxr-xr-x  22 rich rich     4096 Aug 23  2012  .gimp-2.6
drwxr-xr-x  24 rich rich     4096 Sep 23 15:58  .gimp-2.8
-rw-rw----   1 rich rich        0 Feb 24  2015  .gksu.lock
drwx------   3 rich rich     4096 Jul 11  2015  .gnome
drwxr-xr-x  11 rich rich     4096 May 17  2017  .gnome2
drwxr-xr-x   2 rich rich     4096 Jul 25  2009  .gnome2_private
drwxr-xr-x   3 rich rich     4096 Aug  2 15:52  .gnupg
drwxr-xr-x   3 rich rich     4096 Aug 23  2011  .google
drwxr-xr-x   6 rich rich     4096 Jan 11  2018  .googleearth
-rw-rw----   1 rich rich       54 Mar  2  2013  .goutputstream-04SPTW
-rw-rw----   1 rich rich       54 Nov 15  2012  .goutputstream-088RNW
-rw-rw----   1 rich rich       54 Mar 29  2013  .goutputstream-0CWQUW
-rw-rw----   1 rich rich       54 Jan 30  2013  .goutputstream-1A4PRW
-rw-rw----   1 rich rich       54 Dec 19  2012  .goutputstream-1OVUPW
-rw-rw----   1 rich rich       54 Dec  3  2012  .goutputstream-1V0TOW
-rw-rw----   1 rich rich       54 Feb 17  2013  .goutputstream-22NWSW
-rw-rw----   1 rich rich       54 Feb  6  2013  .goutputstream-2DGESW
-rw-rw----   1 rich rich       54 Mar 30  2013  .goutputstream-2E33UW
-rw-rw----   1 rich rich       54 Apr  9  2013  .goutputstream-2KN4UW
-rw-rw----   1 rich rich       54 Nov  6  2012  .goutputstream-2L4DNW
-rw-rw----   1 rich rich       54 Apr  4  2013  .goutputstream-2NKLUW
-rw-rw----   1 rich rich       54 Apr 24  2013  .goutputstream-2V8QVW
-rw-rw----   1 rich rich       54 Mar 26  2013  .goutputstream-2YYMUW
-rw-rw----   1 rich rich       54 Mar  8  2013  .goutputstream-338KTW
-rw-rw----   1 rich rich       54 Apr  7  2013  .goutputstream-39JJVW
-rw-rw----   1 rich rich       54 Mar 31  2013  .goutputstream-3H6IUW
-rw-rw----   1 rich rich       54 Dec 30  2012  .goutputstream-3ZMDQW
-rw-rw----   1 rich rich       54 Nov 21  2012  .goutputstream-40YSNW
-rw-rw----   1 rich rich       54 Jan 26  2013  .goutputstream-43UORW
-rw-rw----   1 rich rich       54 Apr  6  2013  .goutputstream-47E4UW
-rw-rw----   1 rich rich       54 Oct 25  2012  .goutputstream-4OSTMW
-rw-rw----   1 rich rich       54 Nov 22  2012  .goutputstream-58MWNW
-rw-rw----   1 rich rich       54 Mar 25  2013  .goutputstream-5POWUW
-rw-rw----   1 rich rich       54 Apr  2  2013  .goutputstream-5XWIUW
-rw-rw----   1 rich rich       54 Mar 25  2013  .goutputstream-6HCRUW
-rw-rw----   1 rich rich       54 Mar  7  2013  .goutputstream-6R8LTW
-rw-rw----   1 rich rich       54 Feb  7  2013  .goutputstream-7HICSW
-rw-rw----   1 rich rich       54 Dec 23  2012  .goutputstream-7SNPPW
-rw-rw----   1 rich rich       54 Oct 31  2012  .goutputstream-7YSCNW
-rw-rw----   1 rich rich       54 Feb 26  2013  .goutputstream-8HG4SW
-rw-rw----   1 rich rich       54 Mar 12  2013  .goutputstream-9FYMTW
-rw-rw----   1 rich rich       54 Mar 28  2013  .goutputstream-9NXJUW
-rw-rw----   1 rich rich       54 Feb  6  2013  .goutputstream-9OM6RW
-rw-rw----   1 rich rich       54 Apr 21  2013  .goutputstream-A2Y3VW
-rw-rw----   1 rich rich       54 Jan 17  2013  .goutputstream-ABVZQW
-rw-rw----   1 rich rich       54 Oct 29  2012  .goutputstream-AVXGMW
-rw-rw----   1 rich rich       54 Dec  4  2012  .goutputstream-B88DOW
-rw-rw----   1 rich rich       54 Jan 21  2013  .goutputstream-BC68QW
-rw-rw----   1 rich rich       54 Mar 19  2013  .goutputstream-C1NDUW
-rw-rw----   1 rich rich       54 Jan 22  2013  .goutputstream-C2NXQW
-rw-rw----   1 rich rich       54 Nov 14  2012  .goutputstream-C307NW
-rw-rw----   1 rich rich       54 Feb 19  2013  .goutputstream-C6WRSW
-rw-rw----   1 rich rich       54 Mar 25  2013  .goutputstream-CY4VUW
-rw-rw----   1 rich rich        0 Oct 20  2012  .goutputstream-CZYWMW
-rw-rw----   1 rich rich       54 Feb 12  2013  .goutputstream-D09ESW
-rw-rw----   1 rich rich       54 Mar 26  2013  .goutputstream-DU2OUW
-rw-rw----   1 rich rich       54 Apr 12  2013  .goutputstream-DW7DVW
-rw-rw----   1 rich rich       54 Feb 12  2013  .goutputstream-DZR3RW
-rw-rw----   1 rich rich       54 Feb 27  2013  .goutputstream-E1SYSW
-rw-rw----   1 rich rich       54 Dec 19  2012  .goutputstream-E39HPW
-rw-rw----   1 rich rich       54 Jan 21  2013  .goutputstream-EBR4QW
-rw-rw----   1 rich rich       54 Jan 28  2013  .goutputstream-EJSYRW
-rw-rw----   1 rich rich       54 Dec 29  2012  .goutputstream-ENRZPW
-rw-rw----   1 rich rich       54 Mar 29  2013  .goutputstream-F5DSUW
-rw-rw----   1 rich rich       54 Dec  5  2012  .goutputstream-F7AWOW
-rw-rw----   1 rich rich       54 Apr  1  2013  .goutputstream-F8RHUW
-rw-rw----   1 rich rich       54 Jan 14  2013  .goutputstream-FFI0QW
-rw-rw----   1 rich rich       54 Dec 15  2012  .goutputstream-GAB4OW
-rw-rw----   1 rich rich       54 Mar 18  2013  .goutputstream-GJRVTW
-rw-rw----   1 rich rich       54 Nov 30  2012  .goutputstream-GN7KOW
-rw-rw----   1 rich rich       54 Apr  9  2013  .goutputstream-H0FMVW
-rw-rw----   1 rich rich       54 Mar 25  2013  .goutputstream-H0HUUW
-rw-rw----   1 rich rich       54 Mar 25  2013  .goutputstream-H3KUUW
-rw-rw----   1 rich rich       54 Nov 28  2012  .goutputstream-HP19NW
-rw-rw----   1 rich rich       54 Dec 10  2012  .goutputstream-I6LXOW
-rw-rw----   1 rich rich       54 Feb  6  2013  .goutputstream-IGTASW
-rw-rw----   1 rich rich        0 Dec 28  2012  .goutputstream-IM9JPW
-rw-rw----   1 rich rich       54 Apr  8  2013  .goutputstream-ISMLVW
-rw-rw----   1 rich rich       54 Mar 10  2013  .goutputstream-IYNATW
-rw-rw----   1 rich rich       54 Dec  6  2012  .goutputstream-J1AHPW
-rw-rw----   1 rich rich       54 Feb 22  2013  .goutputstream-KLR7SW
-rw-rw----   1 rich rich       54 Jan 27  2013  .goutputstream-KMKNRW
-rw-rw----   1 rich rich       54 Apr 11  2013  .goutputstream-KQOBVW
-rw-rw----   1 rich rich       54 Apr 23  2013  .goutputstream-KSYAWW
-rw-rw----   1 rich rich       54 Apr 24  2013  .goutputstream-L2G2VW
-rw-rw----   1 rich rich       54 Apr 15  2013  .goutputstream-LTBMVW
-rw-rw----   1 rich rich       54 Dec 16  2012  .goutputstream-MG6ZOW
-rw-rw----   1 rich rich       54 Feb 23  2013  .goutputstream-MKWYSW
-rw-rw----   1 rich rich       54 Feb  2  2013  .goutputstream-MT2DRW
-rw-rw----   1 rich rich       54 Dec  1  2012  .goutputstream-N9CAOW
-rw-rw----   1 rich rich       54 Mar 13  2013  .goutputstream-OGGBUW
-rw-rw----   1 rich rich       54 Apr  3  2013  .goutputstream-OL2NUW
-rw-rw----   1 rich rich       54 Nov 12  2012  .goutputstream-PCEONW
-rw-rw----   1 rich rich       54 Nov  4  2012  .goutputstream-PE6ANW
-rw-rw----   1 rich rich       54 Nov 26  2012  .goutputstream-PLBAOW
-rw-rw----   1 rich rich       54 Nov 30  2012  .goutputstream-PMXEOW
-rw-rw----   1 rich rich       54 Feb  9  2013  .goutputstream-QR1ZRW
-rw-rw----   1 rich rich       54 Feb  4  2013  .goutputstream-REYGSW
-rw-rw----   1 rich rich       54 Feb 24  2013  .goutputstream-RGV6SW
-rw-rw----   1 rich rich       54 Nov  9  2012  .goutputstream-S4E8MW
-rw-rw----   1 rich rich       54 Jan 12  2013  .goutputstream-SVBYQW
-rw-rw----   1 rich rich       54 Dec 20  2012  .goutputstream-TDRRPW
-rw-rw----   1 rich rich       54 Dec  2  2012  .goutputstream-TV1AOW
-rw-rw----   1 rich rich       54 Feb  1  2013  .goutputstream-U41SRW
-rw-rw----   1 rich rich       54 Mar 11  2013  .goutputstream-U4EGTW
-rw-rw----   1 rich rich       54 Feb  2  2013  .goutputstream-UV3ORW
-rw-rw----   1 rich rich       54 Mar 19  2013  .goutputstream-VECDUW
-rw-rw----   1 rich rich       54 Apr  4  2013  .goutputstream-VFEOUW
-rw-rw----   1 rich rich       54 Apr 10  2013  .goutputstream-VHN7UW
-rw-rw----   1 rich rich       54 Mar 18  2013  .goutputstream-VOS8TW
-rw-rw----   1 rich rich       54 Dec 14  2012  .goutputstream-VSC2OW
-rw-rw----   1 rich rich       54 Apr  5  2013  .goutputstream-VVBTUW
-rw-rw----   1 rich rich       54 Feb  6  2013  .goutputstream-WL2GSW
-rw-rw----   1 rich rich        0 Oct 20  2012  .goutputstream-WPQLMW
-rw-rw----   1 rich rich       54 Apr  2  2013  .goutputstream-WRSQUW
-rw-rw----   1 rich rich       54 Apr 19  2013  .goutputstream-WVGTVW
-rw-rw----   1 rich rich       54 Nov 11  2012  .goutputstream-WZYQNW
-rw-rw----   1 rich rich       54 Apr  8  2013  .goutputstream-XS1GVW
-rw-rw----   1 rich rich       54 Dec 11  2012  .goutputstream-XU0EPW
-rw-rw----   1 rich rich       54 Jan 24  2013  .goutputstream-XXLVRW
-rw-rw----   1 rich rich       54 Apr 11  2013  .goutputstream-XZUBVW
-rw-rw----   1 rich rich       54 Mar  9  2013  .goutputstream-Y10GTW
-rw-rw----   1 rich rich       54 Dec 27  2012  .goutputstream-Y26WPW
-rw-rw----   1 rich rich       54 Apr  1  2013  .goutputstream-Y4VHUW
-rw-rw----   1 rich rich       54 Jan 31  2013  .goutputstream-YA1GRW
-rw-rw----   1 rich rich       54 Feb 12  2013  .goutputstream-YD8ASW
-rw-rw----   1 rich rich       54 Nov 23  2012  .goutputstream-YJ6MOW
-rw-rw----   1 rich rich       54 Nov 27  2012  .goutputstream-YJUEOW
-rw-rw----   1 rich rich       54 Oct 26  2012  .goutputstream-YMEHMW
-rw-rw----   1 rich rich       54 Feb 18  2013  .goutputstream-YNMSSW
-rw-rw----   1 rich rich       54 Dec 19  2012  .goutputstream-YOYJPW
-rw-rw----   1 rich rich       54 Nov 15  2012  .goutputstream-YZGRNW
-rw-rw----   1 rich rich       54 Apr 11  2013  .goutputstream-ZBXDVW
-rw-rw----   1 rich rich       54 Feb 13  2013  .goutputstream-ZLNDSW
drwx------   2 rich rich     4096 Mar  5  2017  .gphoto
drwxr-xr-x   2 rich rich     4096 May 25  2015  .gstreamer-0.10
-rw-rw-r--   1 rich rich       58 Oct  6  2012  .gtk-bookmarks
-rw-rw-r--   1 rich rich      181 Aug 14  2012  .gtk-custom-papers
-rw-rw-r--   1 rich rich      939 Feb  9  2016  .gtk-recordmydesktop
-rw-rw-r--   1 rich rich     4090 Dec 22  2016  .hugin
drwxrwxr-x   2 rich rich     4096 Dec  8  2016  .hugindata
-rw-rw----   1 rich rich   355140 Sep 26 15:38  .ICEauthority
drwxr-xr-x   3 rich rich     4096 May  9  2010  .icedteaplugin
drwxr-xr-x   4 rich rich     4096 Dec 13  2013  .icons
-rw-rw-r--   1 rich rich       21 Jun  8 16:15  .iscan_preference
drwxr-xr-x   5 rich rich     4096 Jun  8  2016  .java
drwxr-xr-x   4 rich rich     4096 Dec  5  2016  .kde
drwxr-xr-x   3 rich rich     4096 Jul 22  2011  .libreoffice
-rw-r--r--   1 rich rich        0 Aug 29  2016  .lightworks.thereCanBeOnlyOne
drwxr-xr-x   3 rich rich     4096 Jul 25  2009  .local
drwxr-xr-x   7 rich rich     4096 Sep 15  2009  .lprof
drwxrwxr-x   6 rich rich     4096 Feb 28  2013  .luckyBackup
drwxr-xr-x   3 rich rich     4096 Mar  9  2013  .macromedia
drwxr-xr-x   2 rich rich     4096 Aug 29  2016  .MCTranscodingSDK
drwxr-xr-x   3 rich rich     4096 Feb  8  2010  .mission-control
drwxr-xr-x   5 rich rich     4096 Nov 17  2017  .mozilla
lrwxrwxrwx   1 rich rich       23 Sep 20 17:30  .mozilla-thunderbird -> /home/rich/.thunderbird
drwxrwxr-x   2 rich rich     4096 Apr 25  2013  .mplayer
drwxr-xr-x   2 rich rich     4096 Oct 23  2012  .nautilus
drwxr-xr-x   3 rich rich     4096 Aug  6  2009  .netx
drwx------   2 rich rich     4096 May  9  2013  .noiseninja
drwx------   4 rich rich     4096 May  9  2013  .nv
drwxrwxr-x   2 rich rich     4096 Apr 21  2013  .nvidia
-rw-rw-r--   1 rich rich      491 Oct 27  2016  .nvidia-settings-rc
drwxr-x---   6 rich rich     4096 Feb  7  2018  .openshot
drwxrwxr-x   9 rich rich     4096 May 12  2016  .openshot_qt
drwxr-xr-x   6 rich rich     4096 Apr 27 19:11  .pan2
drwxrwxr-x   2 rich rich     4096 Oct 24  2012  .pdfedit
drwxr-xr-x   3 rich rich     4096 Jul 21  2011  .pki
-rw-r--r--   1 rich rich      807 Sep 20 16:36  .profile
-rw-rw-r--   1 rich rich        2 Dec 22  2016  .ptbt1
drwx------   2 rich rich    12288 Sep 25 17:22  .pulse
-rw-rw----   1 rich rich      256 Jul  4  2012  .pulse-cookie
drwx------   2 rich rich     4096 Nov  2  2017  .putty
drwxr-xr-x   2 rich rich     4096 Oct 25  2011  .pypar2
drwxr-xr-x   2 rich rich     4096 Oct 24  2012  .qt
drwxr-xr-x   2 rich rich     4096 Sep 15  2009  .quiteinsane_gimp_plugin
drwxrwxr-x   2 rich rich     4096 Nov  6  2016  .redeclipse
drwx------   2 rich rich     4096 Jan 14  2018  .remmina
drwxr-xr-x   2 rich rich     4096 Aug  1  2009  .rubyripper
drwxrwxr-x   4 rich rich     4096 Oct  8  2015  .sabnzbd
drwxr-xr-x   3 rich rich     4096 Jul 25  2009  .sane
-rw-rw-r--   1 rich rich      409 Sep 23 15:53  .sane-pygtk.cfg
drwxr-xr-x   2 rich rich     4096 Aug 24  2010  .scim
drwxrwxr-x   3 rich rich     4096 Jun 29 10:17  .shutter
drwx------   6 rich rich     4096 Mar 24  2013  .Skype
drwxr-xr-x  20 rich rich     4096 Sep 26 16:51  snap
drwxr-xr-x   2 rich rich     4096 Jul 28  2009  .ssh
-rw-rw-r--   1 rich rich        0 Oct 20  2012  .sudo_as_admin_successful
drwxrwxr-x   3 rich rich     4096 Apr 23  2013  .swt
drwxr-xr-x   5 rich rich     4096 Oct 20  2010  .themes
drwx------   3 rich rich     4096 Sep 21 15:41  .thumbnails
drwxr-xr-x   4 rich rich     4096 Jul 22  2011  .thunderbird
drwxr-xr-x   2 rich rich     4096 Jul 28  2009  .tsclient
drwxr-xr-x   2 rich rich     4096 Mar 11  2017  .tuxpaint
drwxr-xr-x   2 rich rich     4096 Jul 25  2009  .update-manager-core
drwxr-xr-x   2 rich rich     4096 Jul 21  2011  .update-notifier
drwxr-xr-x   4 rich rich     4096 Aug 24 06:46  .VirtualBox
lrwxrwxrwx   1 rich rich       27 Sep 20 17:46  Vitals -> /home/rich/Documents/Vitals
-rwxr-xr-x   1 rich rich 13516547 Sep 26 00:12  vuescan
drwxr-xr-x   2 rich rich     4096 Sep 27 13:01  .vuescan
drwxr-xr-x   2 rich rich     4096 Sep 27 11:06  Vuescan
-rw-rw-r--   1 rich rich       96 Jul  5  2012  .vuescanrc
drwxr-xr-x   2 rich rich     4096 Jul 26  2009  .w3m
drwxr-xr-x   2 rich rich     4096 Apr  8  2010  .wapi
-rw-rw-r--   1 rich rich      176 Jun  8 11:14  .wget-hsts
drwxr-xr-x   4 rich rich     4096 Sep 21 16:32  .wine
drwxr-xr-x   3 rich rich     4096 Nov 14  2009  .winetrickscache
-rw-------   1 rich rich      218 Aug 28 14:46  .Xauthority
-rw-rw-r--   1 rich rich       54 Apr 28  2013  .Xauthority.05C3VW
-rw-rw-r--   1 rich rich       54 May 12  2013  .Xauthority.0VGGWW
-rw-rw-r--   1 rich rich       54 May  3  2013  .Xauthority.14MUWW
-rw-rw-r--   1 rich rich       54 May 27  2013  .Xauthority.1UFSXW
-rw-rw-r--   1 rich rich       54 Jul  4  2013  .Xauthority.2UM0ZW
-rw-rw-r--   1 rich rich       54 May 30  2013  .Xauthority.7ZYZXW
-rw-rw-r--   1 rich rich       54 Jul 18  2013  .Xauthority.8YE7ZW
-rw-rw-r--   1 rich rich       54 May 20  2013  .Xauthority.ARRJXW
-rw-rw-r--   1 rich rich       54 Aug 31  2013  .Xauthority.FL6Q2W
-rw-rw-r--   1 rich rich       54 Jul 20  2013  .Xauthority.IHOD0W
-rw-rw-r--   1 rich rich       54 Jul 12  2013  .Xauthority.II99ZW
-rw-rw-r--   1 rich rich       54 Jul 18  2013  .Xauthority.L0UJ0W
-rw-rw-r--   1 rich rich       54 Aug  7  2013  .Xauthority.LP9H1W
-rw-rw-r--   1 rich rich       54 Apr 25  2013  .Xauthority.O3I7VW
-rw-rw-r--   1 rich rich       54 May 21  2013  .Xauthority.PFTAXW
-rw-rw-r--   1 rich rich       54 Jun 19  2013  .Xauthority.PFXDZW
-rw-rw-r--   1 rich rich       54 May  3  2013  .Xauthority.TETJWW
-rw-rw-r--   1 rich rich       54 Aug 28  2013  .Xauthority.WGSJ2W
-rw-rw-r--   1 rich rich       54 Jun 13  2013  .Xauthority.Y85HYW
-rw-rw-r--   1 rich rich       54 Sep  9  2013  .Xauthority.YE5Y2W
-rw-rw-r--   1 rich rich       54 Aug  7  2013  .Xauthority.ZACH1W
drwxr-xr-x   2 rich rich     4096 Jul 21  2011  .xine
drwxr-xr-x   2 rich rich     4096 Nov  6  2009  .xinput.d
-rw-r--r--   1 rich rich     7567 May 12  2014  .xscreensaver
-rw-------   1 rich rich     3376 Aug 27 17:07  .xsession-errors.old

```

```
rich@rich-Linux:~$ ls -la Desktop
ls: cannot access 'Desktop': No such file or directory

```

---

### Post by Impavidus on 2018-09-28
Also show us the contents of .config/user-dirs.dirs:```
cat ~/.config/user-dirs.dirs
```My suspicion is that the Desktop directory (or whatever translation you used) was removed, user-dirs was updated and now the desktop shows the contents of your home directory.

BTW, all those .goutputstream-****** files are the result of an old bug. You can safely remove them. I think the same for those .Xauthority.****** files.

---

### Post by trash1464 on 2018-09-28
> **Impavidus said:**
> Also show us the contents of .config/user-dirs.dirs:```
cat ~/.config/user-dirs.dirs
```My suspicion is that the Desktop directory (or whatever translation you used) was removed, user-dirs was updated and now the desktop shows the contents of your home directory.

BTW, all those .goutputstream-****** files are the result of an old bug. You can safely remove them. I think the same for those .Xauthority.****** files.

```
rich@rich-Linux:~$ cat ~/.config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
rich@rich-Linux:~$ 

```
I have used Ubuntu for some years and at least 4 or 5 releases keeping /home on a separate drive with the system on its own dedicated SSD. Makes upgrades or recovery from a catastrophic failure easy. That must be where all those old files are from. Deleted per your recommendation, thanks!

---

### Post by trash1464 on 2018-09-29
I wound up doing another full install with formatting all drives. No clue why desktop folders did not get created last time but its all good now.

Now to figure out how to tag this thread as solved.............

---

### Post by ajgreeny on 2018-09-29
Thanks for marking as solved.

Just for your information, the content of the ~/.config/user-dirs.dirs file was completely incorrect apart from the XDG_DOCUMENTS_DIR="$HOME/Documents" line as all the rest, including the Desktop did not include the needed folder name, and all end with "$HOME/" which is why your Desktop folder was showing all your home folders.
I think it should have been easily corrected by editing that corrupt file and adding the folder name to the end of each line where it was missing.

I have no idea how that file corruption might have happened; do you?

---

### Post by Impavidus on 2018-09-30
Maybe because the directory was deleted. Why that happened I don't know. On my own system I deleted the Music, Templates and Videos directories because I didn't use them, and a short while later I found that user-dirs.dirs was updated automatically:```
$ cat .config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Bureaublad"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/Openbaar"
XDG_DOCUMENTS_DIR="$HOME/Documenten"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/Afbeeldingen"
XDG_VIDEOS_DIR="$HOME/"

```I don't use Desktop or Public either, but didn't delete those.

---

### Post by trash1464 on 2018-10-01
> **ajgreeny said:**
> Thanks for marking as solved.

Just for your information, the content of the ~/.config/user-dirs.dirs file was completely incorrect apart from the XDG_DOCUMENTS_DIR="$HOME/Documents" line as all the rest, including the Desktop did not include the needed folder name, and all end with "$HOME/" which is why your Desktop folder was showing all your home folders.
I think it should have been easily corrected by editing that corrupt file and adding the folder name to the end of each line where it was missing.

I have no idea how that file corruption might have happened; do you?

It is a mystery to me. I installed 18.04 the same as every previous release using the "something else" leg, formatting the system drive and leaving the /home drive as is. That process has worked well until now. Maybe some accumulative bunch of stuff on the old /home drive conspired against me?? At the end of the day, the system and /home drives were both formatted to do a truly clean install and /home was selectively restored from duplicity backups. It was then I discovered that duplicity is not bullet proof. A lot of stuff was lost but life goes on. The system is now responsive and stable. Thanks for your time!

---

### Post by lite.m.finocchiaro on 2019-01-29
I'm replying to say that I have this exact same problem.

I modified and saved ~/.configs/user-dirs.dirs with the correct folder names, but upon logout/login, it was back in corrupted form. Same after a reboot.

This all happened after I lost power last week.  

I thought I had it fixed, but after an update today it happened again, and my user-dirs.dirs is back to this:

Edit:  I restart my machine very rarely, so I think the restart has something to do with why this file is getting corrupted.

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
```

---

### Post by wildmanne39 on 2019-01-29
Hello lite.m.finocchiaro, please start your own thread so you can get the help you need instead of posting in a solved thread because most people that help here will not look for new posts in a solved thread and we like for everyone to start there own thread when asking for help.

Thanks

---

