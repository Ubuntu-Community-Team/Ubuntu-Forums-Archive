---
title: "Autoremove didn't work"
date: 2019-05-12
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2019-05-12
Hi:

After an upgrade (12.04 to 14.04) I wanted to remove the packages as I skipped that option during the upgrade. Then I ran autoremove but it warned that 87MB will be erased. 87MB? I did the same upgrade in another desktop PC and it erased around 2GB.

Now I can't upgrade as there is no room in the disk. Is there any other way to get rid of those obstacle packages? Are they located in a specific folder?

Yes I know I should do a fresh install but this is the situation: no room in disk and I need to remove those packages.

Thanks

---

### Post by CatKiller on 2019-05-12
You've upgraded from one unsupported version to a different unsupported version, with inadequate disc space. Do a fresh install.

Autoremove isn't magic.

---

### Post by rva1945 on 2019-05-12
I agree, but clean and autoclean did the job.

---

### Post by Impavidus on 2019-05-13
apt clean just removes the package files, that is, the archive format in which the software is downloaded. It doesn't uninstall the software. You could use synaptic and hunt for obsolete or manually installed packages (that's what it's called by synaptic), but simply formatting the hard drive will be faster.

---

