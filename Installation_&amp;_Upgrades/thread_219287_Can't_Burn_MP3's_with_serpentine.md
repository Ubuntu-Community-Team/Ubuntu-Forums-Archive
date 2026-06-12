---
title: "Can't Burn MP3's with serpentine??"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by nixmega on 2006-07-19
Ok here's my problem, Put in my CD, click create audio CD (love that feature !!), pulls up serpentine and anything .mp3 isn't recoginzed as a file you can add. So I:

apt-cache search lame

apt-get install gstreamer0.10-plugins-ugly-multiverse

and I get this:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly-multiverse: Depends: liblame0 (>= 3.96.1-1) but it is not installable
E: Broken packages
root@nixmegas-ubuntu-ze4420:/home/nixmega#

(yeah i know, old slack user so i use sudo :P sue me.)

So is this just a broken dependency.. and if so how do you suggest going around it?? ](*,) Does anyone else have this same problem?

-Nixmega

---

### Post by will_in_wi on 2006-07-19
you need to enable the multiverse repos. You can do this most easily in synaptic.

---

### Post by FredB on 2006-07-20
and if you want to do it by hand :

sudo gedit /etc/apt/sources.list

and remove # before lines with multiverse in it.

---

