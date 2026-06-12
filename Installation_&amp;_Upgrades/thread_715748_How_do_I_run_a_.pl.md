---
title: "How do I run a .pl?"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by CyberCat7 on 2008-03-05
I have some programs downloaded, but they contain .pl files.

How do I run those in Ubuntu 7.10?

I have been searching for an easy way to install perl as I read somewhere that I need it to run .pl files.

---

### Post by Biggus on 2008-03-05
You would ( I think) first of all make the file executable, using a terminal :

```
chmod +x name_of_script

```
You would then simply type in the path to the .pl file to execute it :

/home/user/filename.pl

I've never tried it, but I think you can install perl using :

```
sudo aptitude install perl
```

---

