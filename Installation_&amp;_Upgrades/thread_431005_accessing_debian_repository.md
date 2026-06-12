---
title: "accessing debian repository"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by potterpoole on 2007-05-02
Now that I am back to squair one with synaptic how do I access the debian repository

---

### Post by lw5 on 2007-05-02
Perhaps you should clarify a bit about what you are trying to do?

---

### Post by GrueTamer on 2007-05-02
I think all you have to do is add this custom repository to your sources

```
deb http://http.us.debian.org/debian stable main contrib non-free
```

An easy way to add things to your sources list is through synaptic, in the repository settings menu.  Add it in the "third-party software" area.

But remember, sometimes, regular debian packages don't work correctly in ubuntu.  Just thought I'd warn you about that.

If you're not in the US, you need to add a different mirror, but I don't know what it is off hand, but it's similar, I know that.

---

### Post by zvacet on 2007-05-02
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by az on 2007-05-02
> **potterpoole said:**
> Now that I am back to squair one with synaptic how do I access the debian repository

Ubuntu and Debian are not binary-compatible.  Do not use any foreign repositories.  Look for backports or compile the package from source, using the deb-src repositories, if you need.

---

### Post by potterpoole on 2007-05-03
This is all in search of  the latest version of a small game called xjig
I dont plan to make downloading from debian a habit and I dont know how to compile anything from source code. I am an artist not a programer. If It was'nt for the suport and time that the Linux comunity is willing to give me I would have to use windows. I wish I could give back more than I can but clay and computers dont mix.

---

### Post by az on 2007-05-03
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=xjig](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=xjig)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=xjig](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=xjig)

Xjig is the same version in Debian as in Ubuntu!

Do you have the universe repo enabled?

---

### Post by potterpoole on 2007-05-03
I am not geting the file usr/share/menu/xjig which inhances its performance. Its on the package list but dosent download. shold I try reporting this as a bug?

---

### Post by az on 2007-05-03
> **potterpoole said:**
> I am not geting the file usr/share/menu/xjig which inhances its performance. Its on the package list but dosent download. shold I try reporting this as a bug?

You mean that you don't get a menu entry for it?  Most packages in universe do not provide freedesktop.org-compliant menu entries.  Yes, this is a bug.

A workaround is to install the "menu" package.  That will provide you with a "debian" menu with all desktop apps' entries.  Another workaround is to make a desktop or taskbar launcher by hand.

---

