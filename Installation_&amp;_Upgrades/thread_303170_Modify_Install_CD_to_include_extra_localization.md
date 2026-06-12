---
title: "Modify Install CD to include extra localization"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by brkamikaze on 2006-11-19
I'd like to modity the Alternate Install CD to include my country's language-{pack,support} stuff so I don't have to download the language packages for every system I install.

I'm also planning to install Edgy on a few computers that don't have internet access and I need the installation to be localized.

I would like to know how to include the packages so Debian's Setup would use them automatically, like it does with the -en locale.

---

### Post by K.Mandla on 2006-11-19
I don't have a direct answer for that, but the first thing that comes to mind is the [Reconstructor]("http://reconstructor.aperantis.com/"), which allows you to build a live CD (not an alternate CD, I don't think) with your settings as the default.

Another option might be to [set up a local repository]("http://www.ubuntuforums.org/showthread.php?t=42862") that has all the packages you use on a CD. Then you just have to *apt-cdrom add* and install the language packages you want. That would be ideal for your offline machines; you could install updates at the same time.

Or if you want, you could try installing from [the DVD version]("http://cdimage.ubuntu.com/releases/edgy/release/"). Unless I'm mistaken, that has *everything*.

---

### Post by brkamikaze on 2006-11-20
The computers don't have a DVD reader nor I do have a DVD burner ;/

I'll try the 2nd option and report my success when done. VMWare helps a lot :)

---

