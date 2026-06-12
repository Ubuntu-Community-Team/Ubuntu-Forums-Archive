---
title: "How Do I Disable Certain Updates In Ubuntu?"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by sternael on 2006-08-01
On one of my computers in a remote location using a snaily DSL, every update is a pain. A single MB takes ages. I keep an old 386 "out of the box" kernel good for nothing, just in case, and to make the GRUB menu look more impressive ;) while I use the newest k7 kernel.

Ubuntu wants me to update my 386 kernel every time it boots, and it distracts me from "real" updates.

Is it possible to let the Update Manager ignore notifications for certain updates, like using Window$ Update?

---

### Post by swamytk on 2006-08-01
System->Administration->Synaptic->
Select the packages you don't want to update
From packages menu -> select "Lock Version"

---

### Post by Jagot on 2006-08-01
Or, from Terminal:

```
aptitude hold pkgname
```

You realise that you can remove the old kernel if you're using the k7 now?

---

### Post by bioman85 on 2007-11-20
A follow-up question to this:

In order to get an old CD-RW drive to work properly in Ubuntu I had to rebuild the hal package with someone's custom patch. I would like to force this version and not be asked to upgrade it. The issue is that the current version with the patch is the same as the version it is asking me to upgrade to, so forcing the version does not disable the prompt. 

What are my options?

Thanks

---

### Post by edgarinventor on 2008-01-03
Hey, worked fine with me, as long as Wings 3D won't fix that latest Linux version, the old one's locked!

Thanx !:)

---

### Post by doorknob60 on 2008-02-05
Sorry for bumping an old thread, but this worked great when I compiled the latest pidgin and it kept wanting to overwrite it with what it thought was a newer version :P Thanks!

---

