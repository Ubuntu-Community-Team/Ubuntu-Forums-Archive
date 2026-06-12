---
title: "Upgrading HPLIP from stock 2.8.2 to 2.8.7"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by xen-uno on 2008-08-12
HPLIP = Hewlett Packard Linux Imaging & Printing (drivers used by CUPS for HP devices)

.2 is latest in Synaptic, .7 is available via HP. I'm trying to upgrade to .7 as outlined here ...

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

... and especially here ...

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

Installs fine ... no errors, however, the install script runs **sudo hp-setup** which should detect my LaserJet 4 that has both parallel (disconnected - not needed) and JetDirect (192.168.0.20) connections. It can't seem to find the printer (which is on & ready) either automatically or manually (when given the IP). 2.8.2 works fine with either connection, but I wanted to break something with a non-commissioned upgrade. As of right now, .7 is installed and not working but fortunately, hasn't broken .2. No mention is made by HP of the need to un-install older versions. Anyone have a clue what's going on here?

---

### Post by cariboo on 2008-08-12
Ubuntu version numbers are not always the same as upstream version numbers eg: Latest stable kernel is 2.6.26.2 but when I run:

```
uname -a
```

I get this result:

```
jimk@intrepid:~$ uname -a
Linux intrepid 2.6.26-5-generic #1 SMP Sun Aug 10 20:28:44 UTC 2008 x86_64 GNU/Linux
```

This was just updated 08/08/08

Jim

---

### Post by xen-uno on 2008-08-14
Not the case here ... 2.8.7 released 7/30/08

Release log:

[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

---

### Post by wesswei on 2008-08-14
I'm in the same boat here. 

I tried building the package from the hplip sourceforge page, but the build fails. I let you know if I get it to install properly.

EDIT 1: I noticed hplip2.8.7 is in the intrepid repositories. It then however has ridiculous dependencies, some of which are completely unnecessary and do not conform to current packages. It's your choice and risk, but you can do the following if you do not want to build the package yourself.

Add this to your repos list either in synaptic or manually edit the sources.list:
```
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
```
Then ```
sudo apt-get install hplip
``` should automatically upgrade and add the needed dependencies.

I'm going to try uninstalling and rebuilding first as it upgrades libc6, which a lot of programs need, and I don't want to break anything unless I'm sure upgrading won't break it.

Good luck, and let me know if you decide to do that.

---

### Post by wesswei on 2008-08-14
Just an update on my end. 

I successfully built 2.8.7 of hplip. I completely uninstalled hplip2.8.2 via synaptic. Then compiled and installed hplip using the autoinstaller from the website. I rebooted and have full support for my printer. No headaches here. Everything works! Well, I haven't tried the buttons yet, but at least software scans and prints ok.

I tried to use checkinstall before to build my own package, but it fails on install using the generated *.deb. I really wish I could have installed the ubuntu package from intrepid or at least have a backported archive. Anyway, if anyone finds one or trys the intrepid version, post your success or PM me.

:)

PS. I did have to modify the hp-systray startup entry to use the --qt4 option otherwise it doesn't integrate into the taskbar.
Found here: [https://bugs.launchpad.net/hplip/+bug/231978]("https://bugs.launchpad.net/hplip/+bug/231978")

---

### Post by xen-uno on 2008-08-16
You must be on 32 bit 8.04? x64 here. Uninstalled .2 hplip (hpijs, hplip, hplip-data, and another dependency) via Synaptic. Ran the .7 install script with no errors (this time with parallel support) but it still doesn't detect the LJ4.

---

