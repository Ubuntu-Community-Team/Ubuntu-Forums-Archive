---
title: "Uninstall a deb package"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by motorcity909 on 2009-12-01
Hi all

I installed [Cover Thumbnailer]("http://software.flogisoft.com/cover-thumbnailer/en/") from the package on the website.  I've decided I don't want it, so removed it with Synaptic.

However, the folder thumbnails it generates are still appearing in Nautilus in my Music and Pictures folders.  [See screengrab - the CD graphic appears as my album cover jpegs are in sub-folders.]

I've rebooted, still the same, so would appreciate any help.

Thanks.

---

### Post by motorcity909 on 2009-12-01
Quick update - I can get rid of the CD graphic so it reverts to the normal folder icon by switching thumbnail view to *never* in Nautilus' preferences.

However, that means I don't get previews of any other documents in, say, my Documents folder, which I do like.

Just to explain - it's the first sub-level of folders within Music and Pictures that I simply want to have the standard folder icon not that CD graphic or a thumbnail of jpegs.

I hope I'm making sense here!

Thanks.

---

### Post by motorcity909 on 2009-12-01
All sorted.  Normal folder icons back for Music and Pictures folder with thumbnail previews still there for files and pics themselves.

As they say in the IT Crowd - have you tried turning it off and on again?

---

### Post by FLOZz on 2009-12-01
Just a little information : you can clear the ~/.thumbnail directory for removing thumbnails ^^

```
rm -rf ~/.thumbnail
```

---

