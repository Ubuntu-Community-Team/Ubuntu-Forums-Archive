---
title: "Repository sync on Windows"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by fedo2 on 2015-05-28
Hi to all,

I would like to sync the precise release of Ubuntu on my Windows. Reason is because my Windows is on a separate Internet line and I blew off my other Internet line if I sync it on my CentOS server.
Then I will copy all the files on a hard drive, network share or something and copy it into my CentOS server.

My repo Ubuntu on CentOS is working fine, I just kill my Internet link with first synchro... (like 60~80Gb to download).

Here is my CentOS script  :
```
#!/bin/bash
arch=i386
section=main,restricted,universe,multiverse
release=precise,precise-updates,precise-security
server=ch.archive.ubuntu.com
inPath=/ubuntu
proto=http
outpath=/var/www/html/ubuntu12
debmirror       -a $arch \
                --no-source \
                -s $section \
                -h $server \
                -d $release \
                -r $inPath \
                --progress \
                --ignore-release-gpg \
                --no-check-gpg \
                -e $proto \
                $outpath
 

```


How can I do the same but with Windows ?

Greats
Fedo

---

### Post by etescartz on 2015-05-28
I don't know Windows scripting and therefore I hate it. [Camicri Cube Server]("https://launchpad.net/cube-server") is what you're looking for.

Just have a look at their tutorial  [PDF]("https://launchpad.net/cube-server")

---

