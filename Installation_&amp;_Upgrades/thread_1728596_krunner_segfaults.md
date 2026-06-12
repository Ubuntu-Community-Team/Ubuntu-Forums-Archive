---
title: "krunner segfaults"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2011-04-13
I have Kubuntu 10.10 64-bit, which was running fine until I did a bunch of apt-get software installs to permit me to compile YaWP weather plasmoid. In the process I am now at KDE 4.6.2, and my system is now non-functional, not able to start KDE desktop.

When KDE starts I get continuous krunner segfaults, krunner is taking 100% of the CPU, the desktop is there but the system is unusable. /var/log/messages is filled with the krunner segfaults, each line further indicating "error 4 in libkio.so.5.6.0". I tried reinstalling kubuntu-desktop, problem remains.

I expect I have created some software incompatibility with my installs, but I do not know how to diagnose/resolve. Would appreciate recommendations .... Gus

---

### Post by rosencrantz on 2011-04-13
Could it be an indigestible plugin?
Try setting all enabled plugins to False in 
~/.kde/share/config/krunnerrc
or delete the rc file and let KDE reinitialise it.

---

### Post by gus_zernial on 2011-04-14
Good idea, but unfortunately it did not stop the segfaults.
Below is my .krunnerrc .... what I did was create a backup
of the file (krunnerbackup) and then delete the original 
and restart ... KDE did not create a new krunnerrc and the
segfault problem was the same. Is it possible there is a very basic krunnerrc I could install and try that? Or, other ideas?

Thx, Gus

[EdgePositions]
Screen0=750,0

[General]
PastQueries=,goog,google

[Interface]
Height 1050=260
Height 1080=295
Height 1200=267
Height 864=255
Size=420,143
Width 1152=420
Width 1600=420
Width 1680=420
Width 1920=420

[PlasmaRunnerManager]
LaunchCounts=1 services_google-earth.desktop,1 services_Google-googleearth.desktop

[Runners][Bookmarks]
dbfile=/home/rbroman/.mozilla/firefox/ce9dn18p.default/places.sqlite

[TaskDialog]
Height 1080=419
Width 1920=649
filterState=0
headerState=\x00\x00\x00&#65533;\x00\x00\x00\x00\x00\x00\x00\x01\x00\x00\x00\x00\x00\x00\x00\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x0f&#65533;3\x00\x00\x00\t\x00\x00\x00\r\x00\x00\x00d\x00\x00\x00\x0c\x00\x00\x00d\x00\x00\x00\t\x00\x00\x00d\x00\x00\x00\x08\x00\x00\x00d\x00\x00\x00\x07\x00\x00\x00d\x00\x00\x00\x06\x00\x00\x00d\x00\x00\x00\x04\x00\x00\x00d\x00\x00\x00\x03\x00\x00\x00d\x00\x00\x00\x02\x00\x00\x00d\x00\x00\x02t\x00\x00\x00\x0f\x01\x01\x00\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00d&#65533;&#65533;&#65533;&#65533;\x00\x00\x00&#65533;\x00\x00\x00\x00\x00\x00\x00\x08\x00\x00\x00&#65533;\x00\x00\x00\x02\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x03\x00\x00\x00\x00\x00\x00\x00H\x00\x00\x00\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x04\x00\x00\x00\x00\x00\x00\x00P\x00\x00\x00\x01\x00\x00\x00\x00\x00\x00\x00h\x00\x00\x00\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\x00\x00\x00\x00\x00\x00&#65533;\x00\x00\x00\x01\x00\x00\x00\x00
ioInformation=5
ioUnits=0
normalizeCPUUsage=true
showCommandLineOptions=false
showTooltips=true
showTotals=true
units=0
updateIntervalMSecs=2000
version=5

---

### Post by gus_zernial on 2011-04-14
I was able to solve this, I'll post how for reference.

1) I created a new user called test and booted to that account.
The new account also had the krunnre segfault problem, so I assumed that the problem was not a .kde config file problem.

2) I booted into recovery mode and did an apt-get remove --purge on kubuntu-desktop, kdebase-workspace-bin and kdebase-workspace-data

3) I did an apt-get clean

4) I did an apt-get install on kubuntu-desktop, kdebase-workspace-bin and kdebase-workspace-data.

5) I did an apt-get dist-upgrade

and after all that the krunner segfaults went away. I'm far from a KDE expert, so I believe not all these steps are necessary, but they did solve the problem.

---

### Post by rosencrantz on 2011-04-14
Hmm, no plugins activated, so my idea seems to be wrong. I attached mine (had to rename to .txt for uploading) if you want to play around a bit.
Have you considered reverting your updates? I wouldn't try it on the whole KDE upgrade, but it might work if you have just a few suspicious packages.
You can find out about system changes with:
tail -n 5000 /var/log/dpkg.log | egrep 'install |upgrade '
and package versions with:
apt-cache policy packagename

I hope it's not some obscure config file. In that case, I'm stumped.

---

### Post by rosencrantz on 2011-04-14
OK, you obviously considered a downgrade. Glad you solved it :-)

---

