---
title: "Unstable desktop after Fiesty upgrade..."
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by SFDD on 2007-04-28
I just upgraded Edgy to Fiesty. There were several errors reported during the upgrade, but at the end (after two tries) I was able to get it to boot the desktop. But now random things are crashing, such as the volume control, the trash can, etc. I just get these "quit unexpectedly" messages popping up. Eventually, all the icons on the desktop vanished too. I read another post that advised to reinstall ubuntu-desktop, but this is what I get:

```
root@P3-UBUNTU:/home/david# apt-get install ubuntu-desktop

Reading package lists... Done

Building dependency tree       

Reading state information... Done

ubuntu-desktop is already the newest version.

The following packages were automatically installed and are no longer required:

  libapr0 ntp-simple libwavpack0 libxcompext1 nxagent libxcomp1 expect ntp

  tcl8.4 nxlibs

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

6 not fully installed or removed.

Need to get 0B of archives.

After unpacking 0B of additional disk space will be used.

Setting up ttf-gentium (1.02-2ubuntu2) ...

E: /var/lib/defoma/locked exists.

E: Another defoma process seems running, or you aren't root.

E: If you are root and defoma process isn't running undoubtedly,

E: it is possible that defoma might have aborted.

E: Please run defoma-reconfigure -f to fix its broken status.

dpkg: error processing ttf-gentium (--configure):

 subprocess post-installation script returned error exit status 1

Setting up x-ttcidfont-conf (25) ...

E: /var/lib/defoma/locked exists.

E: Another defoma process seems running, or you aren't root.

E: If you are root and defoma process isn't running undoubtedly,

E: it is possible that defoma might have aborted.

E: Please run defoma-reconfigure -f to fix its broken status.

dpkg: error processing x-ttcidfont-conf (--configure):

 subprocess post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of ttf-thai-tlwg:

 ttf-thai-tlwg depends on x-ttcidfont-conf; however:

  Package x-ttcidfont-conf is not configured yet.

dpkg: error processing ttf-thai-tlwg (--configure):

 dependency problems - leaving unconfigured

Setting up xfonts-scalable (1.0.0-6) ...

warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

E: /var/lib/defoma/locked exists.

E: Another defoma process seems running, or you aren't root.

E: If you are root and defoma process isn't running undoubtedly,

E: it is possible that defoma might have aborted.

E: Please run defoma-reconfigure -f to fix its broken status.

dpkg: error processing xfonts-scalable (--configure):

 subprocess post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of xorg:

 xorg depends on xfonts-scalable (>= 1:1.0.0-1); however:

  Package xfonts-scalable is not configured yet.

dpkg: error processing xorg (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of ubuntu-desktop:

 ubuntu-desktop depends on x-ttcidfont-conf; however:

  Package x-ttcidfont-conf is not configured yet.

 ubuntu-desktop depends on xorg; however:

  Package xorg is not configured yet.

dpkg: error processing ubuntu-desktop (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 ttf-gentium

 x-ttcidfont-conf

 ttf-thai-tlwg

 xfonts-scalable

 xorg

 ubuntu-desktop

E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas on what I might try next?

---

### Post by Iarwain ben-adar on 2007-04-28
> E: Please run defoma-reconfigure -f to fix its broken status.

Try that ;)


Iarwain

---

### Post by SFDD on 2007-04-29
Honestly, I didn't try that at fist because I wasn't sure if it was a *real* error message or one of those that will just lead to more trouble.

But I have since tried it and it's made no difference. 

Sometimes I'm getting the "quit unexpectedly" message and sometimes--as is the case with Firefox--the program just disappears.

Is there any such command along the lines of "verify" that will scour the system to ensure all files for this upgrade are present and reinstall them if needed?

---

### Post by Iarwain ben-adar on 2007-04-29
I don't know of such a command..

But it complains also about the defoma process already running..

(try a 'killall defoma' or something like that)


Iarwain

---

