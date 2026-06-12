---
title: "problem with gcc"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Ronen1001 on 2010-05-07
i cant install gcc 4.5.0 because i still dont have a internet in ubuntu

i have a driver for my wireless card and i cant compile it .
can someone give me a tutorial or something how to install gcc manually?

i have ubuntu 10.04

---

### Post by lechien73 on 2010-05-07
How did you install 10.04? If you have a CD, you can try installing it from there:

[LIST=1]
[*]Insert your CD
[*]Go to System -> Administration -> Software Sources
[*]Click the checkbox next to "Cdrom with Ubuntu 10.04..."
[*]Click Close and reload the repository data
[*]Try installing gcc again.
[/LIST]

---

### Post by lechien73 on 2010-05-07
Further research indicates that may not work. From a machine with an Internet connection, you can download the deb files for gcc from here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/)

---

