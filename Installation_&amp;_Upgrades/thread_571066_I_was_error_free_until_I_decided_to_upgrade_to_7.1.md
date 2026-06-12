---
title: "I was error free until I decided to upgrade to 7.10"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by dunnthetown on 2007-10-08
Ok, it was stupid on my part to upgrade to Gutsy. I was wondering, is there a way to revert to last upgrade, or do I have to wait until the 18th when Gutsy actually releases. Help appreciated. I can't install any software because of that upgrade. Another thing is that util-linux won't work and I can't install the language packs. Please help me.

---

### Post by dunnthetown on 2007-10-08
This is the message whenever I try to install packages.

```
E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured
```

---

### Post by dunnthetown on 2007-10-08
I meant after I try to install packages.

---

### Post by tgalati4 on 2007-10-08
>sudo apt-get clean

---

### Post by dunnthetown on 2007-10-08
> **tgalati4 said:**
> >sudo apt-get clean

I tried that and got the same thing.

---

### Post by dunnthetown on 2007-10-09
Can someone please help me! :(

---

### Post by dunnthetown on 2007-10-09
> **tgalati4 said:**
> >sudo apt-get clean

Here's what I got when I typed that in:

```
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

```

---

### Post by twist2b on 2007-10-09
you could backup the files and then re-install the older ubuntu....
or wait for gusty to come out...

---

### Post by louieb on 2007-10-09
Not much help here But for what its worth. I got the xUbuntu Gutsy beta alternate CD. Pop it in and was going to restart and do a new install. When a box opened and offered to upgrade using the CD. I clicked ok and several hours later wound up with a partially functioning xUbuntu Gutsy install.  At least I had a working desktop. But several programs gave errors said some stuff was missing.

:confused: Never have had a lot of luck with upgrades. Tried for a while to reinstall  broken packages. Got tired of that and am now doing a fresh install from the xUbuntu beta alternate CD.

---

