---
title: "iso image as repository"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by srcmnk on 2007-04-25
Hi, I fresh installed feisty on my pc, but I don't have the CD any more, I've the iso image instead.
I've to configure the modem but this require the build-essential  and linux-headers package.
I was able to find how to mount the iso image:

sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso

now my question is: how do I add this to the repositories?

thank you for your help.

---

### Post by Metacarpal on 2007-04-25
Are you unable to download these from the regular Ubuntu repositories?

(Currently downloading iso to test theory on how to add to repos)

---

### Post by srcmnk on 2007-04-26
I need that packages to be able to connect through linux, at the moment I can only connect from my windows partition :-k

---

### Post by Compyx on 2007-04-26
I think adding this to your /etc/apt/sources.list should do the trick:
```

deb file:/media/iso / feisty main restricted

```

This is untested, I don't have time to test this now.

---

### Post by srcmnk on 2007-04-26
as soon as I get back home I'll try it out,

thank you :-)

---

### Post by srcmnk on 2007-04-26
it works! 

thank you so much =D>

---

