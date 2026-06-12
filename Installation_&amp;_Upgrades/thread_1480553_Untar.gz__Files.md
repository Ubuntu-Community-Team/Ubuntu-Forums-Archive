---
title: "Untar.gz  Files"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by benj2514 on 2010-05-11
I'm sorry if this question has been asked many times before, but I am unable to untar the file gish153-1.tar.gz. I've tried the command lines that I've seen on the internet... tar xvfz gish153-1.tar.gz and -zxvpf gish153-1.tar.gz. I have never been able to untar anything on my computer and its starting to become inconvenient. Anything anybody can tell me about these files will help. Thx.

---

### Post by lemming465 on 2010-05-14
If you check the man page for tar, and can puzzle it out, you will discover that the "-f" option wants an argument (the archive file), so if you are smooshing them all together, you have to put "f" last.  Try **tar -xvzf gish153-1.tar.gz**.

---

