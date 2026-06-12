---
title: "Recommended Disk Partitions"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by idheath on 2007-02-20
Hi,

I'm pretty new to Ubuntu (and indeed Linux).

I've done a 'scratch' install of Ubuntu to have a good look at it (I'm very impressed BTW :) ).

Anyway, now I want to install it 'properly' and would be interested in the best recommendations for the partitioning of my hard disk.  I only intend to install Ubuntu (i.e. no dual-boot).

By default the installation simple creates 2 partitions '/' & '/swap'.  Is this best practice?  Should I create other partitions (e.g. '/root', '/opt' etc.)?  If so what sizes should they be?

I have a 200Gb disk and am interested how I should chop-it-up or am I simply over complicating things?

Also is there a 'unix' naming convention to use when adding/mounting additional hard disks to a system?

Thanks in advance.

Cheers Ian

---

### Post by renzokuken on 2007-02-20
for ease, then two partitons /swap (~1.5gb) and / (~198.5gb) will be fine.

i wouldnt worry too much about seperating out the root folders too much. 

one tip i have found very useful though is to create a seperate partition for your home folder to keep all your docs/vids/music/settings seperate from your install path so you can reinstall if needed without touching the home directory.

it may look something like

/swap      ~1.5gb
/             ~15gb
/home     ~180gb

---

### Post by orb9220 on 2007-02-20
Yep that is what I do and a clean install I still have all my settings and installed apps.

winXP is first partition as hda1
/ 10Gb is root and second as hda2 
swap 984mb is hda3
/home 60GB is hda4

This my dual boot xp and edgy setup with a second Hd as a fat32 114gb for music pics etc.... that xp and ubuntu can both read and write to.

---

