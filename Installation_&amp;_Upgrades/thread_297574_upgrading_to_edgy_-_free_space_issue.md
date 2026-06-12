---
title: "upgrading to edgy - free space issue"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by rat1000 on 2006-11-11
I am running version 6.06 and am trying to upgrade to Edgy.  I followed the instructions on the site.  I get an error message saying

Not enough disk space.  Free at least 208 MB on /var/cache/apt/archives

I cleaned the archives as suggested by the error message.

My partitions are as follows:

/dev/hda1  /boot  101.94MB   68.42MB free
    /hda2  /usr   13.67GB  10.53GB free
    /hda3  /var   698MB    423MB free
    /hda5  /      698MB    418MB free
    /hda7  /tmp   502MB    435 free
    /hda8  /home  22GB     19GB free

I didn't realize var needed to be large to upgrade to Edgy.  Do I need to allocate more free space to /var?  If so, how to I go about doing this without destroying my data or reinstalling anything?

---

### Post by kidders on 2006-11-11
Hi there,

That depends on whether you want a "quick fix" or something more sensible & permanent.

If you temporarily require more space than you felt was reasonable when you designed your partitioning scheme, you could always try...

[LIST]
[*]Create a /dev/hda9 and mount it at /var/cache temporarily.
[*]Mount a ramdisk at /var/cache during the upgrade.
[*]Symlink /var/cache to a filesystem with more room on it (although cross-filesystem symlinks can occasionally cause apps to do odd things).
[/LIST]

The edgy upgrade requires rather a lot of .debs I'm afraid :-(

**Edit:** Another alternative might be to download & burn the Edgy CD and upgrade using that.

---

