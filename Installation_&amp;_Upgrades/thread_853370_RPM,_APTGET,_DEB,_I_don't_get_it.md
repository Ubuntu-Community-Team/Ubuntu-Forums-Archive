---
title: "RPM, APTGET, DEB, I don't get it"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by NMbottlecap on 2008-07-08
So I'm getting used to linux and not windows or Mac, and I asked a friend how to install a plugin so I can listen to MP3s she asked if I'm using RPM, aptget, or debs.  So I don't sound like an idiot, which does Ubuntu use?  Thanks.

---

### Post by lazyart on 2008-07-08
apt-get is preferred, but debs are good too.

---

### Post by NMbottlecap on 2008-07-08
thanks! Also I your signature 
"It's all about choice, right? Then stop flaming Windows users. "

---

### Post by wdaniels on 2008-07-08
> **NMbottlecap said:**
> So I'm getting used to linux and not windows or Mac, and I asked a friend how to install a plugin so I can listen to MP3s she asked if I'm using RPM, aptget, or debs.  So I don't sound like an idiot, which does Ubuntu use?  Thanks.

RPM and DEB are package formats used by RedHat and Debian distributions respectively. Ubuntu is based on Debian and therefore uses the DEB package format.

Aptitude and apt-get are package management programs designed to use DEB package "repositories" and to handle things like the dependencies between packages. So commands like apt-get are really just automated ways of fetching and installing DEB files.

---

### Post by bapoumba on 2008-07-08
> **NMbottlecap said:**
> So I'm getting used to linux and not windows or Mac, and I asked a friend how to install a plugin so I can listen to MP3s she asked if I'm using RPM, aptget, or debs.  So I don't sound like an idiot, which does Ubuntu use?  Thanks.

To listen to mp3, enable the multiverse repositories (from synaptic) and install ubuntu-restricted-extras
[uwiki]RestrictedFormats[/uwiki]

---

### Post by Bablefish on 2008-07-08
I am both a Linux and Windows guy and I know what you mean about how it can get a little confusing. But there are 100s of DEB programs out there. I just install Amazon's music downloader and that was a DEB file.

---

### Post by NMbottlecap on 2008-07-08
sweet sweet MP3's, thanks for the advice! Now I just have 1 bug-a-boo left, dual displays.

---

