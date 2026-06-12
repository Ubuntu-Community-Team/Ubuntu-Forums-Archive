---
title: "errors on all deb-packages"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by gronne on 2008-06-12
I just installed ubuntu on a bigger hdd and it was a fairly easy install as usual, but now that I'm in it, it appears that (at least) all deb-packages cannot be installed. I believe it could be the hdd that's in error, but I'm not sure at all. I had to format it from the ntfs partitions I had on it, and made it an entire ext3 from the ubuntu install-cd. I've pasted the error I got from trying to install unrar:

 $ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/96.9kB of archives.
After this operation, 246kB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/unrar_1%3a3.7.8-1_i386.deb (--unpack):
 files list file for package `apport-gtk' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/unrar_1%3a3.7.8-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wolfen69 on 2008-06-12
try
```
sudo apt-get install -f
```

---

### Post by gronne on 2008-06-12
Thanks for the fast answer, but...

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by gronne on 2008-06-12
What does the E: stand for in the last line of the error I pasted(in the first post)? Does it stand for error?

---

### Post by avtolle on 2008-06-12
> **gronne said:**
> What does the E: stand for in the last line of the error I pasted(in the first post)? Does it stand for error?
Yes, it does, with the text following describing the error.

---

