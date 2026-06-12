---
title: "I can't install my new kernel"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by tseliot on 2005-06-21
I did

alberto@ubuntu:/usr/src/linux$ sudo dpkg -i kernel-image-2.6.12_2.6.12_i386.deb
Password:
dpkg: error processing kernel-image-2.6.12_2.6.12_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.12_2.6.12_i386.deb

Then I tried

alberto@ubuntu:/usr/src/linux$ sudo dpkg -i kernel-image-2.6.12
dpkg: error processing kernel-image-2.6.12 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.12

What's wrong?

---

### Post by defkewl on 2005-06-21
Are you sure your kernel image located in /usr/src/linux ?

---

### Post by tseliot on 2005-06-21
you're right! Sorry I didn't notice it was there (I'm very stressed for my Spanish exams).

Thanks

---

