---
title: "Choosing server"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by wangjiaji on 2008-02-26
For some packages, e.g., Emacs, apt-get insists on connecting http://security.ubuntu.com instead of the server I've chosen, and this makes the downloading very slowly and a great pain for me, is there any way to avoid http://security.ubuntu.com and just download directly from the chosen server? Thanks!

---

### Post by dstew on 2008-02-26
I think you would just comment out that line in your /etc/apt/sources.list file.

---

### Post by wangjiaji on 2008-02-26
Ah yes, that worked, thank you. I thought that would be commented out automatically.

---

### Post by zvacet on 2008-02-27
> apt-get insists on connecting [http://security.ubuntu.com](http://security.ubuntu.com)

Of course it does.It is one of Ubuntu repositories.Now it is commented out and you are getting no security updates.it is better to have slow updates then not have any,specially if we are talking about security updates.

---

### Post by wangjiaji on 2008-02-27
> **zvacet said:**
> Of course it does.It is one of Ubuntu repositories.Now it is commented out and you are getting no security updates.it is better to have slow updates then not have any,specially if we are talking about security updates.

I'm using one repository from Taiwan, I think it has security updates, too? And that (main?) repository address just got left uncommented between other addresses, I think it's a mistake?

---

