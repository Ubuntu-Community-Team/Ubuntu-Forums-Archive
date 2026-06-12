---
title: "how to install *.rpm"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by ramadan on 2008-06-20
i did download acrobat reader in rpm format and i cant install it, any clue
every help is appreciated
thanks

---

### Post by Pjotr123 on 2008-06-20
rpm is not for Ubuntu, because Ubuntu uses .deb. rpm's are made for rpm-based distro's like Fedora and OpenSUSE.

Find the deb on the website and doubleclick that, just like you would a Windows .exe installer.

---

### Post by Pumalite on 2008-06-20
Sudo apt-get install alien
Then convert rpm to deb
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by logos34 on 2008-06-20
> **Pjotr123 said:**
> 
Find the deb on the website and doubleclick that, just like you would a Windows .exe installer.

the better way is to get it through the repos by adding medibuntu:
[http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu)

then

sudo apt-get install acroread acroread-escript acroread-plugins mozilla-acroread

---

### Post by Pjotr123 on 2008-06-20
> **Pumalite said:**
> Sudo apt-get install alien
Then convert rpm to deb
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

alien is an emergency measure. Unreliable and yields potentially unstable results. If a .deb is available (in this case, it is) then that's always preferable.

---

### Post by ramadan on 2008-06-20
thank you all guys, I'll search for deb but the adobe site provides only rpm format. and am confused with distros and prosp, etc
at least i know now that rpm is for fedora it is first to me :lolflag:

N.B i extracted the rpm content and  accidentally dble click a file and the acrobat works so where should i store the files manually and how to make it open pdfs by default if possible?

---

