---
title: "PXE Boot Install of 13.10 vs 12.04 Using Http Mirror"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by ccarver0 on 2013-11-03
Hello All,

I have a server that acts as DCHP, TFTP, and HTTP servers for provisioning Ubuntu 12.04 systems using PXE net installations against a local mirror where my files are hosted over HTTP using Apache.  I build new servers, they boot, receive their IP and TFTP information, and are automatically installed with 12.04 using preseeding and a custom kickstart file.  It works great.  I just tried to setup the same kind of automated provisioning system by locally mirroring the 13.10 server files in the TFTP directory and web server.  I made the necessary changes in my pxelinux menus.  However, this install doesn't work.  I get the error in the GUI installer:

[IMG]http://i.imgur.com/RhCHr4a.png[/IMG]
 
 /var/log/syslog contains these lines:

```
Nov  3 15:21:08 main-menu[2345]: (process:7100): WARNING: could not open /lib/modules/3.11.0-12-generic/modules.builtin: No such file or directory
**Nov  3 15:21:09 main-menu[2345]: INFO: Menu item 'live-installer' selected**
**Nov  3 15:21:09 base-installer: error: Could not find any live images**
Nov  3 15:21:09 main-menu[2345]: WARNING **: Configuring 'live-installer' failed with error code 1
Nov  3 15:21:09 main-menu[2345]: WARNING **: Menu item 'live-installer' failed.
Nov  3 15:29:03 main-menu[2345]: INFO: Modifying debconf priority limit from 'critical' to 'high'
Nov  3 15:29:03 debconf: Setting debconf/priority to high
Nov  3 15:29:09 main-menu[2345]: INFO: Menu item 'save-logs' selected

```

When I compare the /var/log/syslog output with the Ubuntu 12.04 system (which installs perfectly), here's the difference:

```
**Nov  3 16:36:19 main-menu[2615]: INFO: Menu item 'bootstrap-base' selected**
Nov  3 16:36:19 debconf-copydb: Cannot open question file /target/var/cache/debconf/config.dat: No such file or directory
Nov  3 16:36:19 debconf-copydb: Cannot open template file /target/var/cache/debconf/templates.dat: No such file or directory
Nov  3 16:36:19 base-installer: chroot: can't execute 'debconf-set-selections': No such file or directory
Nov  3 16:36:19 base-installer: warning: /usr/lib/base-installer.d/20console-setup returned error code 127
Nov  3 16:36:19 debootstrap: gpgv:
Nov  3 16:36:19 debootstrap: Signature made Tue Aug 20 23:12:17 2013 UTC using DSA key ID FBB75451
Nov  3 16:36:19 debootstrap: gpgv:
Nov  3 16:36:19 debootstrap: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
```

It seems like 'bootstrap-base' menu item is selected for 12.04 (which succeeds), as opposed to 'live-installer' menu item being selected for 13.10 (which fails).  I don't specify any menu items in my kickstart or preseeding.  Does anyone know why this is different or if this is definitely my problem?  Any documentation or suggestions would be very much appreciated!

Thanks in advance.

---

### Post by ccarver0 on 2013-11-05
I solved this problem by editing my kickstart file to specify a URL of a public http mirror, rather than the local mirror that I had created from a CD image.  I'm still not sure why the local mirror created from the CD is adequate for 12.04 and not 13.10.

---

### Post by zaitch on 2013-11-24
Did you ever fix this beyond the public server specification? I've hit much the same thing

At first I thought this was the (infamous) missing ".disk" in the root disk image, but it appears not.

Haven't tried it on 12.04, only 13.10

Everything else - PXE, HTTP files, KS file seems OK.

---

### Post by thirstycat on 2014-05-07
> **zaitch said:**
> Did you ever fix this beyond the public server specification? I've hit much the same thing



would love to know if anyone has gotten to the bottom of this... I'm running into the same issue with a pxe boot install of 14.04

---

### Post by John_Kelly on 2014-06-25
I am also having this problem with 14.04
For some reason the earlier versions of Ubuntu on my PXE server work fine, but 14.04 still fails to install

There is still no fix for this?

---

### Post by ppatrick on 2014-07-29
Serva got it solved;
Get the full append line (it's a long one) from here:
[http://vercot.com/~serva/an/NonWindowsPXE3.html](http://vercot.com/~serva/an/NonWindowsPXE3.html)
you can pass the d-i parameters either in a pressed file or as kernel parameters in an append line.

---

