---
title: "blkid inconsistency"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-08-04
Like the title says, this seems to wary between releases,

In Intrepid (8.10) it required sudo to work.
In Jaunty (9.04) it doesn't
In Karmic (9.10) it once again requires.

```
devil@core7:~$ blkid
devil@core7:~$ sudo blkid
/dev/sda1: LABEL="warehouse" UUID="0287d1b4-b14c-4596-b205-a523a69c7707" TYPE="ext4"
/dev/sdb1: UUID="c03558b0-76cb-4459-a386-b69093499d1a" TYPE="ext4"
/dev/sdb5: UUID="f9d1b276-9802-42a7-a565-d0b6013ee525" TYPE="ext4"
/dev/sdb6: UUID="d7b33c27-4e4f-4edb-b368-d0628fe235ca" TYPE="swap"
devil@core7:~$ ls -l `which blkid`
-rwxr-xr-x 1 root root 18888 2009-07-16 18:20 /sbin/blkid
```

Has anyone else noticed?

Next is a snippet from my friends machine, running jaunty
As you can see, no sudo is required.
```
user@machine:~$ ls -l `which blkid`; blkid
-rwxr-xr-x 1 root root 13772 2008-10-13 16:10 /sbin/blkid
/dev/sda1: UUID="85f0d968-4466-470d-8c1c-a49f450dcdb8" TYPE="ext3" 
/dev/sda5: UUID="2a1dc80c-6c14-44d4-8878-76c3aa80d6b9" TYPE="ext3" 
/dev/sda6: UUID="a898aa54-2279-4d73-a2d7-52c4f7360ac1" TYPE="ext3" 
/dev/sda7: UUID="f3395ddb-8d91-4c4e-b4f4-39d136c3bc51" TYPE="swap" 
/dev/loop0: TYPE="squashfs"
user@machine:~$
```

---

### Post by phenest on 2009-08-04
Confirmed. I'm guessing it should be with sudo. In that case, raise a bug report with Jaunty.

---

### Post by taavikko on 2009-08-04
> **phenest said:**
> Confirmed. I'm guessing it should be with sudo. In that case, raise a bug report with Jaunty.

I'm not certain this particular command needs an sudo in the first place, since all it does is print the device name + UUID and FS

But if someone with an actual Jaunty underneath or more experienced to innerbeing of util-linux will shed some more light on the issue?

But will be more than willing to raise the bug, in a minute.
EDIT// reported as: [https://bugs.edge.launchpad.net/ubuntu/+source/util-linux/+bug/408998](https://bugs.edge.launchpad.net/ubuntu/+source/util-linux/+bug/408998)

---

### Post by phenest on 2009-08-04
I'm not sure, but I reckon as it's accessing block devices, it should. Raise a bug anyway.

---

### Post by taavikko on 2009-08-04
> **phenest said:**
> I'm not sure, but I reckon as it's accessing block devices, it should. Raise a bug anyway.

Just edited the previous post, raised one.
Let Keybuk (Scott James Remnant) to decide if it's worth a bug or not...

---

