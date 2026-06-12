---
title: "Adding repositories / upgrading GIMP"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Kalrog on 2007-07-12
I am having some problems with GIMP currently - I can't open any of the jpeg files from my new camera via GIMP.  They open in other viewers just fine, but nothing will open in the GIMP.  I get an error saying that the plug in cannot open the file.  What I *think* is going on is that the brand new camera has some exif information that the GIMP can't handle and I don't know where the problem is.  I have tried to upgrade the GIMP to see if that helps, but the latest version I can find through the package manager is 2.2.13 and I am already running that.  The latest version of GIMP (stable) is 2.2.16 and I found that at debian.org but it had a download link instead of an apt-get or similar instructions.

So how do I go about getting packages that are newer than what is available through the default repositories?  How do I add the debian.org repository (is it possible) to get this package and its dependancies through apt-get or synaptics?  Is there an easier way to go about this?

Thanks!

---

### Post by ThrobbingBrain66 on 2007-07-12
Adding repos for packages that aren't compiled against the distro/version that you're running is a bad idea.  While it's theorectically possible, the potential for mass system breakage and headaches is too great, IMO.  If you aren't running Feisty, you could always upgrade to get the latest packages.  Otherwise it would be best to wait for Gutsy to be released.

Ubuntu philosophy is to be very stable.  The trade off is having relatively "out-of-date" package versions to accomplish this.

---

### Post by Kalrog on 2007-07-13
I agree with the waiting for a stable release philosophy - except when I am having a problem with the currently released version.  And that is the situation I am in now.  I would really like to have an image editor that works with my pictures now instead of waiting for Gutsy to be released.  Are there other decent imaged editors compiled for Feisty?  The viewers that I have work find, but the editor (GIMP) is currently lacking.

---

