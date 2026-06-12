---
title: "hello, I have install Ubuntu in another disk with &quot;portable_ubuntu&quot; with Windows XP"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2013-05-02
hello, I have install Ubuntu in another disk with "portable_ubuntu" with Windows XP, after 2 years the update writes "no space left on device", but I have 27 Gb, what can I do?

---

### Post by Bashing-om on 2013-05-02
spi_;

Additional info required for a quality response.
>  install Ubuntu in another disk with "portable_ubuntu" with Windows XP mean that you have installed ubuntu inside of Windows as a "wubi" installation?

What version of ubuntu are you running ? :```
lsb_release -a
```

If you have ubuntu in a separate partition, these terminal commands will yield the disk usage.
```
df -h
du -h --max-depth=1 | sort -hr
``` Looking about for extraordinary large directories.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by spi_ on 2013-05-03
I have installing ubuntu inside Windows as a "wubi" installation...

Version:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


what can I do?

---

### Post by Bashing-om on 2013-05-03
spi_;

I have no experience and little knowledge of "wubi". I am aware that there is a 30 GB limit on the entire size of the "wubi" application. As to how one trims out the excess files from with-in "wubi", I can not say; others who have the experience will provide assistance.
[INDENT=2]
there are a few things I choose not to know

[/INDENT]

---

