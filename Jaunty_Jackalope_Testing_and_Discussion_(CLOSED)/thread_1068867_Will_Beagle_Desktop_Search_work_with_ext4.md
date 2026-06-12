---
title: "Will Beagle Desktop Search work with ext4?"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jongkind on 2009-02-13
Will Beagle Desktop Search work with the ext4 filesystem?

---

### Post by phrostbyte on 2009-02-13
I don't think Beagle knows about the filesystem itself. So yes.

---

### Post by jongkind on 2009-02-14
Well, beagle does know about the file-system. E.g. it will be relatively slow on Reiser4 because it cannot use extended attributes. 

My assessment is that it will work with Ext4, but I wonder how it will perform there. My hope is that anyone has some experience with this, so that I can decided whether I want to make the move to Ext4.

---

### Post by hugmenot on 2009-02-16
Beagle does not work for me at all at the moment. It doesn't start due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/gmime2.2/+bug/314217](https://bugs.launchpad.net/ubuntu/+source/gmime2.2/+bug/314217)

---

### Post by gnomeuser on 2009-02-16
Beagle will work with any filesystem that supports extended attributes. This includes ext4, and I am using that very technology on my ext4 system right now.

---

### Post by jongkind on 2009-02-16
Ah, that sounds good. Was it necessary to enable the extended attributes via the fstab file?

---

