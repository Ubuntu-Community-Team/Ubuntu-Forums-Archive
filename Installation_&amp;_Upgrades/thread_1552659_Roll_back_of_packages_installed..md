---
title: "Roll back of packages installed."
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by niteshreddy on 2010-08-13
hey guys...

Can i rollback all the operations done by apt-get in a certain period of time.?

i installed too many libraries when i was trying to install a webcam driver from source.

thanks..!

---

### Post by earthpigg on 2010-08-13
hi,

0) system -> admin -> log file viewer -> dpkg.log is the log of what you've installed and uninstalled.

1) look in /var/cache/apt/archives to verify you still have older versions of the packages. that's what this folder is for.

2) uninstall the new versions of them.

3) install the older packages in your local apt archive.

---

