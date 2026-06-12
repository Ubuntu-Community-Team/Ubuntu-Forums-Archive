---
title: "Can't extract kernel source"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by talonstriker on 2008-05-21
Hi guys,
I tried to extract the kernel source and I'm a crapload of errors.  
Here's the command I used:
sudo tar -jxvf linux-source-2.6.24.tar.bz2

Here's the output:
tar: linux-source-2.6.24/arch/powerpc/platforms/44x/Kconfig: Cannot open: No such file or directory
(+ a million more similar errors with diff file names)

Any idea how I can extract the file? I doubt that the file is corrupted since I can browse through all its contents thru Ark.

---

### Post by tamoneya on 2008-05-21
can you check permissions.  If the permissions are wrong then it would try to make a directory, fail, then try to place a file in the directory and then discover that the directory doesnt exist.
```
ls -la
```

---

### Post by talonstriker on 2008-05-21
Eh I was attempting to extract it as root.... So it should have worked right?  Anyways I'll try that once I get home.
Thanks for the suggestion.

---

### Post by tamoneya on 2008-05-21
> **talonstriker said:**
> Eh I was attempting to extract it as root.... So it should have worked right?  Anyways I'll try that once I get home.
Thanks for the suggestion.

Sorry I forgot about the sudo part.  What is the current location of the tar.gz file.

---

