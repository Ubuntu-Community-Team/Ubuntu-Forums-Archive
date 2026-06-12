---
title: "flickr uploadr and wine"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by edm00se on 2005-10-03
After finding a lack of  native flickr uploading app's, f-spot failing to launch [here]("http://www.ubuntuforums.org/showthread.php?t=71393"), and this past attempt to use flickr's uploadr for windows through wine, I'm becoming a bit ticked off.
Anywho, I installed flickr uploadr through wine and everything seemed hunky dory. Well, when I run it, the window initializes for about 1/2 a second, then fizzles out and then I get the wine "you got an error" screen. When run from terminal, I get the following output:
> eric@RabbitHole:~$ wine "C:\Program Files\Flickr Uploadr\Flickr Uploadr.exe"
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:ole:CoRegisterMessageFilter stub
err:x11drv:X11DRV_CreateWindow invalid window width -350
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (7000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option 6 STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (7000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option 6 STUB
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  53 (X_CreatePixmap)
Value in failed request:  0x0
Serial number of failed request:  4870
Current serial number in output stream:  4905
Wine failed with return code 1

Please, somebody either help me with f-spot (more preferable) or wave the magic fixer wand. I just crave sleep right now. Any thoughts would be greatly welcomed.

---

### Post by nbcthreat on 2005-10-23
There's a native Linux Uploadr here.

[http://micampe.it/things/flickruploadr](http://micampe.it/things/flickruploadr)

---

### Post by davebgimp on 2005-12-01
I'm trying to install this uploader for Linux and have been told that if i receive this error:

```
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

```

-then I need to install Python development packages for my distrobution. I can't seem to find this in Synaptic. I'm sure I must be searching wrong or missing it. Does anyone have the package's proper name?

---

### Post by davebgimp on 2005-12-01
It's python2.4-dev... (answering my own questions again...heh)

[QUOTE=davebgimp]I'm trying to install this uploader for Linux and have been told that if i receive this error:

```
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

```

-then I need to install Python development packages for my distrobution. I can't seem to find this in Synaptic. I'm sure I must be searching wrong or missing it. Does anyone have the package's proper name?[/QUOTE]

---

