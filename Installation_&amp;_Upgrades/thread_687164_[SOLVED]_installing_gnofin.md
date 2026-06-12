---
title: "[SOLVED] installing gnofin"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by confused1 on 2008-02-04
noob needs help installing gnofin 0.8.4.

i have downloaded it to my desktop 

what command would i use in the terminal - i tried sudo apt-get install gnofin

i have also downloaded Kpkg but when i try to use it, it won't recognize gnofin 


thanks-

---

### Post by shafin on 2008-02-04
what type of file it is?

.tar.gz or .deb?

---

### Post by Partyboi2 on 2008-02-04
download the deb package from [http://packages.debian.org/sarge/gnofin](http://packages.debian.org/sarge/gnofin). Then double click on it to start gdebi-gtk. If all the dependencies are met click on "Install Package" If you are needing to install dependencies you can look for the packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them first.
You can find more about installing stuff from here
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[SIZE=-1]http://www.monkeyblog.org/**ubuntu**/**install**ing/ [/SIZE]

---

### Post by confused1 on 2008-02-08
i'm still here and still trying to install Gnofin 

once i get to this page, "http://packages.debian.org/sarge/gnofin" 
i see a "link for Gnofin"  with the following choices under it. 
:confused:Should i choose one of these   

   *  [gnofin_0.8.4-2.2.dsc]
    * [gnofin_0.8.4.orig.tar.gz]
    * [gnofin_0.8.4-2.2.diff.gz]

or, if i scroll on down, i see a box of choices under "download Gnofin"

and the best choice for me looks like the "i386 download"

i'm not sure which way to go or what to do next and i definitely need  step by step directions

i'm running Ubuntu 7.10

---

### Post by Partyboi2 on 2008-02-08
[Here]("http://debian.lcs.mit.edu/debian/pool/main/g/gnofin/gnofin_0.8.4-2.2_i386.deb") is the i386 deb. It is located at the bottom of that page under "download gnofin" where there is a list of different Architectures. So the link I have provided is for the i386. When you have downloaded it double click on it and it will open the deb installer. Then Select "Install Package"  But....if next to status it tells you there is some dependency problems, (see screenshot for example) you will need to first install those [packages]("http://packages.ubuntu.com/") before continuing to install gnofin. Let us know if you need help with finding the dependencies.

---

### Post by confused1 on 2008-02-08
g'day and thanks partyboi2. That was definitely what i needed. 
upon download, all 18 packages were installed-:popcorn:

---

