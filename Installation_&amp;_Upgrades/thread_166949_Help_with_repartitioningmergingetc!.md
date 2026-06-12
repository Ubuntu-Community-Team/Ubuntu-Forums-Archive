---
title: "Help with repartitioning/merging/etc!"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by sitheris on 2006-04-27
Well I recently converted my file/print/VM/media server to Ubuntu from Windows XP and I must say it's working out great.

One thing I'd like to do though is re-arrange my partitions a bit and try to consolidate but I don't know where to begin. 

Here is what I currently have:

/dev/hda - 80gb drive (primary master)
--/dev/hda1 - 40gb, NTFS (from old Windows install)
--/dev/hda2 - 40gb, ext3 (Ubuntu Install)

/dev/hdb - 200gb drive (primary slave)
--/dev/hdb1 - 150gb, ext3 (files, media, etc)
--/dev/hdb2 - 50gb, ext3 (Virtual Machines)


What I would like to do is this:

/dev/hda - 80gb drive (primary master)
--/dev/hda1 - 50gb, ext3 (Ubuntu install)
--/dev/hda2 - 30gb, ext3 (Virtual Machines)

/dev/hdb - 200gb drive (primary slave)
--/dev/hdb1 - 200gb, ext3 (files, media, etc)


Can this be done without reinstalling/reconfiguring Ubuntu? If so, how could I begin? For example I think I could do this - delete hda1, merge unused space into hda2, would this automatically make hda2 the new hda1?  From there I could create a new partition hda2, move my VM files there.

Then I could simply merge hdb2 space into hdb1.

The question is what commands do I use to do all this?  Thanks

---

### Post by gerbman on 2006-04-27
[QUOTE=sitheris]Here is what I currently have:

/dev/hda - 80gb drive (primary master)
--/dev/hda1 - 40gb, NTFS (from old Windows install)
--/dev/hda2 - 40gb, ext3 (Ubuntu Install)

/dev/hdb - 200gb drive (primary slave)
--/dev/hdb1 - 150gb, ext3 (files, media, etc)
--/dev/hdb2 - 50gb, ext3 (Virtual Machines)


What I would like to do is this:

/dev/hda - 80gb drive (primary master)
--/dev/hda1 - 50gb, ext3 (Ubuntu install)
--/dev/hda2 - 30gb, ext3 (Virtual Machines)

/dev/hdb - 200gb drive (primary slave)
--/dev/hdb1 - 200gb, ext3 (files, media, etc)


Can this be done without reinstalling/reconfiguring Ubuntu?[/QUOTE]I am unsure what the effect of simply deleting /dev/hda1 would be, but assuming you have successfully moved your VM files to /dev/hda2, you should be able to delete /dev/hdb2 and resize /dev/hdb1 using GParted (a nice simple GUI for managing partitions). GParted is included on the LiveCD, but not in the default installation. Install with```
sudo apt-get install gparted
```and run with```
sudo gparted
```Make sure to unmount /dev/hdb first or it won't let you delete/resize partitions on the drive. As always, make sure to back up important data before messing with partitions. GParted displays the very accurate disclaimer that> Since GParted can be a weapon of mass destruction only root may run it.;-)

---

### Post by sitheris on 2006-04-27
Thanks, I'll check out gparted :)

---

