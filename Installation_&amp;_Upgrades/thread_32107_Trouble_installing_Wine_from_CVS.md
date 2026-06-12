---
title: "Trouble installing Wine from CVS"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2005-05-06
I was using a how-to from this forum to install the latest Wine from CVS. The version available for Ubuntu does not work for me, so I decided to try CVS one.

At some point of the installation I've got the following:

```
bison -p SQL_ -d ./sql.y -o sql.tab.c
"./sql.y", line 71: junk after `%%' in definition section
"./sql.y", line 71: no input grammar
"./sql.y", line 71: unknown character `.' in declaration section
``` 

and the last line repeats over and over again indefinitely. I 've taken a look at sql.y, and the line 71 it complains about is the followng:

```
%pure-parser
``` 

I tried googling  and have not found any solution. Any Ideas?

---

### Post by jodef on 2005-05-06
Although the HOWTO section not for questions if your problems pertain to it directly better to ask there. If it is an error the author can correct it or even point you in the right direction.

---

### Post by foxy123 on 2005-05-07
[QUOTE=jodef]Although the HOWTO section not for questions if your problems pertain to it directly better to ask there. If it is an error the author can correct it or even point you in the right direction.[/QUOTE]
I do not think that this problem is how-to specific, although firstly I asked there, but have not got any answer.

---

