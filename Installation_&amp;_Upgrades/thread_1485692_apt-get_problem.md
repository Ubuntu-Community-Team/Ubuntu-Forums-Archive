---
title: "apt-get problem"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by cusri2004 on 2010-05-17
Hi there,

I accidentally removed python on my ubuntu 10.04 which paralyzed gnome completely. So I am trying quite a few things to get it back from Recovery mode. One of the things people suggest online is to do

sudo apt-get install ubuntu-desktop

However, this doesn't seem to be working for me. It just complains that it 

Could not resolve 'nz.archive.ubuntu.com'

Failed to fetch [http://nz.archive.ubuntu.com/(some]("http://nz.archive.ubuntu.com/%28some") junk regarding the package)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing.

And I try 

sudo apt-get update

Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg
Could not resolve 'archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid Release.gpg
Could not resolve 'nz.archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid-updates Release.gpg
Could not resolve 'nz.archive.canonical.com'

Err [http://nz.archive.canonical.com]("http://nz.archive.canonical.com/") lucid-security Release.gpg
Could not resolve 'nz.archive.canonical.com'

Reading package lists.....Done

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg) Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/...id/Release.gpg) Could not resolve 'nz.archive.ubuntu.com'

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/...ty/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/...ty/Release.gpg) Could not resolve 'nz.archive.ubuntu.com'

W: Somed index files failed to download, they have been ignored, or old ones used instead. 

And sudo apt-get update --fix-missing also spits the same error message as above.

Please help

---

### Post by cusri2004 on 2010-05-24
bump

---

### Post by wojox on 2010-05-24
Did you try:

```
sudo apt-get install python
```

---

### Post by jerome1232 on 2010-05-24
Try just switching servers, maybe that mirror is down.

System -> Administration -> Software Sources, drop the download from dialog and select another server. You can even have it ping them all and find the fastest one (it takes awhile to ping them)

**I totally missed that first part about removing python, ignore me. I'm addressing a completely different issue**.

---

### Post by dino99 on 2010-05-24
your packages are into /var/cache/apt/archives

sudo apt-get install -f

---

