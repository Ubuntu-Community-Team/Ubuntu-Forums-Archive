---
title: "[SOLVED] How do I know I've installed all of 8.04?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Janeleaper on 2008-08-21
I've upgraded from 7.10 to 8.04.  It was a difficult upgrade, to put it mildly.  First of all I had the hanging locales problem, described elsewhere on this forum.  Then I had the Dell Inspiron 530 compatibility problem described on the Dell Ubuntu forum.  But I got there in the end, with a lot of help.

Everything is working well now and I seem to have everything -- except the Hardy Heron wallpaper.  This is not important.  Although the Heron is cute, I find brown tiring to look at over long periods and customise my wallpaper anyway. However, if I'm missing the Heron, how do I know whether I'm missing something else?  Is there any way of checking?

---

### Post by sameerds on 2008-08-21
> **Janeleaper said:**
> I've upgraded from 7.10 to 8.04.  It was a difficult upgrade, to put it mildly.
<snip>
However, if I'm missing the Heron, how do I know whether I'm missing something else?  Is there any way of checking?

Well, there could be a number of options here:

1) If your system seems to be working well, maybe there's no need to check.

2) You can try "sudo dpkg --configure -a", if you think there might be broken packages. This command checks to see if there are any partially installed packages, and tries to complete there installation.

3) You can try "sudo aptitude -f install" ... this commands checks to see if there are any dependency problems, and tries to fix them. It might upgrade some packages or download and install missing packages.

4) You could ensure that your system is up-to-date, using "sudo aptitude update" followed by "sudo aptitude safe-upgrade".

---

### Post by Janeleaper on 2008-08-21
Thanks.  I've already run dpkg --configure -a, but not the other two.

---

### Post by Janeleaper on 2008-08-22
I've now found that I can no longer play video, which I could before I upgraded.

---

### Post by Janeleaper on 2008-08-22
Sorry - sorted.  I just had to install Gecko.

---

