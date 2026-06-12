---
title: "oh dear, another boot error!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mshale on 2007-04-21
I just installed a fresh copy of ubuntu and i get and error that tells me apt-get is not installed.  I can press ctrl-d and get past it, but this shouldn't happen.  I know that this error usually occurs after one remove a drive after installation.  I have removed nothing.  here is a list of my system's HD:

I have one promary ntfs partition with windows on it

i have another primary that is the SWAP

I have an extended partition that contains 2 logicals (one for ubuntu, and one for kubuntu)

and i have one other partition that i believe is a primary that plays cd's w/o booting an OS

Does anyone know what i can do a/b these errors?

---

### Post by jdong on 2007-04-21
What is /dev/sda6? fsck is telling you that it has no clue what UUID=87151bf8-6bfe-4664-9795-5952ae9a80d5 is referring to, which fsck claims is "/dev/sda6". Does this drive still exist? If yes, what does "vol_id -u /dev/sda6" report?

---

### Post by mshale on 2007-04-21
> **jdong said:**
> What is /dev/sda6? fsck is telling you that it has no clue what UUID=87151bf8-6bfe-4664-9795-5952ae9a80d5 is referring to, which fsck claims is "/dev/sda6". Does this drive still exist? If yes, what does "vol_id -u /dev/sda6" report?

I solved the prblem by reinstalling ubuntu.  it seems as though it didn' like that i installed kubuntu on that second logical partition.

Thanks for your help though!

---

