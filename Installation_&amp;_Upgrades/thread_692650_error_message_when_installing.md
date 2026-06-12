---
title: "error message when installing"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by kenny1948 on 2008-02-10
I keep getting this message when I try to upgrade or install anything new in Ubuntu Feisty

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cdrkit/icedax_1.1.2-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cdrkit/icedax_1.1.2-1ubuntu1_i386.deb)
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)

which connection was refused? I tried looking up the IP but it didn't tell me anything relevant.:confused:

---

### Post by yabbadabbadont on 2008-02-10
Looks like there is trouble with the US mirror.  Try choosing a different one when asked during the install.  (You may have to turn on the expert options in order to be asked)

---

### Post by kenny1948 on 2008-02-10
unfortunately I'm still too much of a "newbie" what do you mean by "the expert options"?:confused:

---

### Post by Partyboi2 on 2008-02-10
Go to Software Sources (System>Admin>Software Sources) on the first tab you will see "Download from" change that to a different server and see if that helps

---

