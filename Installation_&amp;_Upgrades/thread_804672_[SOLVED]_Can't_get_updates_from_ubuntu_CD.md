---
title: "[SOLVED] Can't get updates from ubuntu CD"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2008-05-23
I've just upgraded to Hardy from Gutsy via the alternate CD.  The udate manager says there are four files needed and they are on the installation CD.  However, synaptic won't fetch them.  It says to put the installation CD in the drive (which I have done), but it won't see the CD.  Is there something I need to do still, or is there a workaround?

---

### Post by bwhite82 on 2008-05-23
Are you entirely sure that the packages on the CD are *updated* versions? One reason why Synaptic could be ignoring them is because they are either the same version or older. Also, double check that the CD is still in your sources.list.

---

### Post by Goldpin on 2008-05-23
> **Soldierboy said:**
> Are you entirely sure that the packages on the CD are *updated* versions? One reason why Synaptic could be ignoring them is because they are either the same version or older. Also, double check that the CD is still in your sources.list.

As far as I know they should be.  It's not that they're being ignored, it simply looks like the program is ignoring (or can't see) the installation CD.

---

### Post by bwhite82 on 2008-05-23
> **Goldpin said:**
> As far as I know they should be.  It's not that they're being ignored, it simply looks like the program is ignoring (or can't see) the installation CD.

If thats the case then issue the command (with the disk in the drive):

> sudo apt-cd add

---

