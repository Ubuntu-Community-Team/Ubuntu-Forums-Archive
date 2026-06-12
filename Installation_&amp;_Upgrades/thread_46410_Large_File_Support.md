---
title: "Large File Support"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by david_finlayson on 2005-07-04
I have an application that would like to make a 10+ Gb temp file. The program crashes at 2 gig. Is this a large file size limitation in Hoary? If so, How can I fix it?

> uname -a
2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux

Thanks,

David

---

### Post by rider343 on 2005-07-04
what is your filesystem?

---

### Post by art on 2005-07-04
most probably it's a limitation of the program. To check if there is a limit imposed by OS type 
ulimit -a in shell. It will give you the limits on filesizes on your system

---

### Post by doclivingston on 2005-07-05
Fat32 can't deal with files > 2Gb, but basically all of the other linux filesystems support files considerable bigger than that (exactly how big depends on the file systems).

---

### Post by nocturn on 2005-07-05
[QUOTE=david_finlayson]I have an application that would like to make a 10+ Gb temp file. The program crashes at 2 gig. Is this a large file size limitation in Hoary? If so, How can I fix it?

> uname -a
2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux

Thanks,

David[/QUOTE]

Probably the program itself.  I have files of 4-10 GB on a reiser filesystem.

---

### Post by david_finlayson on 2005-07-05
The filesystem is ext3.

david@elger:~$ ulimit -a
core file size        (blocks, -c) 0
data seg size         (kbytes, -d) unlimited
file size             (blocks, -f) unlimited
max locked memory     (kbytes, -l) unlimited
max memory size       (kbytes, -m) unlimited
open files                    (-n) 1024
pipe size          (512 bytes, -p) 8
stack size            (kbytes, -s) 8192
cpu time             (seconds, -t) unlimited
max user processes            (-u) unlimited
virtual memory        (kbytes, -v) unlimited

Assuming that I understand ulimit, the problem seems to be with the program, which is odd considering it's a GIS algorythm for processing massive rasters.

Could the error be coming from a shared library? I think that the program links to libstdc++-libc6.2-2.so.3

David

---

### Post by nocturn on 2005-07-05
To check if you can create large files, try this 

```

dd if=/dev/zero of=test.tmp bs=1024k count=4000

```

This will create a 4 GB file.

du -m test.tmp 
shows the size.

---

