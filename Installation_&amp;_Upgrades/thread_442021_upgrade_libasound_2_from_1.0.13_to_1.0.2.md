---
title: "upgrade libasound 2 from 1.0.13 to 1.0.2"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by stijngysemans on 2007-05-13
For Cinerella to compile, I need a higher version of libasound. I just installed ubuntustudio and the "old" one is deliverd with it. How can I upgrade it to the higher version?

---

### Post by FuturePast on 2007-05-13
Um, version 1.0.2 is not higher than 1.0.13.

There are precompiled packages available. Is it necessary for you to build your own?

---

### Post by stijngysemans on 2007-05-14
Ok i get this message from the ./configure command (for Cinelerra)
```

checking for libasound headers version >= 1.0.2... not present.
configure: error: Sufficiently new version of libasound not found.


```
And as you see, I'm using Ubuntustudio

---

### Post by FuturePast on 2007-05-15
sudo apt-get install build-essential libasound2-dev

---

### Post by gravometric on 2008-03-16
I'm having the same error with a newer libasound requirement:
```

checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found.
```

I'm trying to manually compile alsa and alsa-utils  (I need 1.0.16 for my soundcard, but 1.0.14 is all that's in the repos).  the alsa-drivers package compiled without errors, but the "alsa-utils" package is what is giving me errors.  I'm running Ubuntu Studio with the 64bit kernel.

I ran Idconfig and it seems I've got plenty-a-version ahead of libasound:
```

$ sudo ldconfig -v |grep libasound
        libasound.so.2 -> libasound.so.2.0.0
        libasound.so.2 -> libasound.so.2.0.0
$

```

...so something "sufficiently newer" from the repositories is not going to help me out.  If anyone has an alternate route on how to install alsa 1.0.16 (not version .15 in the testing repositories), then I'm all ears.

also, I did try sudo apt-get install build-essential libasound2-dev
```

$ sudo apt-get install build-essential libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libasound2-dev is already the newest version.

```

---

### Post by vaibshah on 2008-06-17
Hi!
I am trying to install skype setup on my Ubuntu 6.06 computer. I have downloaded skype-debian_2.0.0.72-1_i386.deb, but double-clicking it shows an error "Error: dependency is not satisfiable: libasound2"

I tried the sudo command as below, to install necessary package. But it doesn't help.

Can you guide me pls?

My ultimate goal is to start using Logitech QuickCam Pro 9000.

Thanks ahead!

> **FuturePast said:**
> sudo apt-get install build-essential libasound2-dev

---

