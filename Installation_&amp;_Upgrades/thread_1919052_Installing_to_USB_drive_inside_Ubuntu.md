---
title: "Installing to USB drive inside Ubuntu"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by briansrapier on 2012-02-02
I'm currently using 10.04 LTS and am interested in installing Ubuntu 10.04 LTS to a bunch of USB thumb drives for a project I have in mind. Using USB Creator copies the liveCD to the drive which, I'll admit, is faster than running off a CDROM, but I'd like to make them full blown installs, not just a live environment.

I'd thought about, perhaps, mounting the ISO and chrooting into the installer environment to run the install, but it's just an idea I have at this point.

I've read a little about using the live version combined with persistent filesystems, but the docs I've seen regarding it all seem to be rather dated. The newer docs state that there are inherent issues with 10.04 and newer versions of Ubuntu (and variants).

I'd appreciate a clue.

---

### Post by searchfgold6789 on 2012-02-02
See if this works: boot from a  newer version of ubuntu (10.10+, doesn't matter if from Live CD or whatever) and use the USB creator installed there by default to burn the image to a USB stick. There's an option to "save files and settings" in a fixed amount of space reserved on the disk, which you can optionally select, this will be exactly like having an Ubuntu install on a USB disk. For more info, go to pendrivelinux.com.

---

