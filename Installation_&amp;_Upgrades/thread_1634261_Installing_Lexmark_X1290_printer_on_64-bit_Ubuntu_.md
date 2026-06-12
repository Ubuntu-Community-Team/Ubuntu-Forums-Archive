---
title: "Installing Lexmark X1290 printer on 64-bit Ubuntu 10.10"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by BioGeek on 2010-11-30
I upgraded from a 32-bit Ubuntu 10.04 to a 64 bit Ubuntu 10.10.
Under 32-bit Ubuntu 10.04, I had a Lexmark X1290 printer working flawlessly. Now I'm trying to install this printer again on the 64-bit Ubuntu 10.10 system.

I'm following the instructions from [http://www.trodrigues.net/wiki/linux:ubuntu:lexmark_x1290]("http://web.archive.org/web/20080119224658/http://www.trodrigues.net/wiki/linux%3aubuntu%3alexmark_x1290") and using the Z600 series driver from Lexmark.

[B]Create a directory named lexmark and unpack the driver:
[/B]
```
mkdir lexmark
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```
[B]Extract the driver from the install script:
[/B]
```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

```**And untar it:**

```
tar -xvzf install.tar.gz

```
This generates 2 drivers (z600cups-1.0-1.i386.rpm and z600llpddk-2.0-1.i386.rpm) that then should be converted to .deb files with alien and installed with dpkg, but -as the filenames already indicate- the drivers are for 32-bit systems and not for 64-bit systems. Hence the error:

```
$ sudo dpkg -i z600cups_1.0-2_i386.deb 
dpkg: error processing z600cups_1.0-2_i386.deb (--install):
  package architecture (i386) does not match system (amd64)
  Errors were encountered while processing: z600cups_1.0-2_i386.deb
```
Any idea how I can get this to work?

---

### Post by Achronon on 2011-07-01
To install the z600  driver on an amd64 or x86-64 platform see the instructions here:
[http://ubuntuforums.org/showthread.php?t=616097]("http://ubuntuforums.org/showthread.php?t=616097")

You will have to download the tarball CJLZ600LE-CUPS-1.0-1.TAR.gz  from an alternative location.

e.g., do,

`wget ftp://192.87.102.43/vol/1/pardusrepo/ftp/pub/pisi/source/2007/CJLZ600LE-CUPS-1.0-1.TAR.gz`

Or if that location is now dead try one from the list here:
[http://www.filewatcher.com/m/CJLZ600LE-CUPS-1.0-1.TAR.gz.4301167.0.0.html]("http://www.filewatcher.com/m/CJLZ600LE-CUPS-1.0-1.TAR.gz.4301167.0.0.html")

---

### Post by Achronon on 2011-07-01
Hmmm...

After installing the z600 driver as above, I tried printing a test page and received a system tray message:

Printer "Lexmark_X1100" cups-insecure-filter.

SOLUTION: (worked for me)

sudo chown -R root:root /usr/lib/cups/filter/
sudo chown -R root:root usr/lib/cups/backend/


I'm using:
cups 1.4.6
kernel: Linux version 2.6.38-8-generic
arch: x86_64

---

