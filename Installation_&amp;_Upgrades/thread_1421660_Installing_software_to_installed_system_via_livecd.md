---
title: "Installing software to installed system via livecd"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by shikha985 on 2010-03-04
I am having trouble installing HPLIP (all versions) onto my system. When  I go to configure the source code, it goes into a loop checking for a  BSD install. So, to get around this I want to try and install HPLIP onto  the system via a livecd. How would I go about doing this?

---

### Post by stlsaint on 2010-03-04
Try inserting livecd and open your Software Sources menu and selecting the cd as where to install from. Then try and install that package again.

---

### Post by aysiu on 2010-03-04
I don't know the exact details of this, but I think you'd use something called *chroot*

Any reason in particular you think a live CD installation would be more successful than the normal installation?

---

### Post by ajgreeny on 2010-03-04
Why do you need to get it from anywhere other than the repos, or if you must have the very latest version, as a binary .run file from HP direct.  There should be no need to use source code for hplip for ubuntu.

---

