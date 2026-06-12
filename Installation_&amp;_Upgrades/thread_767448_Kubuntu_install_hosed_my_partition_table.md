---
title: "Kubuntu install hosed my partition table"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ElTimo on 2008-04-25
I'm not quite sure HOW it did so, but here's what happened:

I was noticing that my Kubuntu install (which was originally had GNOME) was running noticeably slower. I figured this must be due to lots of packages that didn't get uninstalled when i made the switch to KDE, so i decided to do a clean install of Kubuntu.

My hard drive is set up with a 40 GB partition as sda1, which is mounted as the root directory. Then I have a ~205GB partition for my files and such, sda3, which is mounted at /home. The rest of my drive (about 6-7 GB) is used for swap.

Currently, I am writing this from the LiveCD environment, and when i try to look at either sda1 or sda3 I get a weird error "the enclosing drive for the volume is locked." When I try to run the 'rescue' command in parted, it says "Unable to open /dev/sda - unrecognised disk label." Does this mean that the partition table for my disk is MIA? or is there some way to resurrect this drive and its contents? I have several important assignments for school stored in my home directory, so this is of great importance to me.

Any help at all will be rewarded with candy.

No seriously, I'll give you candy if you can fix this.

---

### Post by ElTimo on 2008-04-25
Almost forgot my system specs:

Dell Latitude D820
2.0 GHz Core 2 Duo
250 GB SATA hard drive
NVidia Quadro 110m 256 MB

If there's anything else important that I missed, just ask.

---

