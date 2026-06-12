---
title: "Changing mini.iso's version"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by hufman on 2008-05-24
Is there a way to easily change which version of Ubuntu the Minimal CD Image installs from within the installer menu? I would like the use the same burned image to install any version of Ubuntu, so that I don't need to download and burn a new ISO every time a new version comes out.
Does the Minimal CD Image include this support?

---

### Post by zvacet on 2008-05-25
I don´t think so,because every new version comes with different kernel(that is one rreason which comes to my mind righ now).And if you can do that what is the point?Minimal CD is about 10MB big(if we can say big for that size).

---

### Post by hufman on 2008-05-25
I think it should be possible, since it grabs the kernel and other packages from a certain directory on an APT mirror. It should just be possible to change which directory to grab the packages from.
I think this would be useful to save on CDRs and reduce how many CDs are floating around the room. It would also make testing new versions of Ubuntu easier, because I wouldn't have to download a new CD for every new Beta or RC, I just tell mini.iso to load a different copy of the repository.
Where does mini.iso store its settings for the Installation program? Perhaps I could handtweak them, maybe?

---

