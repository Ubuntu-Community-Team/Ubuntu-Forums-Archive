---
title: "mini iso install freeze, non-pae i486"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by andreazzz on 2013-11-23
Hi everyone!
Yesterday I bought a nice little pc with AMD Geode processor, after a little trial and error I found out I had to use a non-PAE iso, so I downloaded the 12.04 mini ISO (both Ubuntu and Lubuntu) and installed it on a USB drive with Unetbootin (after dd'ing the pc gives an error "xxx.img not found"), start the installation, but during the part of the installation where everything is downloaded, my screen freezes (I can type text in the bottom of the screen, but it gives no response). Any ideas? I made the live-USB several times, both with Ubuntu and Lubuntu, I tried graphical and terminal install.

Thanks for your help so far!

---

### Post by ptrakk on 2013-11-23
"initrd.img not found?" or "xxx.img not found"

---

### Post by ptrakk on 2013-11-23
what are you dd'ing? please be more specific.

---

### Post by ptrakk on 2013-11-23
also try debian wheezy for it has multiarch support for cpus.

---

### Post by andreazzz on 2013-11-24
I did not get the error another time (I switched to Unetbootin), but the error was "initrd.img not found".
I dd'ed the Ubuntu (and Lubuntu) 12.04 mini-iso to my (formatted) USB with ```
dd if=~/Downloads/mini.iso of=/Dev/sdb1
``` Normally it works, but apparently it doesn't with the mini iso.

Will I be able to install Unity in Wheezy (haven't tried yet on my RaspPi)?

---

### Post by mörgæs on 2013-11-24
For the latest three years Buntu has not been running on the Geode, and I don't know of any workarounds. 

Your best option is trying other distros.

---

### Post by andreazzz on 2013-11-25
I succesfully installed Lubuntu 12.04 and installed "ubuntu-desktop", removed all the useless programs and now I'm stuck at booting. Something with the graphics settings messed up, problem is I can't use keyboard nor mouse to click anything. Alt+F2, dpkg-reconfigure xserver-xorg, no result, apt-get update and upgrade, no result, grub-mkconfig: I get grub, am able to boot into failsafe, but I cannot load Failsafe in the menu...
Lubuntu repair stucks after getting network connection, what should I do?

Edit: I made some progress. The Graphics screen still pop-ups at booting, but I am now able to get in the GUI/init 5 with "startx -- :1". X-org prompts the same error over and over again: 
```

[  1703.679] _XSERVTransSocketINETCreateListener: ...SocketCreateListener() fai$
[  1703.679] _XSERVTransMakeAllCOTSServerListeners: server already running
[  1703.679]
Fatal server error:
[  1703.679] Cannot establish any listening sockets - Make sure an X server isn$
[  1703.680]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[  1703.680] Please also check the log file at "/var/log/Xorg.0.log" for additi$
[  1703.680]
[  1703.680]  ddxSigGiveUp: Closing log
[  1703.680] Server terminated with error (1). Closing log file.

```
(this is the log/Xorg.0.log file)
Any ideas how to solve this? I cannot get X to configure, it prompts the same error...

Thanks for everything so far!

---

