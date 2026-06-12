---
title: "Location of these downloaded files."
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2010-03-16
After downloading deb files, at times (for e.g. with flashplugin-nonfree and wine), apt still downloads files like ariel32.exe, webdin32.exe, it downloaded a flash tarball.

So where does these files get downloaded to? They give problems during offline software installation.

---

### Post by overlord.gaurav on 2010-03-16
I don't know about the .exe files, but you can find the .deb files in /var/cache/atp/archives/

---

### Post by dE_logics on 2010-03-16
That's the place where the debs are stored...these files are different. They are downloaded while the debs are getting installed.

---

### Post by oldos2er on 2010-03-16
> **dE_logics said:**
> After downloading deb files, at times (for e.g. with flashplugin-nonfree and wine), apt still downloads files like ariel32.exe, webdin32.exe, 

Those files are part of the package ttf-mscorefonts-installer.

---

### Post by chaanakya_chiraag on 2010-03-16
I think they are stored in the /tmp folder, which means they get cleared out after a while.

---

### Post by dE_logics on 2010-03-16
Oh no...this is crap.

Actually this is a problem with apt.

---

### Post by mcduck on 2010-03-17
> **dE_logics said:**
> Oh no...this is crap.

Actually this is a problem with apt.

if anything it's problem with the .deb packages that handle the downloading, definitely not apt.

But I'd actually bet that there's a good reason to only store those .exe's in /tmp, as their license most likely prohibits distributing them (which is the exact reason why the files in them aren't included in the .deb packages themselves but are downloaded from the net instead).

---

### Post by dE_logics on 2010-03-17
Oh...I see.

---

