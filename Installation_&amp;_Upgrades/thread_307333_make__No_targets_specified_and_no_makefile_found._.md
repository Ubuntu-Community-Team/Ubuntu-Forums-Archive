---
title: "make: *** No targets specified and no makefile found.  Stop. [Resolved]"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by juliuss on 2006-11-26
Hi.  I'm new to linux and ubuntu.  I'm trying to install a few programs (a program needed for my for my nic and OpenSSH) and I keep getting stuck.

The instructions say that I just need to type "make" but I keep getting this message:
juliuss@juliuss-desktop:~/Desktop/openssh-2.1.1p4$ make
make: *** No targets specified and no makefile found.  Stop.

I've looked on other message boards, and people who ask this question are basically called noobs and made fun of (yay linux!) so hopefully this board is more helpful.

Thanks!

---

### Post by shin on 2006-11-26
There is no Makefile in this directory. Where have you obtained this program from? And is it just openssh? I think that you may just download it from repos.

Also be sure to read README or INSTALL file from the directory of this program (it should be there).

---

### Post by aysiu on 2006-11-26
shin's right--just install it through the repositories: ```
sudo aptitude update && sudo aptitude install openssh-client openssh-server
```

---

### Post by juliuss on 2006-11-26
That seems to have worked.  Thanks!  :KS

---

### Post by aysiu on 2006-11-26
For more on installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by fog on 2006-11-26
Try first cd in the right dir, then ./configure (or autogen.sh if configure doesn 't exist) and after make.

---

