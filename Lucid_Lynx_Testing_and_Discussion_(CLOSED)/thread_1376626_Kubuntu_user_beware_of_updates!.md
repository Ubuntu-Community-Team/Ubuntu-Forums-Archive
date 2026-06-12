---
title: "Kubuntu user: beware of updates!"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by slakkie on 2010-01-09
Hi, received this today on the kubuntu-devel maillinglist.

> 
Currently mesa in Lucid is broken and so no packages that build-depend on it 
can be built.  As a result, Lucid is currently a mix of 4.3.85 (Beta 2) and 
4.3.90 (RC 1) packages.  Getting mesa fixed will not be just a matter of a few 
minutes (hopefully today).

My recommendation is don't update any Lucid systems now.  It's unlikely we 
will see 4.4 RC1 fully built until at least Sunday and possibly Monday even on 
the fast architectures.

Scott K

Source: Message-Id: <201001091111.48796.ubuntu@kitterman.com>


---

### Post by vishalrao on 2010-01-09
link: [https://lists.ubuntu.com/archives/kubuntu-devel/2010-January/003801.html](https://lists.ubuntu.com/archives/kubuntu-devel/2010-January/003801.html)

---

### Post by ronacc on 2010-01-09
thanks for the warning .

---

### Post by plun on 2010-01-09
a new mesa package is uploaded, not available yet

[https://lists.ubuntu.com/archives/lucid-changes/2010-January/003056.html](https://lists.ubuntu.com/archives/lucid-changes/2010-January/003056.html)

--

---

### Post by Seren on 2010-01-09
> **slakkie said:**
> Hi, received this today on the kubuntu-devel maillinglist.

I did update and can't launch X anymore. There is a segfault in X. Glad to know I am not alone (so to speak).

Posted via Lynx browser...

---

### Post by vishalrao on 2010-01-09
> **Seren said:**
> Posted via Lynx browser...

good one! :lolflag:

---

### Post by Reiger on 2010-01-10
Seems safe now (upgraded & booted up fine).

---

### Post by VMC on 2010-01-10
> **Reiger said:**
> Seems safe now (upgraded & booted up fine).

Me too.

---

### Post by caryb on 2010-01-10
Phew I needed to shutdown to go to work tomorrow (15 hours from now) so am relieved it's fixed.

Cary

Yep I know don't use as your primary machine!

---

### Post by jjochum on 2010-01-11
Not fixed for me. On amd64, kdebase-runtime is still at version 4.3.85, which breaks lots of KDE related packages.

---

### Post by caryb on 2010-01-11
Must be a delayed reaction in the southern hemisphere as mine broke this morning.

Cary


& yes before you ask I am using the main server!

---

### Post by jjochum on 2010-01-12
Seems to be fixed now. A couple of packages are still at 4.3.85, nothing critical, however.

---

### Post by vishalrao on 2010-01-12
RC1 should be all ready now: [https://lists.ubuntu.com/archives/kubuntu-devel/2010-January/003829.html](https://lists.ubuntu.com/archives/kubuntu-devel/2010-January/003829.html)

---

### Post by biasquez on 2010-01-12
i have these issues:
- when i do login, X crashes and kdm restart, then i can login 
- after login, i have blank screen with pointer mouse available
- composite with opengl doesn't work but with xrender works (nvidia 195.30 driver installed)

how can i fix it?

---

### Post by MikeDK on 2010-01-12
This affects Ubuntu users to, crashed my lucid x86_64 ubuntu install 3 times could find out what was wrong, but found out that it was the mesa-libs and not the xserver.

doing a fresh install now on my hp 2510p. and ill see if updating the xserver without mesa libs willl work.
hope it'll work.

kind regards mikedk

EDIT: Can anyone of you tell me if the release of the fixed mesa-libs is available in the repos yet?

---

### Post by vishalrao on 2010-01-12
i believe i saw an update comment that "mesa is fixed now"...

---

### Post by MikeDK on 2010-01-12
well, some comments on LP says its probably not fixed, i just wanne be sure, cause it really diasable my system, cant do anything. and cant fix it if its already got crashed.

---

### Post by MikeDK on 2010-01-13
mesa still not fixed, 

regards mikedk

---

