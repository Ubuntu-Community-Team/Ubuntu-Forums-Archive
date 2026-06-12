---
title: "Ubuntu 10.04 Lucid on AMD64"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by az990tony on 2010-06-14
I am unable to install Ubuntu 64-bit Desktop Edition on my AMD64 machine, but the 64-bit Ubuntu Server installs fine.  I am tempted to give up trying to get Desktop installed, and just go with Ubuntu Server and add ubuntu-desktop on top of it.  Has anyone else seen this problem?

The reason I ask is that I will be getting a 64-bit Intel i5 machine next week, and was hoping to install Ubuntu Desktop on it, but am wondering if I should go with Ubuntu Server and then install desktop afterwards.

Please advise.

---

### Post by darkod on 2010-06-14
It's not because it's 64bit. It might be for example video driver issue, the server version doesn't have graphical interface so it might look like working better.

I am running Lucid 64bit just fine on my Athlon 4850e, and I was running Karmic 64bit before that.

Try to boot in live mode. If it doesn't work, try hitting any key at the first splash screen, that should show you a menu. Hit F6 for advanced options, select Safe Graphics if there. Then the Try ubuntu option to load live mode.

If that worked, it's video issue.

Other things to try with F6 is nomodeset, noacpi, etc. It's a hit and miss until you find out what helped you.

---

### Post by az990tony on 2010-06-17
Darkod,
Thanks!  Actually doing the "apt-get install ubuntu-desktop" seemed to solve all my problems.  However, if I need to re-install, I will try out the different options you mentioned.

I got my new i5 64-bit Intel laptop yesterday, and I was able to install the "Ubuntu 10.04 Desktop" just fine, so it is probably my hardware as you suggest.

-- Tony

---

