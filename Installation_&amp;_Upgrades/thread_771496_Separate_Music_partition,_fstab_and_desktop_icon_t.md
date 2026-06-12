---
title: "Separate Music partition, fstab and desktop icon trouble after Hardy upgrade"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Tharmas on 2008-04-27
I had my (bulky) music files on a separate ext3 partition, mounting in ~/Music/ using the following line in fstab:

```
# /dev/hda1
UUID=e66712cd-235e-469b-ae6d-1528b397a0f3 /home/mario/Music ext3 auto,users,rw   0       2
```

And I was happy in Gutsy.

Now I upgraded to Hardy and some annoying things happen:

1) I have a (silly) desktop icon called "80.0 GB Media". The partition is not mounted under /media, so why is this here? I wish I could get rid of it.

2) In the Places menu, instead of "(...), Documents, Music, Pictures, (...)", I have  "(...), Documents, _80.0 GB Media_, Pictures, (...)". It is strange, because in the nautilus book marks I have "Music", not "80.0 GB Media".

I know this isn't exactly critical, but not being able to solve it is getting on my nerves. Can anybody help me to keep my sanity?:confused:

---

### Post by SixedUp on 2008-11-02
I still see this on the newly released Intrepid Ibex.  I mount an additional ext3 partition within my home directory that contains almost all my data, and allows me to relatively easily move from release to release.  I do this using fstab (obviously), using a line like the following:

UUID=863ab845-8824-4afc-9959-e70bb74b573f /home/sixedup/data ext3 defaults,errors=remount-ro,noatime 0 2

However, when I boot, I get an annoying icon on my desktop saying "56GB media". 

There is some interesting advice in [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/114822](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/114822), which shows how in the past you could force a drive/partition to be ignored by gnome if it was mounted by fstab, however, that no longer works as written.

A little more research shows in the HAL changelog ([https://launchpad.net/ubuntu/+source/hal](https://launchpad.net/ubuntu/+source/hal)) that there were changes in this area in 0.5.10-1ubuntu1, which talk about making changes to HAL to only reflect "current status", with apparent removal of fstab awareness.

So, I assume that gnome currently either lacks the flexibility to show only show icons for drives that are *NOT* being specifically managed by fstab, or there is a bug somewhere.  I've worked around my problem with this by creating a rather draconian set of fdi rules copied into /usr/share/hal/fdi/policy/10osvendor/21override.fdi, as follows:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- Make sure /dev/sda8 which is mounted by fstab doesnt
       get messed about by gnome volume manager, and in particular
       doesnt get shown as a removable device on screen -->
<match key="volume.partition_number" int="8">
<merge key="volume.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>

But, this is clearly a dirty hack that depends on my knowing in advance the partition number I want to "blacklist".  I suspect we should probably have something better, but I don't know enough to take this much further (especially right now)

---

### Post by Tharmas on 2008-11-03
I'm glad to see that my old post wasn't ignored, and that I'm not alone.
But sad to realize that that the problem was real and was not solved in Intrepid.
I would have file a bug report but don't know really where the problem is (hal, nautilus, ...?)
Anyway, thanks for your dirty hack.

---

### Post by eap1935 on 2008-12-16
I've noticed that this only happens if you mount a partition in your home directory (or a subdirectory). This behaviour makes me think this is a "feature" of some sort, and deliberately implemented like this.

If you mount the partition outside your home directory, you won't see this, but if you really want the contents of the partition to appear in your home directory, you can use a soft link (ln -s <the real directory> /home/<you>/Music).

---

