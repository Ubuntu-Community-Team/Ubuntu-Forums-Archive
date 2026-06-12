---
title: "problem installing version 8.04"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by nank on 2008-06-19
Hello!! I'm a newbie to Ubuntu, i'm expieriencing problems installing 8.04 it always says there are packages missing. So i'm guessing that they were missing from the old ubuntu version too. Is there anybody that can help me?

---

### Post by housam on 2008-06-19
are you trying to make a fresh install or just upgrading ? did you tried other distros of Ubuntu ? from where you've got your live CD ? you may have a defected CD .

---

### Post by avtolle on 2008-06-19
> **nank said:**
> Hello!! I'm a newbie to Ubuntu, i'm expieriencing problems installing 8.04 it always says there are packages missing. So i'm guessing that they were missing from the old ubuntu version too. Is there anybody that can help me?
You likely have a corrupted iso, a bad burn, or both. Check the md5sum hash of the downloaded iso against the one on the download page to be sure they match, character by character. If the hashes match, boot the CD, select verify CD from the menu. If the md5sum hashes don't match, you will need to download the file again (perhaps using a different mirror, or use a torrent if you know how), and, after running the md5sum check again, assuming all is OK, burn to CD as an image at a low speed (4x works for me; I also use CD-R for the medium). 

If there is a disk error, reburn the iso (if the md5sum checks out) as above; slowly, and preferably to a CD-R; then do the integrity check again.

---

### Post by nank on 2008-06-19
seems to be that some libc are missing and many times the error window appears while using different applications please heeeelp!

---

### Post by nank on 2008-06-19
Thanks but i' don't knowe how to do it.I'm sorry will you be so kind i'm at my first experience with computer and i only know the very basic.Thanks

---

