---
title: "Arora browser crashes with sun-java6-plugin"
date: 2009-06-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-06-20
Like the title says, 
anyone else affected?

```
stat("/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so", {st_mode=S_IFREG|0644, st_size=78978, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=1883, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=1883, ...}) = 0
stat("/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so", {st_mode=S_IFREG|0644, st_size=78978, ...}) = 0
open("/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/amd64/libnpjp2.so", O_RDONLY) = 13
read(13, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220[\0\0\0\0\0\0"..., 832) = 832
fstat(13, {st_mode=S_IFREG|0644, st_size=78978, ...}) = 0
mmap(NULL, 1106952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 13, 0) = 0x7ffb9a414000
mprotect(0x7ffb9a421000, 1044480, PROT_NONE) = 0
mmap(0x7ffb9a520000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 13, 0xc000) = 0x7ffb9a520000
mprotect(0x7ffbab2c5000, 3556, PROT_READ|PROT_WRITE) = 0
mprotect(0x7ffbab2c5000, 3556, PROT_READ) = 0
mprotect(0x7fff1a684000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_GROWSDOWN) = 0
mprotect(0x7ffb9ade9000, 8388608, PROT_READ|PROT_WRITE|PROT_EXEC) = 0
close(13)                               = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```

renaming "libnpjp2.so fixes this (or installing openjdk)

---

### Post by xebian on 2009-06-20
> **taavikko said:**
> Like the title says, 
anyone else affected?

.....

No problem here.  I'm guessing this happens when starting Arora?  I do have the same java plugin installed as FF tells me so because there is none in Arora's preferences.  
It appears to me you have more serious problems with your setup as you reported FF crashing as well.

---

### Post by taavikko on 2009-06-20
> **xebian said:**
> 
It appears to me you have more serious problems with your setup as you reported FF crashing as well.

:D true, true... 
Time to do fresh install soon... already moved all my files to safety (which was a pain, file transfer slowed system)

---

### Post by taavikko on 2009-07-02
The current release from the repos have fixed this issue.

---

