---
title: "Folder where packages are installed by default"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by eklavya_18 on 2010-02-15
Can you tell me where do packages installed with apt-get or synaptic package manager get stored in? I use Ubuntu9.10

---

### Post by darkod on 2010-02-15
I think usually it's /usr/bin

At least that's where I found something I was looking for just now.

---

### Post by raymondh on 2010-02-15
could be in:

/usr
/lib
/sbin

I know this may sound confusing but maybe a file structure visual can help you.  Look at 3.1 and 3.2

[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

Regards,

Raymond

---

### Post by oldos2er on 2010-02-15
**dpkg -L <package name>** will show you where each file in a package is installed. You can see the same thing in Synaptic by clicking Status, Installed, right-click on a package, Properties, Installed Files.

---

