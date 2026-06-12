---
title: "Problem with unpacking kernel sources"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by rostfrei on 2008-06-02
Hello!

I'm trying to get kernel sources for my Ubuntu box with:

```
>apt-get source linux-image-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 60.5MB of source archives.
Get:1 http://archive.ubuntu.com gutsy-updates/main linux-source-2.6.22 2.6.22-14.52 (dsc) [2264B]
Get:2 http://archive.ubuntu.com gutsy-updates/main linux-source-2.6.22 2.6.22-14.52 (tar) [56.9MB]
Get:3 http://archive.ubuntu.com gutsy-updates/main linux-source-2.6.22 2.6.22-14.52 (diff) [3536kB]                                                         
Fetched 60.5MB in 3m56s (256kB/s)            
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22.orig.tar.gz  Hash Sum mismatch
E: Failed to fetch some archives.
```

as you can see there is "Hash Sum mismatch". I tried this several times with different package sources.

Next thing I tried is getting sources from [http://kernel.org](http://kernel.org) . Problem is I get similar errors with those sources to:

```
>tar xzf linux-2.6.22.tar.gz
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

or

```
>tar xjf linux-2.6.22.tar.bz2

bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Weird thing is that if I get older kernel sources there is no problem while unpacking.

```
>tar xzf linux-2.6.0.tar.gz
```

I also tried some more recent versions with the same problem. I even downloaded the most recent tar version, compiled it and tried, but it didn't help.

What is going on? Anybody else had experienced something like that? Did something changed in tar, bzip, gzip?

My system info:
Linux 2.6.22-14-generic (Ubuntu 7.10)
tar 1.18
bzip2 1.0.4
gzip 1.3.12

Regards,

---

### Post by rostfrei on 2008-06-02
I found out there is a problem with our company network. I guess they have some kind of proxy/caching problem which corrupts some downloads.

---

