---
title: "Can't Install Gnome"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by Lurgid on 2005-08-23
I'm trying to setup a box to be used as an information kiosk. It used to be a custom NT based enclosure.

So, to install Ubuntu, I just did a minimal install, but had to do so in a bootstrap fashion, since the enclosure doesn't have a CD-ROM drive. I may be using the wrong terminolgy, but what I mean is that I put the hard drive in a different machine, did the first stage of the install there, and then put the hard drive in the kiosk enclosure for the rest of the install.

So, now I would like to install Gnome and some other packages, but when I do ```
$sudo apt-get install gnome
``` I get ```
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter
```
I don't have a CD-ROM drive in this enclosure, I just want apt-get to download and install gnome from the web. How can I do this, without putting this drive in a machine with a CD-ROM drive in it every time I want to install something new?

---

### Post by tonysathre on 2005-08-23
i would suggest instead of typing server at the boot prompt when u installed to just press enter

---

### Post by Lurgid on 2005-08-23
[QUOTE=tonysathre]i would suggest instead of typing server at the boot prompt when u installed to just press enter[/QUOTE]
 I've usually found it's easier to install with the minimum packages needed and then add the ones you need, rather than trying to uninstall the ones you don't need. Dependencies suck in that way.

Since this is going to be a limited use machine, and in an enclosure, with a static IP address, I don't need "desktop" packages such as dhclient, among others. Starting off with a "server" install seemed to make more sense to me, and I don't want to try to pull the hard drive out of this enclosure again, anyway.

---

### Post by Lurgid on 2005-08-23
I've added the following to my apt sources:
```
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
And now, instead of being asked to insert the CD I get:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or have been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
   gnome: Depends: gnome-desktop-environment (= 62ubuntu2) but it is not going to
 be installed
                Depends: gnome-office (=62ubuntu2) but it is not going to be installed
E: Broken packages
```

So, I then figured maybe I should install x.org first, and I get the "insert CD" error for that install.

---

### Post by mcduck on 2005-08-24
You must remove the CD from your sources.list. Just comment it with '#', and apt will no more ask for the CD but installs everything from the net.

---

### Post by ChristOff on 2005-08-24
I think you miss the 'main' (and eventually the universe and restricted if you want them) entry in your two first sources.list lines
It should look like this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted

---

### Post by Lurgid on 2005-08-24
[QUOTE=mcduck]You must remove the CD from your sources.list. Just comment it with '#', and apt will no more ask for the CD but installs everything from the net.[/QUOTE]
 I totally missed that first line in my sources.list. Glanced right by it, works now, thanks.

---

