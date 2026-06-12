---
title: "scared to reboot: problems with xubuntu dapper ugrade"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by RandomConjecture on 2006-06-18
Okay, I just tried to upgrade to Dapper. I looked through the wikis and help files and thread, and I can't find anything related to this offhand. I used the graphical update manager, so it did my source list for me, so theoretically that's okay. I don't think that's the problem anyway.

At the very end of installation, I had a problem installing cupsys, and 4 subsequent packages. Since one of these packages is xubuntu-desktop, I am terrified to reboot and attempt to finish the installation.

Here's my error:

Setting up cupsys (1.2.0-0ubuntu5) ...
 * Starting Common Unix Printing System: cupsd cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.1.23) | cups (>= 1.1.23); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gimpprint:
 cupsys-driver-gimpprint depends on cupsys-driver-gutenprint (>= 5.0.0~rc2-0ubuntu6); however:
  Package cupsys-driver-gutenprint is not configured yet.
dpkg: error processing cupsys-driver-gimpprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 xubuntu-desktop depends on cupsys-driver-gutenprint; however:
  Package cupsys-driver-gutenprint is not configured yet.
 xubuntu-desktop depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
 cupsys-driver-gimpprint
 hplip
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

My specs: Sony Vaio FX-215 (old computer, hence the xubuntu). 128 mb ram, dlink airxpert dwl-ag650 ethernet adapter. (PCMCIA). That's the only card I currently have plugged in. Lemme know if I'm forgetting any relevant specs.

By the bye, I just installed Xubuntu a month or so ago, and being out of school, I hadn't installed my printer yet. Actually, that's what I was working on when I decided to upgrade, but as far as I know I haven't changed anything with cups except to select it as my printing system in XFCE print manager. I honestly haven't had to change much on this system (Ubuntu rocks!), so everything should be pretty much defaulted.

Any help would be great, because right now I'm scared to do anything.

---

### Post by RandomConjecture on 2006-06-18
Wow, I don't know what I did wrong. Since I've posted this, a gazillion other users have posted issues and been helped. I'm very confused. Can someone give me a heads up on what fatal mistake I made that no one has given me even a clue of a direction to take? Either I broke some etiquette that I'm unaware of, or no one has a clue what this means?

---

### Post by angkor on 2006-06-18
[QUOTE=RandomConjecture]Wow, I don't know what I did wrong.[/QUOTE]

Nothing. My guess is that nobody who looked at your problem knew the answer. I know I don't. Sorry, wish I could be of help, but don't sweat it, somebody will probably come along and help you out.





[http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)

---

### Post by RandomConjecture on 2006-06-18
[https://launchpad.net/products/cups/+bug/31339](https://launchpad.net/products/cups/+bug/31339)

This bug report seems to claim that it's not a bug report at all, and it actually works fine. (Which is true, when I tried apt-get remove cupsys, it had to stop cupsbsd in order to remove the package, which makes no sense.) However, in my case, I can't configure the xubuntu-desktop package because it depends on cupsys.

There's a few other threads about this and similar problems, but I can't quite figure out how they related. 

[http://ubuntuforums.org/showthread.php?t=124214](http://ubuntuforums.org/showthread.php?t=124214)

---

### Post by dpmillerau on 2006-06-25
I had this problem after updating from Breezy (and Hoary a day before that). On AMD64.

The problem appears to be that cupsd is still running, so it can't be restarted. I fixed this by killing it.

ps -aef | grep cupsd

sudo kill -9 <pid>

Where <pid> is the process id of the cupsd process.

The a dpkg reconfigure works. 

Phew.

---

### Post by RandomConjecture on 2006-06-25
I actually can't find any evidence that cupsd is running. It's not listed under ps -A or ps -aef. If I do ps -aef | grep cupsd I get the following:

root@mable:/home/sydney# ps -aef | grep cupsd
root     18624 18603  0 22:34 pts/1    00:00:00 grep cupsd

If I'm not mistaken...that means the only instance of a process with 'cupsd' is the grep itself. Right?

Also, I tried just uninstalling cupsys and reinstalling (that way, no way it could be running) and it does the same thing.

Thanks for the assistance, anyway, though. I actually rebooted, and everything works fine...new XFCE up and running. Which is somewhat baffling considering that according to apt, xubuntu-desktop is still not set up. Go figure.

---

### Post by jcwinnie on 2006-11-21
dpmillerau,

Thanks for considering the problem and offering a suggestion. It dinna work for me.

Could you elaborate on what you meant by dpkg --reconfigure ?

Such a command failed for me, although aptitude did work.

There was considerable activity, but at the end there remained the message from gnome-apt-install that there were dependency problems with xubuntu-desktop.

jcwinnie
](*,)

---

