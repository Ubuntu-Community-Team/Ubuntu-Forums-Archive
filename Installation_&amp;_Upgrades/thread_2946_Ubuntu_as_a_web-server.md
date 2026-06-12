---
title: "Ubuntu as a web-server"
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by p__wack on 2004-11-02
Hi!, I'm a student from Chile and I want to instal Ubuntu in a future web-server, so, I need some info,

My machine is a Dual Pentium II (350MHz @ 392MHz) with 448 MB of RAM with 2 HDDs ( 20GB & 40GB ), on a A.I.R. (the company is in bankrupt) P6BDX-SE motherboard, and a nVidia Riva 128 video card. As you can see, a mud-proof PC from the old times.

I need some basic software in the machine:
- Apache HTTPD 1.3 (no the 2.0)
- mySQL
- PHP 4 or 5
- a simple FTP server
- a SSH server

Ubuntu have it???

ah, another question, ubuntu have the "apt" program for package management???

well, that's all, thanx for your answers, and sorry for my really por english

---

### Post by flygmaskin on 2004-11-02
Yep, ubuntu has all of those. But apache 1.3 is in the unsupported "universe" repo. That means that you might not get regular security updates and bugfixes.  All the other packages you asked for (and apache2) are located in the normal repos.

---

### Post by p__wack on 2004-11-02
[QUOTE=flygmaskin]Yep, ubuntu has all of those. But apache 1.3 is in the unsupported "universe" repo. That means that you might not get regular security updates and bugfixes.  All the other packages you asked for (and apache2) are located in the normal repos.[/QUOTE]
wow, thanx, maybe this will be the distro for my server, the reason for use the old and unsuported Apache 1.3 is: it are tested and aprobed by a giant base of user and sysadmins, and I read in some forums: "apache2 have really bad bugs".

nevertheless, I request a copy of ubuntu to install it in the machine,

thanx!

---

### Post by jdong on 2004-11-02
[QUOTE=p__wack]wow, thanx, maybe this will be the distro for my server, the reason for use the old and unsuported Apache 1.3 is: it are tested and aprobed by a giant base of user and sysadmins, and I read in some forums: "apache2 have really bad bugs"[/QUOTE]

Untrue! Many servers run apache2 without any issues. The new dso model promotes stability by modularizing components. Plus, the ubuntu team won't be that diligent in patching 1.3 -- not as supported as 2.0.

---

### Post by p__wack on 2004-11-02
really?, I'll study more 'bout apache 2.0,

thanx!

---

### Post by jdong on 2004-11-02
in case you didn't assume it: yes, of course ubuntu has apt! What's a debian fork without apt?!?

---

### Post by FLeiXiuS on 2004-11-02
I would reccomend checking out this website for a detailed install of apache / php / mysql.

[http://www.madpenguin.org/cms/?m=show&id=751](http://www.madpenguin.org/cms/?m=show&id=751)

Just download the latest inspite of the outdated.

---

