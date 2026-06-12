---
title: "Got no network and cant update via chroot!  err help needed."
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-01-22
I'm no expert in networking iis normally just works. Router is ok as karmic is fine.

Lucid boots ok just no net. 

ifconfig just shows the lo local loopback but no eth0

Extract from chroot.

apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Translation-en_GB
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Translation-en_GB
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Translation-en_GB
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Translation-en_GB
  Could not resolve ‘archive.ubuntu.com’

---

### Post by ssam on 2010-01-22
did you mount the special directories into the chroot?

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

---

### Post by philinux on 2010-01-22
> **ssam said:**
> did you mount the special directories into the chroot?

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

Yes. My chroot access is done by my script. Updating has always worked fine until yesterdays updates.

edit

Managed to get in to lucid via recovery with networking and updated. Chroot is now worrking but booting into lucid still gives no eth0.

I can manually add a wired connection but this is lost on reboot.

Updated via chroot and rebooted. All fixed. Very weird.

---

