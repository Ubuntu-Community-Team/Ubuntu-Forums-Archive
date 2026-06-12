---
title: "just did a fresh feisty install/ have a question"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by biker-dude on 2007-05-17
OK, I'm noticing that ssh is installed on my computer - is apt-get using ssh somehow? Is this a default? I used the easiest install method, a fresh installation over my old one, then used automatix to get the goodies, but I never requested to install ssh.

---

### Post by compiledkernel on 2007-05-17
not by default no. Im not sure if automatix installs openssh-server by default. I think the openssh-client is , but not the server. 

You would have to meander your way over to getautomatix.com to get that kind of support.

---

### Post by bmartin on 2007-05-17
SSH is installed by default. I wouldn't recommend removing it. It shouldn't get in your way, it's incredibly useful, and I'm guessing that many other programs depend on it. It's installed by default with every distro I've ever used.

On the other hand, SSHD, the daemon that allows other computers to connect to yours, is normally **not** installed by default. You can remove the daemon with **sudo aptitude remove openssh-server**. I wouldn't recommend doing this, but you can also remove the openssh-client package (definitely use aptitude for this and not apt-get). If it mentions that removal will break a lot of packages or that a lot of things will have to be removed, **DO NOT** remove it. In the worst case, removal could lead to a dead Linux box.

---

### Post by compiledkernel on 2007-05-17
I have to aggreewith bmartin on this, it would become problematic to remove openssh-client. 

I dont see any issue with removing openssh-server (refered to as SSHD here).

---

### Post by biker-dude on 2007-05-17
So does anybody know what programs use ssh? thanks for the info, btw.

---

### Post by bmartin on 2007-05-17
Try entering **apt-cache showpkg openssh-client** into a terminal (You may need to use **sudo**, but probably not). According to [this page]("http://www.debian.org/doc/FAQ/ch-pkgtools.en.html"), that's one way to determine dependencies.

---

