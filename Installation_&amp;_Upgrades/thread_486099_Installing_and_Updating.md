---
title: "Installing and Updating"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by hybernate20 on 2007-06-27
Maybe this is a stupid question, but I'm going to ask it anyway. It could be that I'm just not as familiar with the package manager as I am with other package managers.

Whenever I try to do an update either from synaptic, with "sudo aptitude update" or "sudo apt-get update", I get a bunch of errors saying things like "Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
  Sub-process bzip2 returned an error code (2)
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages [48.6kB]      
99% [18 Sources bzip2 1764352] [19 Packages 39122/48.6kB 80%]       34.3kB/s 0s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
  Sub-process bzip2 returned an error code (2)
"

for a bunch of different packages.

I also get alot of MD5Sum errors. I tried installing subversion and e17 and a few others, and I get a "E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.4.3dfsg1-1ubuntu1_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.4.3dfsg1-1ubuntu1_i386.deb:) MD5Sum mismatch" or similar.

Any ideas for me?

Thanks!

---

