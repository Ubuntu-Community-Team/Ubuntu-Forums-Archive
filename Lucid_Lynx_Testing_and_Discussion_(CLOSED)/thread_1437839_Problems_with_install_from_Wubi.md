---
title: "Problems with install from Wubi"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pbelfi on 2010-03-24
Trying to install Ubuntu Lucid Lynx through Wubi.....I get as far on the installation of memtest86+ and the installation just hangs!! I've waited for almost an hour, and still stuck at that memtest86+ screen.....any solution for this?

---

### Post by kansasnoob on 2010-03-24
How are you trying to install Wubi?

Read this:

> Wubi as included on the ISO images is unable to enter its second stage of installation, so you will not be able to install inside Windows using just an ISO image in this beta release. As a workaround, users who are installing the Ubuntu Desktop Edition can download the stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed for 10.04 LTS Beta 2. (541607) 

That's from the release notes:

[http://www.ubuntu.com/testing/lucid/beta1#Known%20issues](http://www.ubuntu.com/testing/lucid/beta1#Known%20issues)

The bug referenced:

[https://bugs.launchpad.net/wubi/+bug/541607](https://bugs.launchpad.net/wubi/+bug/541607)

---

### Post by rfbeck on 2010-03-24
That's fixed the problem for me at least. Good looking out.
______
Robert

---

### Post by pbelfi on 2010-03-25
Thanks for the reply...works for me just fine! Thanks again.

---

