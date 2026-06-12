---
title: "Can't install Bochs"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Rykyu on 2010-01-08
Hi everyone,

I'm trying to install Bochs x86 PC emulator. I've downloaded the "bochs-2.4.2-1.i586.rpm" package and installed alien to convert it in .deb package, but it doesn't work.
I tried some commands like "sudo alien --to-deb *.rpm", or "-i", "-T"... but it always answer me :
> error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package bochs: postrm prerm
Warning: Use the --scripts parameter to include the scripts.
Unpacking of 'bochs-2.4.2-1.i586.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.I know I'm not the first to be in trouble with alien, but I think that it works perfectly and that it's only I don't type the right command. Maybe I took the wrong package, I don't know...

Thanks in advance for your help.;)

---

### Post by gsmanners on 2010-01-09
You do know that Bochs is in the Ubuntu repository? Granted, it's not as up to date, but you're less likely to run into an installation problem.

---

### Post by Rykyu on 2010-01-09
It's a shame but until one hour after my post, I didn't try.
Now it's installed, but I still would like to know what was wrong, because if I always depend on apt-get...

Thanks nonetheless :)

---

### Post by gsmanners on 2010-01-09
Your mistake was in relying on a build that isn't right for or possibly even breaks the system you are using. If you want to go the compile from source route, that's fine. But I wouldn't rely on a Fedora package to work in a Debian-based distro.

---

### Post by Rykyu on 2010-01-11
Ok. Anyways, I've installed the last version by compiling source code.

Thank you for your answer ;) .

---

