---
title: "Make apt-get MUCH faster using aria2!"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by antini on 2010-05-25
the author of [aria2]("http://aria2.sourceforge.net") was inspired by something that used another downloader to speed up apt-get.

First, if you don't already have aria2 installed,> sudo apt-get install aria2

aria2 gets the URI, filename, size, sha-256 hash from apt-get, creates a [metalink]("http://www.metalinker.org"), & downloads the files w/ aria2. the nice thing about aria2 is that it can get parts of files from different mirrors, but I don't know if this does that yet. it's already a couple times faster than regular apt-get.

[he writes]("https://sourceforge.net/apps/phpbb/aria2/viewtopic.php?f=1&t=52&start=0"):

apt-get -y --print-uris -qq' outputs needed package metainfo: URI, filename, size, sha-256 hash.
We can transform this output to just list of URIs and feed it to aria2.
aria2 can download multiple files at one so it is faster than axel at this point.
But wait, we have file size and sha-256 hash. Why not convert the apt-get output to metalink for more reliable download?
I wrote a simple Python script called apt2metalink.py to convert apt-get output to metalink4. Please use python2.6.

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
import sys
import re

if __name__ == "__main__":
    entries = []
    while True:
        line = sys.stdin.readline()
        if not line: break
        uri, name, size, chksum = line.split()
        uri = re.sub(r"^'|'$", "", uri)
        hashfunc, hashvalue = chksum.split(':')
        hashfunc = hashfunc.lower()
        if hashfunc == 'sha256':
            hashfunc = 'sha-256'
        entries.append((uri, name, size, hashfunc, hashvalue))
       
    print """<?xml version="1.0" encoding="UTF-8"?>
    <metalink xmlns="urn:ietf:params:xml:ns:metalink">"""

    for e in entries:
        print """<file name="{name}">
    <size>{size}</size>
    <hash type="{hashfunc}">{hashvalue}</hash>
    <url priority="1">{uri}</url>
    </file>""".format(uri=e[0],name=e[1], size=e[2], hashfunc=e[3], hashvalue=e[4])
    print """</metalink>"""

```

Now aria2 can validate checksums!

Let's take a look of actual usage example. First, save above script as 'apt2metalink.py'.
To get packages for upgrade, we can use following command chain:

```
apt-get -y --print-uris -qq upgrade|python2.6 apt2metalink.py|aria2c -d /var/cache/apt/archives/ -M- --file-allocation=none
```

After successful downloads, you can issue 'apt-get upgrade' to install packages.
You can replace 'upgrade' with list of packages to install or upgrade.

NOTE: I had to split the above in two like so:

> apt-get -y --print-uris -qq upgrade|python2.6 apt2metalink.py > tmp.meta4
> sudo aria2c -d /var/cache/apt/archives/ -M tmp.meta4 --file-allocation=none

---

### Post by jerrrys on 2010-05-26
i have installed it, but not used it yet...this is helpful...Thanks

---

### Post by antini on 2010-05-27
> **jerrrys said:**
> i have installed it, but not used it yet...this is helpful...Thanks

let us know how it works.

my updates with apt-get usually run in the 100-300k/sec range. using this method, it was 600k+/sec.

---

### Post by antini on 2010-06-04
The aria2 author Tatsuhiro writes in the same thread "I rewrote the script without Python. I put everything in one shell script."

You will need to use the latest aria2 (1.9.4 or later) to use this. VERY FAST!

```
#!/bin/sh -e

apt-get -y --print-uris -qq upgrade|awk '
    BEGIN {
      print "<?xml version=\"1.0\" encoding=\"UTF-8\"?>"
      print "<metalink xmlns=\"urn:ietf:params:xml:ns:metalink\">"
    }
    { gsub(/\x27/,"",$1);
      split($4, chksum, /:/)
      printf "<file name=\"%s\">",$2
      printf "<size>%d</size>", $3
      printf "<hash type=\"%s\">%s</hash>", chksum[1], chksum[2]
      printf "<url priority=\"1\">%s</url>", $1
      print "</file>"
    }
    END {
      print "</metalink>"
    }'|aria2c -M- --file-allocation=none -d /var/cache/apt/archives/
```

---

### Post by tatsuhiro_t on 2010-09-27
I rewrote scripts pasted in this thread and started apt-metalink project

[http://github.com/tatsuhiro-t/apt-metalink](http://github.com/tatsuhiro-t/apt-metalink)

apt-metalink allows you to download deb packages from several sources
concurrently and makes apt-get (dist-)upgrade process faster if you have fast
internet connection. apt-metalink uses python-apt to interface apt
infrastructure and aria2 as download back-end. Metalink is used to
feed package list to aria2.

---

### Post by antini on 2010-10-11
thanks! using it now, very nice!

---

### Post by ankh.red on 2010-11-17
can someone post a simple HOW TO for this aria2 for apt-get??

---

### Post by blazemore on 2011-07-05
I don't get this. Does it have apt-get syntax in the same way as apt-fast?

---

