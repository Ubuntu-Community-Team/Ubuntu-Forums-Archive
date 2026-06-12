---
title: "great..."
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by sunrex on 2005-11-04
me being the stuiped one, chmoded the entire www dir....

now nothings showing on any folder...

so what do i do so i can get em back online again...

(i used 744 so is there a diff chmod command...)

---

### Post by mlomker on 2005-11-04
I'm not sure what it needs to be, but:

```

mlomker@mlomkernote:/tmp$ ls -l test
-rwxr--r--  1 mlomker mlomker 0 2005-11-04 19:40 test

```

The first rwx is Owner, the second Group, and the third is Everyone.

The values for the Read Write eXecute combination are 4 2 1.

To make RWX it is 7, for RW 6, R 4, etc.

---

