---
title: "Squeeze as lucid's base?"
date: 2009-11-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2009-11-01
I was going through the Lucid release schedule on the wiki, and noticed that Debian testing was listed as the source for DIF.  But everywhere else, I've noticed that Sid is the base for it.

(Source: [https://wiki.ubuntu.com/LTSDebianImportFreeze](https://wiki.ubuntu.com/LTSDebianImportFreeze) )

So, can someone clarify what's going on here? 

Thanks!

---

### Post by SSTwinrova on 2009-11-01
As indicated with the page you linked to this is the **LTS**DebianImportFreeze, so they're just bringing in packages with less bugs to begin with. I don't remember the exact barrier for packages moving from sid -> testing, but they're still fairly up to date (maybe like a week delay?).

---

### Post by 23meg on 2009-11-01
[QUOTE=malachi1990]everywhere else[/QUOTE]

Where?

---

### Post by malachi1990 on 2009-11-01
On the Lucid Lynx schedule here, for one thing (it links to the standard DIF page).  I saw it somewhere else, but I can't recall exactly where.

---

### Post by slakkie on 2009-11-01
> **malachi1990 said:**
> I was going through the Lucid release schedule on the wiki, and noticed that Debian testing was listed as the source for DIF.  But everywhere else, I've noticed that Sid is the base for it.

(Source: [https://wiki.ubuntu.com/LTSDebianImportFreeze](https://wiki.ubuntu.com/LTSDebianImportFreeze) )

So, can someone clarify what's going on here? 

Thanks!

They focus on stability with Lucid. Therefor they sync with a more stable version of Debian. 

In Debian packages are moved from unstable to testing after 2/5/10 days depending on their urgency. Packages in testing may not break other packages, unlike packages in unstable. They must have a lower amount of release critical bugs.

Ergo, the base for Lucid is more stable then of Karmic. Karmic was based on packages in unstable.

Packages which have a higher version in Ubuntu will be used in stead of the Debian package.

---

### Post by malachi1990 on 2009-11-01
Thanks!

---

