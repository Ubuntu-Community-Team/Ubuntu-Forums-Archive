---
title: "Wubi Ubuntu 12 install boot stops at logo screen"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by abexman on 2012-07-20
Hey folks. Ubuntu newb here. I was trying to follow the instructions here
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
and after "II. Install Xorg's xf86-input-wacom tar or clone the git repository for Lucid, Maverick, Natty, & Oneiric" and the step "a) Now compile the xf86-input-wacom tar (download, compile, and install xf86-input-wacom):", I was rebooting.

After that my Ubuntu just stops on the logo splash screen for Ubuntu with the little dots beneath it.

My suspicion is this has something to do with the fact I had previously been editing the Grub2 menu options at /etc/default/grub and the steps above seemed to overwrite whatever changes I had made. I could be wrong though.

This is a Wubi install with Windows 7. I ran the recommended repair on the Boot Repair disk but it did not seem to solve.
[http://paste.ubuntu.com/1102372/](http://paste.ubuntu.com/1102372/)

---

### Post by abexman on 2012-07-23
If I reinstall Wubi within Windows 7, would that completely wipe out my previous install? I know root.disk gets overwritten. But if I reinstall and then use my previously backed up (backed up now, in unbootable state) root.disk file. Or would that likely just result in me continuing to not be able to boot? In other words does this root.disk likely contain my corrupted boot configuration?

---

