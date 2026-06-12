---
title: "Karmic dropping Glibc for Eglibc?"
date: 2009-05-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-05-07
Debian is dropping Glibc for Eglibc:
[http://www.h-online.com/open/Debian-changes-from-GLIBC-to-EGLIBC--/news/113228](http://www.h-online.com/open/Debian-changes-from-GLIBC-to-EGLIBC--/news/113228)
or
[http://blog.aurel32.net/?p=47](http://blog.aurel32.net/?p=47)

I wonder whether Karmic will follow? And whether this is also good news for Ubuntu?

---

### Post by gnomeuser on 2009-05-07
eglibc is really a patchset ontop of glibc, so it would not be the dreaded scenerio where we replace a big vital piece of the stack with something entirely new.

I agree that Mr. Drepper can be a little hard to deal with at times but he is incredibly talented and in most of the examples where he is protrayed as being mean to users it is because he gets pushed repeatedly. E.g. I think it's perfectly reasonable for him to refuse to support vendor patched versions.

As Mr. Drepper seems to consider ARM embedded crap and Ubuntu has it as a supported arch, eglibc might make sense as they do support ARM.

---

### Post by lithorus on 2009-05-07
> **gnomeuser said:**
> eglibc is really a patchset ontop of glibc, so it would not be the dreaded scenerio where we replace a big vital piece of the stack with something entirely new.

I agree that Mr. Drepper can be a little hard to deal with at times but he is incredibly talented and in most of the examples where he is protrayed as being mean to users it is because he gets pushed repeatedly. E.g. I think it's perfectly reasonable for him to refuse to support vendor patched versions.

As Mr. Drepper seems to consider ARM embedded crap and Ubuntu has it as a supported arch, eglibc might make sense as they do support ARM.
Reading through some of the bug reports, it's not that he's mean at times, but more that he refuses to give explenations and the whole "you don't pay me, so why should I listen to you?" is just not good for an OSS project which libc is.

He might be a good programmer but is it good to have him make the decisions aswell?

Also I don't think the ARM thing was much vendor specific. The patch seemed very valid and would probably have improved the code in general.

---

### Post by gnomeuser on 2009-05-07
> **lithorus said:**
> Reading through some of the bug reports, it's not that he's mean at times, but more that he refuses to give explenations and the whole "you don't pay me, so why should I listen to you?" is just not good for an OSS project which libc is.

He might be a good programmer but is it good to have him make the decisions aswell?

Also I don't think the ARM thing was much vendor specific. The patch seemed very valid and would probably have improved the code in general.

For what it is worth, having interacted with Drepper via the Fedora project, I have always found that he writes very well thoughtout explainations. He prefers to do so in papers instead of bug reports which is perfectly legitimate. He has some amazing papers up on his website examining many vital topics.

I also think it's perfectly valid for him to say "Take my word for it, if you demand a well thoughtout explanation remember that I am paid by Red Hat to work on glibc not to hold your hands - the information is out there do your own research or pay me to spend the required hours to provide a proper paper". To which donating a dollar is basically an insult, if you paid me that little after repeatedly wasting my time on bugzilla, it would show exactly the value you put on my time.

---

