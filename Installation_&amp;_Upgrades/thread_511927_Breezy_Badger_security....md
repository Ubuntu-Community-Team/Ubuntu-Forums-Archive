---
title: "Breezy Badger security..."
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by jcr723 on 2007-07-28
About 6 mo. ago, I bought the book "Beginning Ubuntu Linux" by Keir Thomas.  My intention was to see if I would prefer using Ubuntu Linux instead of Windows.  The book came with a live CD to allow dual booting Windows XP.  I installed it and everything worked fine:  I can choose which OS to use at boot up.

About 2 weeks after setting up the dual boot option (i.e. about 51/2 mo. ago), I unexpectedly found that I had to use Windows almost exclusively.  So I neglected Linux.  Finally, I now have some flexibility to re-examine Linux.  

My question:    Is Breezy Badger 'secure'?  Unlike 6 mo. ago, I can't risk compromising my Windows XP installation so I don't particularly want to upgrade.  I'm paranoid that my next upgrade won't go as smoothly as the last.  I just want to learn about Linux but if there's some reason that use of such an old version is inadvisable, I'd like to know.

Thanks in advance for any help.

John

---

### Post by rillip on 2007-07-28
I don't think any really important security upgrdes have been made.  If you were running a web server, I'd say no way, but Breezy Badger should work fine as a desktop.

Coincidently, you should be able to upgrade just by using

sudo apt-get distro-upgrade

And not having to reinstall.  It could break your Breezy, but there's no danger to Windows like this.  Worse case scenario, you can always boot the LiveCD and install over only the partitions you have back to Breezy Badger if it doesn't work.

---

