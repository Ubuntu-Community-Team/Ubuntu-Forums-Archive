---
title: "&quot;trying to overwrite '/bar/baz', which is also in package “foo&quot;"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by leorolla on 2010-03-31
If a given file in package X has a namesake in (version m.n.k of) package Y, shouldn't its deb file of package X contain information about conflicting with (version m.n.k of) package Y?

This error message can be considered a bug? Should one file such a bug?

---

### Post by lean on 2010-03-31
Yes.

Usually it is a problem with files that are moved from one package to another, but the old package is not updated. But it can of cause also be because of conflicting packages, but it is more rare, since it is usually known if new packages have duplicate functionality when they are created.

---

### Post by leorolla on 2010-03-31
But I mean, the mere fact that it does not contain in the .deb file the information that it conflicts with a specific range of versions of some other package, leaving the error message to appear only at the time of the user's unfortunate attempt to upgrade, should this be filed as a bug?

---

