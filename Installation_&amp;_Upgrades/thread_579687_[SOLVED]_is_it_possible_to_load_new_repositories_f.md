---
title: "[SOLVED] is it possible to load new repositories from an .iso image?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jai_mantravadi on 2007-10-18
Ok, so I tried to upgrade to the release candidate to beat the rush. Network upgrades didn't seem to work (tried all listed methods), so I thought "no big deal, just download and mount the iso" Right? Well, I can mount the iso image just fine, and upgrade off of the "cd" with my trusty loop device. Well, after I reboot Kubuntu asks me for a CD from which to upgrade a *ton* of packages. But... remounting the iso didn't help. I couldn't find a way to add my "cdrom image" image in either Adept, or apt-get. I wasn't sure if there was a way to hack the sources.list to point to a local file/drive. Anyways, I ended up burning a CD, but I thought that this might be a handy hack for next time there's an upgrade for those who download the CD/DVD iso and just want to upgrade. Any ideas? Thanks!
Jai

---

### Post by jetpeach on 2007-10-18
i'm not sure abou the answer to your question, but am looking to upgrade using the CD rather (with 4 ubuntu machines i'd rather not download on each...). i remember last time upgrading to feisty i had to use the alternate CD, since it actually has the DEB packages on it, but i can't remember if i got it to work.

---

### Post by jai_mantravadi on 2007-10-18
My question is how to keep from burning a CD, but just as an FYI here is what I did:

[Upgrade for Gutsy (look towards bottom)]("https://help.ubuntu.com/community/GutsyUpgrades") (hint: download the alternate install CD and just insert it with ubuntu running)

If you want to keep from burning a CD, then:
according to 
[How to mount/unmount CDs without burning]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

Use the following command to load loop module and then to mount an iso image
```

sudo modprobe loop
sudo mount debianetch.iso /media/isoimage/ -t iso9660 -o loop

```
What I want to know is, after reboot, the update manager/Adept looks for the CD in the cdrom drive, but I don't want to burn a CD. Does anybody know how to use the iso to get the updates to all the programs? I updgraded using the iso, but couldn't update all the packages using the iso and had to burn the CD. Andy ideas?

---

### Post by DavidTangye on 2007-10-18
> **jai_mantravadi said:**
> My question is how to keep from burning a CD, ...

What I want to know is, after reboot, the update manager/Adept looks for the CD in the cdrom drive, but I don't want to burn a CD. Does anybody know how to use the iso to get the updates to all the programs? I updgraded using the iso, but couldn't update all the packages using the iso and had to burn the CD. Andy ideas?I think you can change /etc/apt/sources.list - the line
```
 deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
```to something like ```
deb file://(path to your mounted iso image)
```Check the docs for apt. 'man source.list' gives: > file
           The file scheme allows an arbitrary directory in the file system to be considered an archive. This is useful for NFS mounts and local mirrors or archives.

---

### Post by jai_mantravadi on 2007-10-19
David,
Thanks! I'll try it out next time.
Jai

---

