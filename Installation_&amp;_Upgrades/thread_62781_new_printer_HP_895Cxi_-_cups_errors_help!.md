---
title: "new printer HP 895Cxi - cups errors help!"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by taygan on 2005-09-05
I had a stylus C60 that bit the dust, got a free HP Deskjet 895Cxi, bought the ink and cables.  It works in windows both parallel and USB. Can't get it to work in Ubuntu.  I've installed and reinstalled cups and foomatic and hpijs.  The Epson used gimp-print, which may have messed things up, I haven't figured it out yet.

Tried Parallel and USB, same errors (here's the parallel saga first:)

First I tried removing the non-working DeskJet 895Cxi:

I couldn't remove it (CUPS error status 1280, whatever that is, I can't find the error code meaning.) so I stopped it, tried to restart gnome-cups-manager (oops, forgot to restart cups) and got the *same* error 1280.  I restarted cupsd and removed the printer.

```
taygan@chugiak:~ $ gnome-cups-manager

** (gnome-cups-manager:8748): WARNING **: failed request with status 1280

taygan@chugiak:~ $ killall -HUP cupsd
cupsd(6791): Operation not permitted
cupsd: no process killed
taygan@chugiak:~ $ sudo killall -HUP cupsd
Password:
taygan@chugiak:~ $ gnome-cups-manager

** (gnome-cups-manager:8777): WARNING **: failed request with status 1280
taygan@chugiak:~ $ sudo cupsd
taygan@chugiak:~ $ gnome-cups-manager
```


Next I tried adding the printer:

New Printer>(it detected the Local HP 895C) Forward>(autodetection not working now??)I have to manually select HP Deskjet 895C (hpijs - recommended)>Apply  *error 1280 again*

```
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz

** (gnome-cups-add:8903): WARNING **: failed request with status 1280
```

stop and restart cupsd and try it again:

Ah HA! now the 895C shows up in gnome-cups-add!  Hmmm CUPS is messing up??

```
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz
```

Try a test page::

Properties>Print Test Page>"A4 test page sent to printer" but nothing prints.  Looking at the terminal... uh oh failed request status 200:

```
** (gnome-cups-manager:9009): WARNING **: failed request with status 200

** (gnome-cups-manager:9009): WARNING **: failed request with status 200
Selected ppd file = foomatic-ppds/HP/HP-2000C-hpijs.ppd.gz
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz

** (gnome-cups-manager:9009): WARNING **: connect = 'parallel:/dev/lp0'
```


Stop and restart cupsd - SAME PROBLEMS!! ugh.


****************************

remove printer (goes okay)>reboot>switch to USB and try again>>

teminal>gnome-cups-manager>add a printer>use detected printer (local HP Deskjet 895C)>forward>(Ah Ha! it's detected!)HP Deskjet 895C - hpijs (recommended)>Apply>nothing happened

FAILED code 1280 again.

```
taygan@chugiak:~ $ gnome-cups-manager
Selected ppd file = foomatic-ppds/HP/HP-2000C-hpijs.ppd.gz
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz

** (gnome-cups-add:8700): WARNING **: failed request with status 1280
```

stop and start cupsd, try again, it works!

```
taygan@chugiak:~ $ sudo killall -HUP cupsd
Password:
taygan@chugiak:~ $ sudo cupsd
taygan@chugiak:~ $ gnome-cups-manager
Selected ppd file = foomatic-ppds/HP/HP-2000C-hpijs.ppd.gz
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz
```

try to go to properties (it works, but the terminal has errors):

```
** (gnome-cups-manager:8869): WARNING **: failed request with status 200

** (gnome-cups-manager:8869): WARNING **: failed request with status 200
Selected ppd file = foomatic-ppds/HP/HP-2000C-hpijs.ppd.gz
Selected ppd file = foomatic-ppds/HP/HP-DeskJet_895C-hpijs.ppd.gz

** (gnome-cups-manager:8869): WARNING **: connect = 'usb://HP/DeskJet%20895C?serial=MY946190QNFB'

```

Print a test page: nothing happens, no errors.

stop and restart cupsd and try test page again, same errors..


TRY AS ROOT! same errors, except when I add a second printer I get 404 instead of 200.  THe first printer still gets 200.



HELP!

---

