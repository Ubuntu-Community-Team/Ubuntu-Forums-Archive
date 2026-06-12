---
title: "fuse"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by mrpaulAU on 2007-12-04
I just installed Ubuntu on my computer after reformatting my hard drive. I'm working on getting it to recognize the external hard drive that I have and have been trying to install ntfs-3g-1.1120 and the fuse package. When installing fuse, I get the error message after the ./configure  make  make install  

make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/fuse" || mkdir -p -- "/usr/local/include/fuse"
mkdir: cannot create directory `/usr/local/include/fuse': Permission denied
make[2]: *** [install-fuseincludeHEADERS] Error 1
make[2]: Leaving directory `/home/paul/Desktop/fuse-2.7.1/include'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/paul/Desktop/fuse-2.7.1/include'
make: *** [install-recursive] Error 1

any help on this matter would be much appreciated. Thanks.

---

