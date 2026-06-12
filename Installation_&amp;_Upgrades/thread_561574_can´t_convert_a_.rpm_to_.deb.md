---
title: "can´t convert a .rpm to .deb"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by roy92 on 2007-09-27
im trying to convert  a rpm to deb  using alien but when i type "sudo alien -d LimeWireLinux.rpm" i get this error: 

argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
chmod: invalid option -- /
Try `chmod --help' for more information.
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'

---

### Post by logos34 on 2007-09-27
The -d option ('--to-deb') is the default...try simply

sudo alien LimeWireLinux.rpm

anything?

Have you considered the open-source alternative to Limewire pro, Frostwire? (there's a .deb for it)

---

### Post by roy92 on 2007-09-28
ok, I installed frostwire and its running ok, but everytime i use alien that error appears, any idea of that error:confused:?

---

### Post by hoodlum on 2007-09-29
[here ]("http://limewirepro.at.tt/") a latest version of limewire pro and its a .deb. plus i dont think they make a limewire rpm anymore.

---

### Post by roy92 on 2007-09-29
yea, it worked... thanks hoodlum

besides i will continue searching about that error

---

