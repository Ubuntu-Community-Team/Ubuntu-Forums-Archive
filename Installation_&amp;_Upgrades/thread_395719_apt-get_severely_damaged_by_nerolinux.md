---
title: "apt-get severely damaged by nerolinux"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by dedalesha on 2007-03-28
My apt-get on Ubuntu Edgy 6.10 is not capable of installing anything anymore after I have unsuccessfully attempted to install nerolinux package, which I got from Nero website.

I get an error: Unknown Error: exceptions.SystemError  E: The package nerolinux needs to be reinstalled, but I can't find an archive for it

I have wiped out the cache and the archives, but the error is still there for all GUI and console apt-get related calls.

Can anyone please help. How can I make it forget about the nerolinux package?

Thanks a lot

---

### Post by dedalesha on 2007-03-29
Fixed it.

Found the Nero package definition in /var/lib/dpkg/status file. The package was in reinstall status. Just removed the whole package section. Luckily it was pretty well formatted text

---

