---
title: "Why doesn't this bl*(*dy thing work?"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by bs554 on 2005-03-08
I am trying to install ubunt onto a ext2 formated partion but every time it tries to mount the cdrom the installer crashes and gives the error- 'cant mount the cdrom'. Is this partioned wrong and should it be FAT32 or something else.

---

### Post by az on 2005-03-08
"but every time it tries to mount the cdrom the installer crashes and gives the error- 'cant mount the cdrom"

What would this have to do with your filesystem on your disk?

If you make your way through the installation and the partitioner has problems with your disk, that is one thing.  It would seem that the installer is not getting very far along to even think about the problem being your filesystem.

Now, if my psychic poweres are keen, maybe you mean that you copied the iso to an ext2 filesystem and are trying to mount it as a loop device and boot from that.  Well, the warty installer has a lot of trouble doing that.  It sort of expects to be on a cd device.  I think the Hoary installer can do this.

---

