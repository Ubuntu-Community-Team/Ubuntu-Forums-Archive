---
title: "Please help with LVM resizing"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Peepsalot on 2007-02-03
I have a computer that I want to install Ubuntu on.  It currently has Fedora Core 5 on there, with the root directory inside a logical volume.  I want to resize filesystem, then resize the volume, and create a new volume in the free space for Ubuntu.  I have never really used lvm before, so I am having some trouble.

From what I understand, one of the first steps I need to do is run resize2fs.
When I boot from a linux "rescue" CD to make the changes, I don't see the logical volumes under /dev , so is there some command I need to run to make these available?

Edit: oh, and this also begs the question: Can I install Ubuntu onto a logical volume?

---

### Post by Peepsalot on 2007-02-03
I figured it out, I had to run "vgchange -a y".

But I'm still not sure that I can install Ubuntu onto a logical volume.

---

### Post by Peepsalot on 2007-02-03
It appears I need the alternate install cd, which is now being downloaded.

Why am I still talking to myself? :rolleyes:

---

