---
title: "Convert from rpm to deb problem"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by tortiman on 2008-10-06
I have maya in rpm format and need convert to deb for installing, but when it's converting with alien show this message error:

Unpacking of 'Maya2008_0-2008.0-142.i686.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.

What happen?

---

### Post by ronnielsen1 on 2008-10-06
[http://ubuntuforums.org/showthread.php?t=66859](http://ubuntuforums.org/showthread.php?t=66859)
This might help

---

### Post by tortiman on 2008-10-06
thanks ronnielsen1, my problem is in this point: 

for i in *.rpm; do sudo alien -cv $i; done

convert two files from rpm a deb, but in the third(Maya2008_0-2008.0-142.i686.rpm) show this error:


Unpacking of 'Maya2008_0-2008.0-142.i686.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.

---

### Post by tortiman on 2008-10-06
please someone know this!!!

---

### Post by tortiman on 2008-10-06
I don't think that I'm the one that had this problem!! I search in the web and this problem isn't common.

---

### Post by Forbees on 2008-10-06
when i convert rpm to deb i used 
```
 sudo alien -k blah.rpm
```

i've never heard of alien -cv >,<

might be the same thing, but try out alien -k

be sure the .rpm is in your home folder ( idk if -cv required that or not)

---

### Post by tortiman on 2008-10-06
Forbees thanks, but I can't convert to deb the file Maya2008_0-2008.0-142.i686.rpm. sudo -k don't work

---

### Post by tortiman on 2008-10-07
Nobody had this problem!! This error could be related with perl?

---

### Post by cariboo on 2008-10-07
Apparently you can get debs for Maya from the publisher, and your windows serial number works for the debian version.

Jim

---

### Post by tortiman on 2008-10-07
Hello Jim, where can I get the debs of maya? thanks

---

