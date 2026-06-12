---
title: "No optical drive - making a bootable hardy install partition on the HDD?"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by linuxnube on 2008-07-09
I've only been using Ubuntu for a couple of days so I don't know if this is even technically possible, but here's what I'd like to do.

I want to be able to reinstall Ubuntu (8.04 at this stage) whenever I need to but my laptop has no optical drive. I've already created an /home partition, but was wondering if its possible to put the CD image onto another partition so I can boot from that on the HDD when I need to reinstall.

The machine boots from GRUB. The drive is currently partitioned into a five partitions:

1.Vista (NTFS)
2.Shared (ext3)
3. /home (ext3)
4. /Ubuntu (ext3)
5. Swap

I was thinking it might be possible to add one more partition with an image of the Hardy install CD, and have this show up in GRUB so I can opt to do easy reinstalls over partition 4 above when required (at the rate I tend to mess things up this might be quite frequently!).

Is this possible? I have no idea where to start with this, so if anyone could point me in the general direction to achieving this I would be most thankful.

---

### Post by Herman on 2008-07-09
:) Hello linuxnube,
Here is a link from Ubuntu Community Docs which explains what I think it is you want to do, [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux").
I tried that quite a while ago myself just for fun and it worked very well. Be aware that you should use the Linux terminal commands given for copying the files from the CD to the hard disk partition. Don't be lazy and copy the files by dragging and dropping in GUI. The reason is there are some hidden files that need to be copied and without those the system won't boot. I think it's a hidden directory called .disk if I remember correctly.

Regards, Herman :)

---

### Post by zvacet on 2008-07-09
Maybe [this]("http://unetbootin.sourceforge.net/") can be helpful to you.

---

