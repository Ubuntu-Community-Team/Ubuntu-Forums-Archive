---
title: "New glibc, libc.so.6"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by elmasto on 2008-03-11
I compiled and installed a different version of glibc on my system (per instructions [here]("http://tldp.org/HOWTO/html_single/Glibc-Install-HOWTO/").
Everything seemed to go OK. 
However, when I try and find the version of glibc I am currently using, it comes out as the previous version. What is more, looking at the symlink for libc.6.so and ld-linux.2.so (in /lib) still point the previous library(I am downgrading from glibc2.7 to glibc2.5.1, for school reasons) althogh I have the new version lying around lin /lib.
How can I make the system aware of the new library and start using it (have already run /sbin/ldconfig)?
Thanks a lot,

---

### Post by ubuntubrian on 2008-04-09
I'm having the same problem and can't find a solution anywhere. I'm trying to run RealPlayer and get in a terminal:
/bin/true: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
I don't really need Real Player but would like to figure this out.
Hardy Beta ppc on G3 Powerbook

---

