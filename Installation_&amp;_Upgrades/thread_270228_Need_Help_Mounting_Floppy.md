---
title: "Need Help Mounting Floppy"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by anpan on 2006-10-02
I typed the following in the Terminal:
  sudo mount /media/floppy0

and get the following:

  wrong fstype
  bad option
  bad superblock on /dev/fd0
  missing code page or other error

Can anyone tell me where to go from here?  I am trying to mount the floppy.

Thanks.

Ted

---

### Post by randell6564 on 2006-10-02
> **anpan said:**
> I typed the following in the Terminal:
  sudo mount /media/floppy0

and get the following:

  wrong fstype
  bad option
  bad superblock on /dev/fd0
  missing code page or other error

Can anyone tell me where to go from here?  I am trying to mount the floppy.

Thanks.

Ted

I believe that 'FSTYPE' means file system type, so maybe you are being informed that Ubuntu can't read the format.

---

