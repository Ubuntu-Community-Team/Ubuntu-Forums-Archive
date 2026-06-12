---
title: "Eligible bootstrap partition not recognized by Ubuntu installer"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by DMorg on 2007-02-12
Greetings, I am new here but have been trying to get Ubuntu to run on my PowerBook G4 for several months now;

After many Google searches I found some helpful documentation from penguinppc.org and learned to use mac-fdisk, and then created a working partition scheme that actually allowed me to successfully install Debian Sarge and dual boot--

hda1: partition map
hda2: 800Kb HFS bootstrap partition
hda3: 256MB linux-swap partition
hda4: 5GB reiserfs root

However, whenever I try to install Ubuntu, the installer does not recognize that there IS a bootstrap partition and refuses to let me proceed with the installation;

"No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system."

Additionally, I have tried several times to create HFS bootstrap partitions with gparted, and have not succeeded in creating one that actually works and is recognized by the installer.

Feedback appreciated. I'm trying to get Ubuntu to work so that I can have a working GUI with which to view documentation so that I don't have to go back and forth betweein Linux and OS X.

---

### Post by DMorg on 2007-02-12
Another question: is this a common problem? Or am I just making a simple error?

Still trying...

---

