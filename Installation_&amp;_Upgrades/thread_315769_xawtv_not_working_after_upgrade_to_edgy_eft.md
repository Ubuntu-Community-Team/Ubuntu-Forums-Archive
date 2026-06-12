---
title: "xawtv not working after upgrade to edgy eft"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by MadeR on 2006-12-09
My problem:
after upgrade from Dapper to Edgy xawtv does not work any longer.

that's the output message:This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found


and this is the output of "grep FontPath /etc/X11/xorg.conf":
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/misc"

---

### Post by MadeR on 2006-12-10
is it possible that in edgy eft these fonts do not exist?

---

### Post by barmaley on 2007-01-03
Hello, people
I also have problem running xawtv on edgy, in dapper it worked.
Here is the output I get:

This is xawtv-3.95, running on Linux/i686 (2.6.17-10-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

If someone knows how to make xawtv running on edgy, please help.

---

### Post by arosboro on 2008-01-07
MadeR,

The tv-fonts package contains the default fonts for xawtv. I ran "sudo aptitude install tv-fonts" however the font path wasn't the same as ubuntu's:

```
Selecting previously deselected package tv-fonts.
(Reading database ... 106150 files and directories currently installed.)
Unpacking tv-fonts (from .../tv-fonts_1.1-4_all.deb) ...
Setting up tv-fonts (1.1-4) ...
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
```


It seams in 7.10 Ubuntu uses /usr/share/fonts/X11/misc/ for these fonts.  This is the only folder that the command "locate X11/misc" finds.  Here are the steps that I took to manually install tv-fonts:

Go to [http://linux.bytesex.org/xawtv/tvfonts.html](http://linux.bytesex.org/xawtv/tvfonts.html) to read about manually installing tv-fonts.  Get the latest tar file:  

```

$ cd ~
$ wget http://dl.bytesex.org/releases/tv-fonts/tv-fonts-1.1.tar.bz2
$ tar -xvf tv-fonts-1.1.tar.bz2
$ cd tv-fonts-1.1/
$ make
$ sudo cp *.pcf.gz /usr/share/fonts/X11/misc/
$ cd /usr/share/fonts/X11/misc/
$ sudo mkfontdir
$ xset fp rehash

```

The problem still exists:

```
$ xawtv /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i586 (2.6.22-14-generic)
WARNING: Your X-Server has no DGA support.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion
Oops: can't load any font

```
 
Any ideas?

---

