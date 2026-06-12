---
title: "Applications crash under Gnome due to incomplete installation"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Sam D on 2006-07-25
Hi all,

I just reinstalled Ubuntu 6.06. I must have a problem with my CD reader because I always have a problem during the installation process, and not in a repeatable manner. Different CDs were tried. Live CD does not launch Gnome. The alternate CDs more or less installed a linux, and I finished the intallation "by random" using "*sudo apt-get build-dep ...*".
At the beginning, Gnome could not launch and after different trials, I got it to work after a "*sudo apt-get install linux-headers-`uname -r` build-essential*".

My first question is: is there a way to ask to Synaptic (or whatever) to install all the packages that should have been installed during a normal installation process, and to remove all the other ones ?

Because there must be something wrong. Now, Gnome correctly opens my sessions, but any applications crash whenever they want it to, it can last from 0 second to a few minutes.

Here is my .xsession-errors at the start of Gnome:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sam"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/cornelius:/tmp/.ICE-unix/7593

(gnome-panel:7669): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:7669): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

** (gnome-panel:7669): WARNING **: /build/buildd/gnome-panel-2.14.2/./gnome-panel/panel-applet-frame.c:1304: failed to load applet OAFIID:GNOME_MixerApplet (can't get property bag):
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'
```

It was worth when I tried to install a local printer.
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sam"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/cornelius:/tmp/.ICE-unix/4562
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4637): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:4637): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
(disks-admin:4758): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-OAKT_Printer-foo2oak.ppd (Generic OAKT Printer Foomatic/foo2oak (recommended)[1]) and
    ->Generic-OAKT_Printer.ppd.gz (Generic OAKT Printer Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-ZjStream_Printer-foo2zjs.ppd (Generic ZjStream Printer Foomatic/foo2zjs (recommended)[1]) and
    ->Generic-ZjStream_Printer.ppd.gz (Generic ZjStream Printer Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: model named 'designjet 5500ps (recommended)' doesn't have a recognized structure

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_1500-foo2oak.ppd (HP Color LaserJet 1500 Foomatic/foo2oak (recommended)[1]) and
    ->HP-Color_LaserJet_1500.ppd.gz (HP Color LaserJet 1500 Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2hp (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_2600n-foo2hp.ppd (HP Color LaserJet 2600n Foomatic/foo2hp (recommended)[1]) and
    ->HP-Color_LaserJet_2600n.ppd.gz (HP Color LaserJet 2600n Foomatic/foo2hp (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1000-foo2zjs.ppd (HP LaserJet 1000 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1000.ppd.gz (HP LaserJet 1000 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1005-foo2zjs.ppd (HP LaserJet 1005 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1005.ppd.gz (HP LaserJet 1005 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1020-foo2zjs.ppd (HP LaserJet 1020 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1020.ppd.gz (HP LaserJet 1020 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3030-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3020-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200m-Postscript.ppd (HP LaserJet 3200 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200-Postscript.ppd (HP LaserJet 3200 Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3300_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3330_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4350-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4300-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9050_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9040_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9065_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9055_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-Color_PageWorks_Pro_L.ppd.gz (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-Color_PageWorks_Pro_L-foo2zjs.ppd (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2200_DL.ppd.gz (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2200_DL-foo2zjs.ppd (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2300_DL.ppd.gz (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2300_DL-foo2zjs.ppd (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4910): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2430_DL.ppd.gz (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2430_DL-foo2zjs.ppd (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended))[1]
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-OAKT_Printer-foo2oak.ppd (Generic OAKT Printer Foomatic/foo2oak (recommended)[1]) and
    ->Generic-OAKT_Printer.ppd.gz (Generic OAKT Printer Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-ZjStream_Printer-foo2zjs.ppd (Generic ZjStream Printer Foomatic/foo2zjs (recommended)[1]) and
    ->Generic-ZjStream_Printer.ppd.gz (Generic ZjStream Printer Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: model named 'designjet 5500ps (recommended)' doesn't have a recognized structure

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_1500-foo2oak.ppd (HP Color LaserJet 1500 Foomatic/foo2oak (recommended)[1]) and
    ->HP-Color_LaserJet_1500.ppd.gz (HP Color LaserJet 1500 Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2hp (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_2600n-foo2hp.ppd (HP Color LaserJet 2600n Foomatic/foo2hp (recommended)[1]) and
    ->HP-Color_LaserJet_2600n.ppd.gz (HP Color LaserJet 2600n Foomatic/foo2hp (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1000-foo2zjs.ppd (HP LaserJet 1000 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1000.ppd.gz (HP LaserJet 1000 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1005-foo2zjs.ppd (HP LaserJet 1005 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1005.ppd.gz (HP LaserJet 1005 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1020-foo2zjs.ppd (HP LaserJet 1020 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1020.ppd.gz (HP LaserJet 1020 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3030-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3020-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200m-Postscript.ppd (HP LaserJet 3200 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200-Postscript.ppd (HP LaserJet 3200 Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3300_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3330_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4350-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4300-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9050_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9040_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9065_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9055_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-Color_PageWorks_Pro_L.ppd.gz (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-Color_PageWorks_Pro_L-foo2zjs.ppd (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2200_DL.ppd.gz (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2200_DL-foo2zjs.ppd (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2300_DL.ppd.gz (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2300_DL-foo2zjs.ppd (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:4980): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->Minolta-magicolor_2430_DL.ppd.gz (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2430_DL-foo2zjs.ppd (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended))[1]
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet-pcl3.ppd
Selected ppd file = linuxprinting.org-gs-builtin/HP/HP-DeskJet_710C-pnm2ppa.ppd

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-OAKT_Printer-foo2oak.ppd (Generic OAKT Printer Foomatic/foo2oak (recommended)[1]) and
    ->Generic-OAKT_Printer.ppd.gz (Generic OAKT Printer Foomatic/foo2oak (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/Generic/Generic-ZjStream_Printer-foo2zjs.ppd (Generic ZjStream Printer Foomatic/foo2zjs (recommended)[1]) and
    ->Generic-ZjStream_Printer.ppd.gz (Generic ZjStream Printer Foomatic/foo2zjs (recommended))[1]

** (gnome-printer-view:4894): WARNING **: model named 'designjet 5500ps (recommended)' doesn't have a recognized structure

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_1500-foo2oak.ppd (HP Color LaserJet 1500 Foomatic/foo2oak (recommended)[1]) and
    ->HP-Color_LaserJet_1500.ppd.gz (HP Color LaserJet 1500 Foomatic/foo2oak (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2hp (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_2600n-foo2hp.ppd (HP Color LaserJet 2600n Foomatic/foo2hp (recommended)[1]) and
    ->HP-Color_LaserJet_2600n.ppd.gz (HP Color LaserJet 2600n Foomatic/foo2hp (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1000-foo2zjs.ppd (HP LaserJet 1000 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1000.ppd.gz (HP LaserJet 1000 Foomatic/foo2zjs (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1005-foo2zjs.ppd (HP LaserJet 1005 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1005.ppd.gz (HP LaserJet 1005 Foomatic/foo2zjs (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1020-foo2zjs.ppd (HP LaserJet 1020 Foomatic/foo2zjs (recommended)[1]) and
    ->HP-LaserJet_1020.ppd.gz (HP LaserJet 1020 Foomatic/foo2zjs (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3030-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3020-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200m-Postscript.ppd (HP LaserJet 3200 Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200-Postscript.ppd (HP LaserJet 3200 Postscript (recommended))[1]

** (gnome-printer-view:4894): WARNING **: Two ppds have driver == 'Standard'
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
    ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3300_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]


(and so on....)


DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  6072 Instruction illégale   "$prog" ${1+"$@"}
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 Creating link /home/sam/.kde/socket-cornelius.
Created link from "/home/sam/.kde/socket-cornelius" to "/tmp/ksocket-sam"
Creating link /home/sam/.kde/tmp-cornelius.
Created link from "/home/sam/.kde/tmp-cornelius" to "/tmp/kde-sam"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Creating link /home/sam/.kde/cache-cornelius.
Created link from "/home/sam/.kde/cache-cornelius" to "/var/tmp/kdecache-sam"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: WARNING: Can't open /home/sam/.kde/share/apps/konqueror/bookmarks.xml
invalid length 24902
Failed to process 45 bytes from server
invalid length 24902
invalid length 24902
invalid length 24902

(synaptic:5524): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5524): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
Error: No running window found
```

If someone is able help me ! Thank you sooo much, because I'm a little bit lost.

Yours,
Sam

---

### Post by linear on 2006-07-25
For a quick attempt, try the following at a command prompt:

[B]sudo apt-get update
sudo apt-get install ubuntu-desktop
[/B]
If that doesn't work, start looking through the links in [this thread]("http://www.ubuntuforums.org/showthread.php?t=187656").

---

### Post by Sam D on 2006-07-26
Thanks linear,
I've done that, even "sudo apt-get build-dep ubuntu-desktop".
But I will try to uninstall it and reinstall it.

Otherwise, I've tried to brows the forums, but I don't see a similar thread about applications crashing in a systematic manner.
S.

PS: I have a question by the way, why "install" does not install the dependent packages ?

---

### Post by linear on 2006-07-26
[quote=Sam D]PS: I have a question by the way, why "install" does not install the dependent packages ?[/quote]
Normally install should, and does. Something went horribly wrong here.

---

### Post by Sam D on 2006-07-26
I have followed the different links and it seems that I can take my system back to a clean version just as after an installation using DEBFOSTER.

How to do so ? :confused: 

Debfoster allows me to uninstall the different packages as clean as possible, but which packages should I then install with "*apt-get install*" to have all the basics like the installation CD does ? :?: 

Thx

---

### Post by linear on 2006-07-26
See the post [here]("http://www.ubuntuforums.org/showthread.php?t=186672"), starting at step 5. It might be good to do some of the checks earlier in the post, to make sure you have a clean sources.list and no broken dependencies.

---

### Post by Sam D on 2006-08-01
Excellent,
I've tried all this thread, and I am now confident in the fact that my Dapper is well installed.
BUT THE PROBLEM IS THE SAME :( 
Even gnome crashes, sometimes gdm is auto-restarted.

I have checked /var/log/Xorg.0.log and ~/xsession-errors log files, the first one tells me about the fact that a wacom is no found (it is a reported installation problem, wacom being installed by default), and the second is about the same as previously.

What could I check now that all the packages are correctly installed for sure? :confused:

---

### Post by Sam D on 2006-08-01
By the way, I'm using **zd1211** for my wireless donkle. Sometimes, the WLAN connection cannot make DHCP work, even when I do */etc/init.d/networking restart*. WiFi perefctly works on other computers. I imagine a certain process important to this also crashed at the begining.

If the session successfully opened, sometimes the clock panel or the trash panel fail, a popup then ask me to suppress them.

When I try to launch firefox, it variably lasts, sometimes opens. I might have a message like "*segmentation error*", but again, it is not repeatable.

What do you thing ? New hardware issue, not compatible with dapper ?

---

### Post by Sam D on 2006-08-01
Solution for the crashes : some of my RAM was dead...
I had tried MEMTEST before, but the problem was detected only at test 5 or 6... after quite a while !! Works fine now.

Solution for networking :
something added in */etc/network/interfaces* a line about eth0. In my case, wlan0 and eth0 seem to be non-compatible ! Comment any line about eth0.
If somebody has an explanation ?

---

