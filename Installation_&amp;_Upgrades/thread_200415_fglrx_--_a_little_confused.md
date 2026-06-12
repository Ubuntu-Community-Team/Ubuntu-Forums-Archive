---
title: "fglrx -- a little confused"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2006-06-20
Hi everyone,

might be a little dumb questions, but I am a little bit confused about the different versions of fglrx that are available for ubuntu.

First of all: I used to run the fglrx driver from the ATI website with Breezy with problems. =D> 

After Upgrading to Dapper, that driver got de-installed. So, I downloaded the driver again and installed it like described in this Wiki page: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The installation was successful:

```
timo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

But the next day, auto-update wanted to update *fglrxcontrol* to *8.25.18+2.6.15.11-1* and *fglrx-kernel-source* to *8.25.18+2.6.15.11-1*.

This confuses me. I know there is an flgrx driver in the repo's, but as I understood it, this is not the same binary as the one provided by ATI but an open source implementation.

And then, there is another version of in the restricted-modules, right?

So, should I install these updates, or better not?

What can you recommend me?

Bye,
Timo

---

### Post by Harbinger1080 on 2006-06-20
i'm having the same trouble.  i'm pretty new at this, but i believe that ubuntu sees the ati drivers as something that needs to be "updated" back to fglrx.  i was actually coming here to ask if there is a way to just remove them from the updates list, so i'm not nagged all the time for an update i'm never going to install.

---

### Post by Timokl on 2006-06-21
[QUOTE=Harbinger1080]i'm having the same trouble.  i'm pretty new at this, but i believe that ubuntu sees the ati drivers as something that needs to be "updated" back to fglrx.  i was actually coming here to ask if there is a way to just remove them from the updates list, so i'm not nagged all the time for an update i'm never going to install.[/QUOTE]

The relationship between these different drivers is confusing, indeed. Anyone to shed a light on the topic?

---

### Post by Lux Perpetua on 2006-06-21
I went ahead with the update when prompted, and I didn't have any further issues. fglrxcontrol and fglrx-kernel-source aren't essential parts of the driver, so at least it shouldn't break your 3D video driver.

Also, I'm sorry to say, there is no open-source fglrx, only the closed proprietary driver provided by ATI. The version in the repository is the same as the one offered by ATI.

---

### Post by Harbinger1080 on 2006-06-21
if i let the update install, though, it gets rid of my ATI Control Panel...

---

### Post by Lux Perpetua on 2006-06-21
[QUOTE=Harbinger1080]if i let the update install, though, it gets rid of my ATI Control Panel...[/QUOTE]Hmmm...good point.

---

