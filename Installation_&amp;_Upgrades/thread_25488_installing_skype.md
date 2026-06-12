---
title: "installing skype"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by furunculus on 2005-04-10
hello all, i have just installed ubuntu over the top of my defunct SUSE installation, and now i want to install skype so i can chat with all my chums.

with suse, i d/l'ed skype > clicked "open" in the firefox d/l manager > and away it went, installed in seconds.

with ubuntu, i d/l'ed skype > clicked "open" in the firefox d/l manager > only to be presented with three files: control.tar.gz, data.tar.gz, and debian-binary

errr, just a quick question; what the effing hell are these files, and how the eff do i make them do something useful, like install skype for example................?

many thanks

furunculus

---

### Post by edubarr on 2005-04-10
What version of the file did you download? 

If it was the Debian packaged version then all you need to do is run 'dpkg --install skype*.deb'. This is probably the recomended one for ubuntu. 

If you got the tar.bz2 then just run 'tar xvjf skype*.tar.bz2' and it will extract the files into a directory. All you need to do is go into that directory and run the executable (probably just type 'skype').

By the way, don't open it with firefox, but rather save it on your disk and do either one of those 2 above.

---

### Post by furunculus on 2005-04-10
> root@ubuntu:/home/hosiah # tar xvjf skype*.tar.bz2
tar: skype*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@ubuntu:/home/hosiah # dpkg --install skype*.deb
dpkg: error processing skype*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype*.deb
root@ubuntu:/home/hosiah #


? :-?

---

### Post by edubarr on 2005-04-10
Did you download any of the files before typing those commands? 

Click on the link bellow and save the file to disk:
[http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)

Then run the dkpg command.

---

### Post by furunculus on 2005-04-10
i have d/led the debian file to my desktop.

what is the dpkg command, and how should it be employed to get the package installed?

cheers

---

### Post by furunculus on 2005-04-10
errr, i ran the dkpg command in a terminal and actually ended up installing UT2k4.........?  :?  :p

---

### Post by jeremy on 2005-04-10
[QUOTE=furunculus]i have d/led the debian file to my desktop.

what is the dpkg command, and how should it be employed to get the package installed?

cheers[/QUOTE]
 the correct command is
$ sudo dpkg -i PATH_TO_SKYPE.DEB

---

### Post by sfw5000 on 2005-04-10
Hey -- also check out this post -- might help

[http://ubuntuforums.org/showthread.php?p=125550#post125550](http://ubuntuforums.org/showthread.php?p=125550#post125550)

---

### Post by ozorba on 2005-04-11
[QUOTE=edubarr]What version of the file did you download? 

If it was the Debian packaged version then all you need to do is run 'dpkg --install skype*.deb'. This is probably the recomended one for ubuntu. 

If you got the tar.bz2 then just run 'tar xvjf skype*.tar.bz2' and it will extract the files into a directory. All you need to do is go into that directory and run the executable (probably just type 'skype').

By the way, don't open it with firefox, but rather save it on your disk and do either one of those 2 above.[/QUOTE]

I have installed skype that I downloaded from skype site (debian packahe of course). skype works fine when I run kubuntu. But under ubuntu (GNOME) when I try to call anyone it locks up. I assume there is a problem with sound connection.

---

### Post by furunculus on 2005-04-12
[QUOTE=sfw5000]Hey -- also check out this post -- might help

[http://ubuntuforums.org/showthread.php?p=125550#post125550](http://ubuntuforums.org/showthread.php?p=125550#post125550)[/QUOTE]

cheers, there is a link to an official skype install guide, worked a treat. :D

> sudo apt-get install libqt3c102-mt
wget [http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb](http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb)
sudo dpkg -i skype_1.0.0.20-1_i386.deb

---

### Post by furunculus on 2005-06-01
why doesn't ^this^ work anymore?

> dimble@Dimble:~$  sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libqt3c102-mt-psql libqt3c102-mt-mysql libqt3c102-mt-odbc
The following NEW packages will be installed:
  libqt3c102-mt
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
Need to get 2960kB of archives.
After unpacking 7401kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main libqt3c102-mt 3:3.3.3-7ubuntu3 [2960kB]
Fetched 2960kB in 40s (72.6kB/s)

Preconfiguring packages ...
Selecting previously deselected package libqt3c102-mt.
(Reading database ... 58010 files and directories currently installed.)
Unpacking libqt3c102-mt (from .../libqt3c102-mt_3%3a3.3.3-7ubuntu3_i386.deb) ...Setting up libqt3c102-mt (3.3.3-7ubuntu3) ...

dimble@Dimble:~$ wget [http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb](http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb)
--20:30:26--  [http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb](http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb)
           => `skype_1.0.0.20-1_i386.deb'
Resolving myosc.org... 70.84.56.4
Connecting to myosc.org[70.84.56.4]:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
20:30:26 ERROR 403: Forbidden.

dimble@Dimble:~$ sudo dpkg -i skype_1.0.0.20-1_i386.deb
dpkg: error processing skype_1.0.0.20-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype_1.0.0.20-1_i386.deb
dimble@Dimble:~$ wget [http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb](http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb)
--20:31:00--  [http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb](http://myosc.org/ubuntuguide/skype_1.0.0.20-1_i386.deb)
           => `skype_1.0.0.20-1_i386.deb'
Resolving myosc.org... 70.84.56.4
Connecting to myosc.org[70.84.56.4]:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
20:31:00 ERROR 403: Forbidden.

dimble@Dimble:~$



---

