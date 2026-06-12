---
title: "Synaptic won't let me force version"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by jovean on 2009-12-13
I followed the instructions available (in various places) to force a package version (Xvidcap ... I want the one I downloaded from Sourceforge, not the one in the repo, which won't  record audio).  But it won't do it.  I select "Force version" from the "Package" menu in Synaptic, choose the version I want, and click "Force".  The program works on something - but nothing happens.  No changes are available to apply ... is there a manual way to do this? Update Manager keeps pestering me ...

---

### Post by mtecknology on 2009-12-13
It sounds to me like you probably shouldn't be doing this in the first place....

If you want to isntall something from a different source, then you need to remove it from your system, before installing the other version.

It's highly not recommended to install from a different source though.

Your other option is to simply file a bug about it in launchpad.net.

---

### Post by lidex on 2009-12-13
> **jovean said:**
> I followed the instructions available (in various places) to force a package version (Xvidcap ... I want the one I downloaded from Sourceforge, not the one in the repo, which won't  record audio).  But it won't do it.  I select "Force version" from the "Package" menu in Synaptic, choose the version I want, and click "Force".  The program works on something - but nothing happens.  No changes are available to apply ... is there a manual way to do this? Update Manager keeps pestering me ...

As mtecknology states, uninstall previous version. Then, if it's a deb package, you can install using dpkg or gdebi gui.

---

### Post by jovean on 2009-12-14
I ***need*** the non-repo version because the version of Xvidcap in the repository doesn't support audio recording by default whereas the one on sourceforge ***does***.  Also, I ***did*** uninstall the repository version first, then install using gdebi ... 

And not to be thankless and annoying, but my question wasn't "should I be doing this?", but "how can I do this?"  The real problem is not that I can't install the non-repo version, but that I can't convince Synaptic/Update Manager that I ***REALLY***** do not want** the repository version.

---

### Post by lidex on 2009-12-14
If I understand what you're saying then you need to lock the current version so synaptic doesn't override??? Is that correct because that's not what one would infer from your initial question?

Select the package in right pane of synaptic and go to the "Package" menu. Select "Lock Version" - put a check in box - and synaptic will ignore updates.

---

### Post by jovean on 2009-12-15
Thank you lidex - I was confused about terminology and didn't even know it.  MarkingSolved.

---

