---
title: "bluez upgrade error"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-15
anyone else having this? or know what I can do for it.


```
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
buzzmandt@buzzmandt-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  bluez
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/434kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 246974 files and directories currently installed.)
Preparing to replace bluez 4.45-0ubuntu1 (using .../bluez_4.45-0ubuntu3_i386.deb) ...
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bluez_4.45-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with unknown argument `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/bluez_4.45-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
buzzmandt@buzzmandt-laptop:~$

```

---

### Post by psyke83 on 2009-07-15
[Already filed.]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399543")

---

### Post by alphacrucis2 on 2009-07-15
I get this too.

---

### Post by dieresys on 2009-07-15
> **psyke83 said:**
> [Already filed.]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399543")
It was fixed in [#399482]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399482") but in order to get the fix, you need to update the package, and that is what is not working :mad:.
To manually apply the fix, you have to:
[LIST]
[*]sudo gedit /etc/init.d/bluetooth
[*]Find the "pkill -TERM bluetoothd" line
[*]Replace it with "pkill -TERM bluetoothd || true"
[/LIST]
Then you can update the package as normally :KS.

---

### Post by buzzmandt on 2009-07-15
worked like a charm, thanks for that

---

### Post by zika on 2009-07-15
> **dieresys said:**
> It was fixed in [#399482]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399482") but in order to get the fix, you need to update the package, and that is what is not working :mad:.
To manually apply the fix, you have to:
[LIST]
[*]sudo gedit /etc/init.d/bluetooth
[*]Find the "pkill -TERM bluetoothd" line
[*]Replace it with "pkill -TERM bluetoothd || true"
[/LIST]
Then you can update the package as normally :KS.Thank You!

---

### Post by Aries K on 2009-07-15
Works great thanks.

---

### Post by wayne_cat on 2009-07-15
got the same error ... bluetooth was stopped ... after

```
sudo /etc/init.d/bluetooth start
```no problems ... no need to edit the file

---

### Post by Slug71 on 2009-07-15
> **dieresys said:**
> It was fixed in [#399482]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399482") but in order to get the fix, you need to update the package, and that is what is not working :mad:.
To manually apply the fix, you have to:
[LIST]
[*]sudo gedit /etc/init.d/bluetooth
[*]Find the "pkill -TERM bluetoothd" line
[*]Replace it with "pkill -TERM bluetoothd || true"
[/LIST]
Then you can update the package as normally :KS.

Thanks, worked. :)

---

### Post by ubername on 2009-07-15
> **dieresys said:**
> It was fixed in [#399482]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/399482") but in order to get the fix, you need to update the package, and that is what is not working :mad:.
To manually apply the fix, you have to:
[LIST]
[*]sudo gedit /etc/init.d/bluetooth
[*]Find the "pkill -TERM bluetoothd" line
[*]Replace it with "pkill -TERM bluetoothd || true"
[/LIST]
Then you can update the package as normally :KS.

Thanks from me too!
(Wayne_cat: sorry, unless I misunderstood, your suggestion didn't work)

---

### Post by wayne_cat on 2009-07-15
> **ubername said:**
> Thanks from me too!
(Wayne_cat: sorry, unless I misunderstood, your suggestion didn't work)

Really ... strange ... I was not able to upgrade the package with a stopped bluetooth service. So I just started it ... apt-get dist-upgrade ... and apt was able to upgrade :-k

---

### Post by MacUntu on 2009-07-15
> **wayne_cat said:**
> Really ... strange ... I was not able to upgrade the package with a stopped bluetooth service. So I just started it ... apt-get dist-upgrade ... and apt was able to upgrade :-k

Well, the problem was that message:
```
invoke-rc.d: initscript bluetooth, action "stop" failed.
```

I simply replaced /etc/init.d/bluetooth with an empty file and reinstalled it later.

---

