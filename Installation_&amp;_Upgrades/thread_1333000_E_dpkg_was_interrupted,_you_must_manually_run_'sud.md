---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by polukas on 2009-11-21
after typing 
sudo dpkg -configure a
dpkg: unknown option -o
get the following message 
Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
which option to chose to fix  i've run both update and upgrade and still can't fix it
any ideas outhere?

---

### Post by raymondh on 2009-11-21
> **polukas said:**
> after typing 
[COLOR="Red"]sudo dpkg -configure a[/COLOR]


**sudo dpkg --configure -a**

I hope you just had a typo :)

---

### Post by darco on 2009-11-21
Unless its a typo, you need to add 2 dashes --
sudo dpkg --configure -a


darco

---

### Post by bossbruin on 2009-12-11
I had same problem and after opening terminal and running "sudo dpkg --configure -a" the problem was solved.  It took a while and a couple of restarts but everything seems to be fine now.

---

