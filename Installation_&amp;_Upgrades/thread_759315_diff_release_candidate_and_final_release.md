---
title: "diff release candidate and final release"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by XProgrammer on 2008-04-18
What is the difference between release candidate and final release of Ubuntu builds?. Will there be a slight debugs enabled in release candidate ?. 

if (0 == memcmp(release_candidate,final_release)) {
/* no difference */
} else {
/* What is the difference */
}

---

### Post by mgmiller on 2008-04-19
Here is what the Ubuntu devs have to say:
[https://wiki.ubuntu.com/ReleaseCandidate]("https://wiki.ubuntu.com/ReleaseCandidate")

---

### Post by TheMemphisExperience on 2008-04-19
> **mgmiller said:**
> Here is what the Ubuntu devs have to say:
[https://wiki.ubuntu.com/ReleaseCandidate]("https://wiki.ubuntu.com/ReleaseCandidate")

So...none.

---

### Post by mgmiller on 2008-04-20
Not unless some really nasty bug appears suddenly in the week between RC and final.  Not too likely, IMHO.

---

### Post by chadjohnson on 2008-04-20
If a nasty bug DOES arise, and we have the release candidate installed, would a simple aptitude full-upgrade give us the final release version?

---

### Post by mgmiller on 2008-04-20
> **chadjohnson said:**
> If a nasty bug DOES arise, and we have the release candidate installed, would a simple aptitude full-upgrade give us the final release version?

That would not be necessary.  In the normal course of system updates, it will be transformed (automagically) into the final release as soon as the packages are available in the repos.

---

