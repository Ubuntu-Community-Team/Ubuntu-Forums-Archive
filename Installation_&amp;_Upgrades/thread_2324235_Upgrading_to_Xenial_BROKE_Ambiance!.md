---
title: "Upgrading to Xenial BROKE Ambiance!"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by ShinIori319 on 2016-05-12
Hello.
Not sure if this should go here, but this happened when I upgraded.
I've been using Ubuntu for a while now.
I had made a clean installation of 15.04 a while now which I upgraded to 15.10. It was a while since I last booted into Linux, so today I decided to upgrade to Xenial.

All I gotta say is I'm not very happy, cause the upgrade somehow BROKE the Ambiance theme, including windows and icons.

The icons have the default look, the title bars look white, making text unreadable, and the upper bar thing from Unity is completely transparent.

[ATTACH=CONFIG]269010[/ATTACH]

Any help would be appreciated. Thank you!

---

### Post by howefield on 2016-05-12
I saw this on one machine which came good after a reboot, so to get the simple and stupid question out of the way, have you rebooted since upgrading ?

Also if you are using proprietary graphics drivers did you remove them before upgrade ?

---

### Post by ShinIori319 on 2016-05-12
I have rebooted several times.

I'm using the nvidia-current package. Shoulda I had removed it before upgrading? If that's the cause, is there way to fix it? I tried removing and reinstalling it along with the libcuda package, but nothing.

---

### Post by cigtoxdoc on 2016-05-12
I have the same problem with two different types of PCs.  The first is a DELL Vostro 3500 laptop.  It uses nVidia graphics.  Problem occurs with both nouveau driver as well as the correct nVidia driver.  However, nVidia driver does not have spacing problems (see below).  Other two PCs have Intel i7-4770K processors with Haswell graphics.  I think I have latest Intel drivers, but I am not sure; also the two PCs have different features after the upgrade to 16.04.  One looks okay in terms of spacing of File Edit Package Settings Help on Synaptic (and evolution e-mail).  On the other one, the words are all jammed together.

John

---

### Post by ShinIori319 on 2016-05-13
I think I finally did it.

I uninstalled the NVIDIA drivers, then proceeded to reinstalling all packages by running this shell script:

```
\#\!/bin/bash   

for pkg in `dpkg --get-selections | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y --force-yes install --reinstall $pkg ; done
```

Then reinstall the NVIDIA drivers.

It would not automatically set the theme, so I had to manually set it to another theme, then to Ambiance, and it's worked.

---

### Post by cigtoxdoc on 2016-05-15
I have found that "Highcontrast" theme is essential to making things work correctly.  This includes two PCs with Haswell graphics and two with nVidia graphics (both older PCs).  PCs with nVidia graphics are running the 340.96 driver.  This appears to be a problem with horizontal spacing with two applications.  Synaptic and evolution 3.19.90 are the two were I see the problem.  The nVidia drivers have been reinstalled.'

John

---

### Post by cigtoxdoc on 2016-06-04
This problem has gotten worse over the past week with whatever ubuntu upgrades have been sent to me.  Now high contract theme gives unreadable window titles on dropdown menus.

Perhaps one of the Gurus of Ubuntu will read this and provide a solution.

John

---

### Post by X-RED_Tech on 2016-06-04
Perhaps a clean install of 16.04 will give better results. The latest LTS version also has the correct nvidia drivers version for lots of hardware we previously need a PPA in order to get newer versions. So, chances are that if you do a fresh install of 16.04 then go to additional drivers, select and apply the recommended proprietary version, reboot and everything will be fine.

---

