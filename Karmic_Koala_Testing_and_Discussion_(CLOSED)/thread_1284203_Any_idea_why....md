---
title: "Any idea why..."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hotstovejer on 2009-10-06
There is 1.4 gb of info in my /usr/lib/grub/x86_64-pc folder? That seems a bit excessive, but is that something new in Grub2?

Thanks!

Jeremy

---

### Post by Leighman on 2009-10-06
Yeh, I've got a 540MB Grub now :/

---

### Post by dinxter on 2009-10-06
if you're using grub2, remove the package 'grub', its not needed. someone might want to file a bug perhaps, I don't like the idea of grub-pc not driving out a redundant 1.4gb package

---

### Post by FuturePilot on 2009-10-06
> **dinxter said:**
> if you're using grub2, remove the package 'grub', its not needed. someone might want to file a bug perhaps, I don't like the idea of grub-pc not driving out a redundant 1.4gb package

grub is 1.4GB? :-s That doesn't seem right. My /usr/lib/grub/i386-pc/ directory is only 1.1MB

Maybe see what ls -lh says is taking so much room.

---

### Post by sisco311 on 2009-10-06
> **FuturePilot said:**
> grub is 1.4GB? :-s That doesn't seem right. My /usr/lib/grub/i386-pc/ directory is only 1.1MB

Maybe see what ls -lh says is taking so much room.

```
ls -alh /usr/lib/grub/x86_64-pc/
total 1.4G
drwxr-xr-x 2 root root 4.0K 2009-10-06 19:34 .
drwxr-xr-x 4 root root 4.0K 2009-10-06 19:33 ..
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 e2fs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 fat_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 jfs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 minix_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 reiserfs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 stage1
-rw-r--r-- 1 root root 257M 2009-10-06 13:01 stage2
-rw-r--r-- 1 root root 257M 2009-10-06 13:01 stage2_eltorito
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 xfs_stage1_5

```

---

### Post by FuturePilot on 2009-10-06
> **sisco311 said:**
> ```
ls -alh /usr/lib/grub/x86_64-pc/
total 1.4G
drwxr-xr-x 2 root root 4.0K 2009-10-06 19:34 .
drwxr-xr-x 4 root root 4.0K 2009-10-06 19:33 ..
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 e2fs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 fat_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 jfs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 minix_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 reiserfs_stage1_5
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 stage1
-rw-r--r-- 1 root root 257M 2009-10-06 13:01 stage2
-rw-r--r-- 1 root root 257M 2009-10-06 13:01 stage2_eltorito
-rw-r--r-- 1 root root 129M 2009-10-06 13:01 xfs_stage1_5

```

Truly odd. I do not have an explanation. :?

---

### Post by emarkay on 2009-10-06
> **dinxter said:**
> if you're using grub2, remove the package 'grub', its not needed. someone might want to file a bug perhaps, I don't like the idea of grub-pc not driving out a redundant 1.4gb package

Well can you, or shall I - file the bug?

---

### Post by Longinus00 on 2009-10-06
> **emarkay said:**
> Well can you, or shall I - file the bug?

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/444703](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/444703)

---

### Post by VMC on 2009-10-06
I wonder if those that have excessive files upgraded from earlier release to karmic. I have less than 1mb in my "/usr/lib/grub/" folder.

---

### Post by gali98 on 2009-10-06
I don't even have that folder. I have an i386-pc folder (which is very small.)
And I *am* on 64bit...
This is from a straight beta install.
Kory

---

### Post by natros on 2009-10-06
fix released: [https://bugs.launchpad.net/bugs/444703](https://bugs.launchpad.net/bugs/444703)

---

### Post by sisco311 on 2009-10-06
> **VMC said:**
> I wonder if those that have excessive files upgraded from earlier release to karmic. I have less than 1mb in my "/usr/lib/grub/" folder.

the files are installed by grub_0.97-29ubuntu57_amd64
(decompression bomb :) )
```

[sisco@acme xtmp]$ ls -alh grub_0.97-29ubuntu57_amd64.deb 
-rw-r--r-- 1 sisco users 2.3M 2009-10-06 23:54 grub_0.97-29ubuntu57_amd64.deb

[sisco@acme xtmp]$ ar vx grub_0.97-29ubuntu57_amd64.deb 
x - debian-binary
x - control.tar.gz
x - data.tar.gz
[sisco@acme xtmp]$ tar -tzvf data.tar.gz
...
-rw-r--r-- root/root **268959632** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/stage2
-rw-r--r-- root/root **268960656** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/stage2_eltorito
-rw-r--r-- root/root **134504664** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/e2fs_stage1_5
-rw-r--r-- root/root **134504664** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/jfs_stage1_5
-rw-r--r-- root/root **134504664** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/minix_stage1_5
-rw-r--r-- root/root **134504664** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/reiserfs_stage1_5
-rw-r--r-- root/root **134504664 **2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/xfs_stage1_5
-rw-r--r-- root/root **134504664** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/fat_stage1_5
-rw-r--r-- root/root **134481080** 2009-10-06 13:01 ./usr/lib/grub/x86_64-pc/stage1
...

```

---

