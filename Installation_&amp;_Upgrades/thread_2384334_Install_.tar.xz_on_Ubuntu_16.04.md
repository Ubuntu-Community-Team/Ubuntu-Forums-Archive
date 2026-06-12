---
title: "Install .tar.xz on Ubuntu 16.04"
date: 2018-02-05
forum: Installation &amp; Upgrades
---

### Post by janesh25 on 2018-02-05
Hello Everyone,

This is my first post on Ubuntu Forums and I am also new to Ubuntu.

I am taking an online course which requires me to set up a virtual machine and install vagrant.
I installed VirtualBox using the software centre but the version of vagrant is quite outdated on software centre according to the course guidelines ,so I downloaded the setup from vagrant website.

But, it downloaded in vagrant.tar.xz format , and I am at a loss as to how to install it on Ubuntu 16.04.

Please suggest me how to install it.

Thank You

---

### Post by Frogs Hair on 2018-02-05
Hello and Welcome

Start by extracting the package (right click and extract here). Next check for instructions or read me documents.

Edit:There appears to be a .deb package on the site which will install from the software center if I have found the correct application. Select the debian 32 or 64 bit as needed.

[https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)

---

### Post by wildmanne39 on 2018-02-05
Is your assignment to install vagrant or will you actually be using it?

---

### Post by janesh25 on 2018-02-05
Thank you so much for your help.
It worked.
Just curious as to why it showed version 1.81 when i searched on the Software centre but when i installed using .deb file through software centre it installed 2.02 ?
Why did not software centre showed the latest version in the first place ?

---

### Post by janesh25 on 2018-02-05
Well, I'll be using it along with virtual box to learn Linux commands.I'm new to linux.
Do not want to mess up my Host OS.

---

### Post by Frogs Hair on 2018-02-05
> **janesh25 said:**
> Thank you so much for your help.
It worked.
Just curious as to why it showed version 1.81 when i searched on the Software centre but when i installed using .deb file through software centre it installed 2.02 ?
Why did not software centre showed the latest version in the first place ?

I'm on 17.10 and see version 1.91. It could be the the latest version has not made it to the repository.

---

