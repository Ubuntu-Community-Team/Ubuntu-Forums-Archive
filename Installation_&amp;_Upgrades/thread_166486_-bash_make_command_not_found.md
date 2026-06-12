---
title: "-bash: make: command not found ???"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by mista on 2006-04-26
Hi ive got this problem ...
When i try "make"
i got this...
-bash: make: command not found
what have i dont installed?? or is it any other prob??

---

### Post by nanotube on 2006-04-26
[QUOTE=mista]Hi ive got this problem ...
When i try "make"
i got this...
-bash: make: command not found
what have i dont installed?? or is it any other prob??[/QUOTE]
you are missing a package. 
```
sudo apt-get install build-essential
```
will give you all the stuff needed to compile software :)
i don't know why it's not installed with the default system, but it's not.

---

### Post by mista on 2006-04-26
yes!! tnx alot !!

---

