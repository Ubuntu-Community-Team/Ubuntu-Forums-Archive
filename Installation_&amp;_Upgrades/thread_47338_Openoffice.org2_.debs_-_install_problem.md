---
title: "Openoffice.org2 .debs - install problem"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by PMO6022 on 2005-07-08
I have previously installed OOo2 via the .debs at [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/]("http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/") by unpacking the tarball and running **sudo dpkg -i *.deb**.

I recently reinstalled ubuntu and am running into a problem with this method. I uninstalled the version of Openoffice that comes with the ubuntu install. I've downloaded [OOo_SRC680_m113_en-US_native_LinuxIntel_install_deb.tar.gz]("http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m113/Build-1/OOo_SRC680_m113_en-US_native_LinuxIntel_install_deb.tar.gz")
and tried the same method outlined above to install.  However, this time I get an error:

```
pmorris@ubuntu:~/OOo $ sudo dpkg -i *.deb
Password:
dpkg: error processing openofficeorg-base-1.9.113-linux-2.6-intel.deb (--install):
 package architecture (intel) does not match system (i386)
```

The architecture error repeats for each .deb. I've never had this problem before, and my understanding was that i386 == intel, but I'm getting this error. Is anyone else seeing this, or has anyone successfully installed from this source recently? Any ideas? I think this install method is much easier than the other ones outlined on this forum, and it has always worked flawlessly for me in the past.

---

### Post by mingus on 2005-07-08
Did you know that it is now in the universe repository?

---

### Post by PMO6022 on 2005-07-08
[QUOTE=mingus]Did you know that it is now in the universe repository?[/QUOTE]

The version in universe appears to be old - 1.9.79.2.  Anyway, at this point, I am more interested in *why* I am unable to install these debs.

---

### Post by gugus on 2005-07-08
Try with the command:
```

sudo dpkg -i --force-architecture *.deb

```

---

### Post by PMO6022 on 2005-07-08
[QUOTE=gugus]Try with the command:
```

sudo dpkg -i --force-architecture *.deb

```[/QUOTE]

Not much luck there.  If did install, with a bunch of warnings, but would not start.

---

