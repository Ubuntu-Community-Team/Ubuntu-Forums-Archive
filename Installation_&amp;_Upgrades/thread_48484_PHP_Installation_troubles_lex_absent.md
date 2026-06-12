---
title: "PHP Installation troubles: lex absent"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by nocitizen on 2005-07-12
Hey there,
I'm currently trying to install php on my ubuntu system.  After I've unzipped and untarred the php-4.3.8. into its own folder and commence with ./configure, I get the following error message [I've included about the last 5-10 lines just in case]:

...
checking for bison... bison -y
checking bison version... configure: warning: You will need bison 1.28
2.0 (ok)
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2425: lex: command not found
configure: error: cannot find output from lex; giving up
root@ubuntu: #

It seems that I don't have the capacity to run the lex command, whatever that may be.  I've checked online, and as far as I know it's a command used by the parser programs bison and yacc (but I won't pretend to know what these programs do).  I've downloaded bison, but as you can see, the error remains ](*,) , though it seems I've installed it successfully.  Any help would be much appreciated!  -lee

---

### Post by nemin on 2005-07-13
[QUOTE=nocitizen]Hey there,
I'm currently trying to install php on my ubuntu system.  After I've unzipped and untarred the php-4.3.8. into its own folder and commence with ./configure, I get the following error message [/QUOTE]Just a question: why don't you just use the php version wich is available in the Ubuntu repositories and install it with apt-get?

---

### Post by alastair on 2005-07-13
apt-get install flex

---

