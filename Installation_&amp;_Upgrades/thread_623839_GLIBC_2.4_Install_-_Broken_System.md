---
title: "GLIBC 2.4 Install - Broken System"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Zarathu on 2007-11-26
Well, the title is self-explanatory.  I made the dreadful mistake of compiling Glibc manually, and I accidentally added a flag that basically borked the system.

```
[root@projectpen tls]# ls
ls: relocation error: /lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
[root@projectpen tls]# rm
rm: relocation error: /lib/tls/libc.so.6: symbol _dl_out_of_memory, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference

```

The binaries are screwed.  Any way out of this other than a reformat?

---

### Post by PmDematagoda on 2007-11-26
Can you do sudo dpkg -i ? If you can't then you don't have that much of an option.

---

### Post by Zarathu on 2007-11-26
```

[root@projectpen tls]# dpkg
-bash: dpkg: command not found

```

Alright, so what's the deal?  Reformat?

[It's actually a CentOS system, but those forums are godawful in comparison.]

---

### Post by PmDematagoda on 2007-11-26
Since I do not have much of an experience in CentOS systems I cannot really say what alternatives there are other than a clean reinstall of the system.

---

### Post by Zarathu on 2007-11-26
Eh, it was time anyway.  I have an OpenBSD 4.2 CD here and it is absolutely begging me to install it somewhere.

Thanks, brotha.

---

### Post by PmDematagoda on 2007-11-26
I'm very sorry I couldn't be of more help. I wish you luck with your new installation.

---

