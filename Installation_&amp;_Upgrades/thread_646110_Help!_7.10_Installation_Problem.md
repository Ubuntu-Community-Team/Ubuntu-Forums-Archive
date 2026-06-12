---
title: "Help! 7.10 Installation Problem"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by brucer41 on 2007-12-20
1. Burned 7.10 iso to a bootable CD.
2. Formatted existing hard drive (20 gig) for fresh install
3. insert disc, disc loads then crashes with error:
[60.669296] Kernel panic - not syncing: attempted to kill the idle task!
4. machine freezes and requires a full shutdown
5. does this for whatever option I choose

PC:
Compaq Armada M700 1 gig proc, 1 gig ram, 20 gig HD. No attached USB devices.

---

### Post by mouseboyx on 2007-12-20
Try reburning it or using the alternate install cd:


[http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-i386.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-i386.iso)

When you say formated for fresh install what does that mean? (what did you do)

---

### Post by brucer41 on 2007-12-20
I used a Bootdisk (dos) to format the drive because it was a Win2K install in NTFS and I had read that Ubuntu wouldnt install on an NTFS formatted drive.

I am downloading the alternative cd now, is there any particular command line to use in order to install?

Yes I am a newbie trying to convert from Windows!

---

### Post by jken146 on 2007-12-20
You get an option screen very much like the live CD.  Pick the first one and you go straight into a text-based installer.  No commands required.

Also, it is not possible to install to an NTFS partition.  Don't worry though, the installer will format it in ext3 for you.

---

### Post by sourcerer24 on 2008-07-17
I also just installed Ubuntu 8.04 in my ARMADA m700. The Problem I am having, however, is that I cannot connect to the internet even if I plug a LAN cable into it. The computer doesn't seem to recognize that I have plugged the cable. It must be a software problem because it was working fine with windows. any ideas?

---

