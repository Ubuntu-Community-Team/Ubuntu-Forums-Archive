---
title: "Matlab &amp; libc.so.6: not found"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by psyclone on 2013-12-21
I haven't installed matlab yet. I inserted the following:

e1-desktop@e1desktop:~$ sudo /home/e1-desktop/Downloads/Matlab_R14/install -glnx86 -v

(I've used -glnx86 -v, due to my 64 bit system).
and that returns:


/home/e1-desktop/Downloads/Matlab_R14/install: 1: /home/e1-desktop/Downloads/Matlab_R14/install: /lib64/libc.so.6: not found

I've also tried:

e1-desktop@e1desktop:~$ ln -s libc.so libc.so.6

but that returns:

ln: failed to create symbolic link `libc.so.6': File exists.


Could it be the version of matlab7 (R14) compared with 12.04?

---

### Post by psyclone on 2013-12-22
the version is R2010,

---

### Post by psyclone on 2013-12-22
I've tied several times.

I've removed and re-installed 

libc.so

but it won't link to libc.so.6, the short cut appears in /usr/local/matlab7  but the link is broken. But when I open dir /lib64 the libc.so.6 file isn't present.  
When installing 'libc.so' the actual package installed is 

e1-desktop@e1desktop-MS-7788:/lib64$ sudo apt-get install libc.so
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'eglibc-source' for regex 'libc.so'

any ideas?

---

### Post by psyclone on 2013-12-22
Also correction.

e1-desktop@e1desktop-MS-7788:/usr/local/matlab7$[COLOR=#000000] sudo /home/e1-desktop/Downloads/Matlab_R14/install -glnx86 -v

instead of 

[/COLOR][COLOR=#000000]e1-desktop@e1desktop:~$ sudo /home/e1-desktop/Downloads/Matlab_R14/install -glnx86 -v
 

[/COLOR]

---

