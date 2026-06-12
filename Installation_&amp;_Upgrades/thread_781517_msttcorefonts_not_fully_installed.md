---
title: "msttcorefonts not fully installed"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by MaybeMythtaken on 2008-05-04
For a home theatre PC I have installed gutsy (on a Gigabyte MA69GM-S2H with 1Gb DDR2, with a WinFast DTV-1000S) and installed Mythbuntu. When trying to configure Mythbuntu in its control centre, I ran into some problems with apt-get. 

It seems that my system now has a partially installed msttcorefonts, and I can't work out how to get it completely installed. (I've tried purging it and reinstalling it, but nothing seems to get rid of the problem it has.)

No matter what I try to install or remove now, apt-get adds a message:
```
1 not fully installed or removed.
```
and then proceeds to try to get the rest of the ms font package, timing out on every sourceforge entry, vis.,
```
theatre@wilson-theatre:~$ sudo apt-get remove traceroute
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  traceroute
0 upgraded, 0 newly installed, 1 to remove and 136 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 176kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112363 files and directories currently installed.)
Removing traceroute ...
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--23:44:33--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--23:44:43--  dhttp://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--23:44:53--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--23:45:03--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--23:45:13--  http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--23:45:23--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--23:45:33--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--23:45:43--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--23:45:53--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--23:46:03--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--23:46:13--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--23:46:23--  http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--23:46:33--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is there a way to fix this. It takes minutes every time I do the smallest install or remove and it's preventing installation of software that relies on it. :( 
(Please don't assume I know much about linux.)

---

### Post by MaybeMythtaken on 2008-05-05
Ok, I think I've managed to clean out the screwy partial install. I followed the suggestion given in [Debian Bug report logs #239482.]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=2394")

---

### Post by MaybeMythtaken on 2008-05-05
:cry:
Just when I thought it was going to be smooth sailing, I started setting up Mythbuntu again, and it tries to pull in msttcorefonts, which fails to install, just like before.

Any suggestions?

---

### Post by MaybeMythtaken on 2008-05-05
Purged the msttcorefonts again (after having to mod /var/lib/dpkg/info/msttcorefonts.prerm again).

Next I ran
```
sudo apt-get dist-upgrade
``` and that upgraded a whole heap of stuff. Then tried
```
sudo apt-get msttcorefonts
```
This time it seems to have installed the fonts.

* crosses fingers *

---

### Post by MaybeMythtaken on 2008-05-06
P.S.

Looks like I stuffed up by getting a DTV-1000S. No Linux support. When I was reading the Leadtek site it looked like the 1000S was just a half-height version of the 1000T. I should have looked more closely at the Linux supported cards lists.

---

