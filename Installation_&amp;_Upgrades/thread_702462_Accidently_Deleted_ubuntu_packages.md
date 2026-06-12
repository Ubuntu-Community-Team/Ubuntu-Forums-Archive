---
title: "Accidently Deleted ubuntu packages"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by mortizx on 2008-02-20
Hello, I accidently deleted a lot of packages in ths packet manager..  I can only boot to linux prompt... How can reinstall my ubuntu withour formating the drive

---

### Post by az on 2008-02-20
> **mortizx said:**
> Hello, I accidently deleted a lot of packages in ths packet manager..  I can only boot to linux prompt... How can reinstall my ubuntu withour formating the drive

boot into recovery mode and run

apt-get install ubuntu-desktop

---

### Post by mortizx on 2008-02-20
I tried it, im on my other pc...  It removed all the packages

---

### Post by mortizx on 2008-02-20
i tried sudo tasksel, returns "aptitude faliked (100)"

---

### Post by az on 2008-02-20
Did you mix repositories?  Did you try to use the package manager to install a binary package from another distro?

You will need to install the libc6 package from the version of the distro you want to use, then dist-upgrade to that, and then finally install the ubuntu-desktop package.

If that's too much trouble, back up your home drive and reinstall.  

Don't mix repositories.  Ever.

---

