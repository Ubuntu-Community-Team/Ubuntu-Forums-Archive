---
title: "half installed ttf-mscorefonts-installer"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by BarryD9545 on 2013-10-07
While trying to install ttf-mscorefonts-installer I get this error:

[INDENT]*barry@BKC-Media:~$ sudo apt-get install ttf-mscorefonts-installer*[/INDENT]
[INDENT]*Reading package lists... Done*[/INDENT]
[INDENT]*Building dependency tree       *[/INDENT]
[INDENT]*Reading state information... Done*[/INDENT]
[INDENT]*ttf-mscorefonts-installer is already the newest version.*[/INDENT]
[INDENT]*0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.*[/INDENT]
[INDENT]*1 not fully installed or removed.*[/INDENT]
[INDENT]*Need to get 0 B/27.8 kB of archives.*[/INDENT]
[INDENT]*After this operation, 0 B of additional disk space will be used.*[/INDENT]
[INDENT]*Do you want to continue [Y/n]? y*[/INDENT]
[INDENT]*dpkg: error processing ttf-mscorefonts-installer (--configure):*[/INDENT]
[INDENT]* package ttf-mscorefonts-installer is not ready for configuration*[/INDENT]
[INDENT]* cannot configure (current status `half-installed')*[/INDENT]
[INDENT]*Errors were encountered while processing:*[/INDENT]
[INDENT]* ttf-mscorefonts-installer*[/INDENT]
[INDENT]*E: Sub-process /usr/bin/dpkg returned an error code (1)*[/INDENT]

Now what?

Thanks!

---

### Post by oldos2er on 2013-10-07
Maybe ```
sudo dpkg --configure -a
```

---

### Post by BarryD9545 on 2013-10-08
No luck, same result.

Also, when running the software update, it didn't complete.  Just a window that said,

*  The installation or removal of a software package failed.*

---

### Post by Frogs Hair on 2013-10-08
You can try the following which works with aptitude, but I am not sure about apt-get. Replace the words package name with the complete name of the package being removed .  
 
```
sudo dpkg --remove -force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* package name
```


 [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by BarryD9545 on 2013-10-09
cut/pasted the command from Frog's Hairs' instructions in with my package name and got this:

[INDENT]*barry@BKC-Media:~$ sudo dpkg --remove -force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* ttf-mscorefonts-installer*
*dpkg: error: conflicting actions -f (--field) and -r (--remove)*

[I]Type dpkg --help for help about installing and deinstalling packages 
[*];[/I]
*Use `dselect' or `aptitude' for user-friendly package management;*
*Type dpkg -Dhelp for a list of dpkg debug flag values;*
*Type dpkg --force-help for a list of forcing options;*
*Type dpkg-deb --help for help about manipulating *.deb files;*

[I]Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/I]
[/INDENT]

So I added a hypen to the *-force* and got this:
[INDENT]*barry@BKC-Media:~$ sudo dpkg --remove --force --force-remove-reinstreqgrep ^ /etc/apt/sources.list /etc/apt/sources.list.d/* ttf-mscorefonts-installer*
*dpkg: error: unknown force/refuse option `--force-remove-reinstreqgrep'*

[I]Type dpkg --help for help about installing and deinstalling packages 
[*];[/I]
*Use `dselect' or `aptitude' for user-friendly package management;*
*Type dpkg -Dhelp for a list of dpkg debug flag values;*
*Type dpkg --force-help for a list of forcing options;*
*Type dpkg-deb --help for help about manipulating *.deb files;*

[I]Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/I]

[/INDENT]
help

---

### Post by Frogs Hair on 2013-10-09
As I remember I had the same result without aptitude installed  . ```
*Use `dselect' or `aptitude' for user-friendly package management*
```

Try ```
sudo dpkg -r
```

---

### Post by BarryD9545 on 2013-10-09
Tried and got:

[INDENT][I]barry@BKC-Media:~$ sudo dpkg -r ttf-mscorefonts-installer
dpkg: error processing ttf-mscorefonts-installer (--remove):[/I][/INDENT]
[INDENT]* Package is in a very bad inconsistent state - you should*[/INDENT]
[INDENT]* reinstall it before attempting a removal.*[/INDENT]
[INDENT]*Errors were encountered while processing:*[/INDENT]
[INDENT]* ttf-mscorefonts-installer*[/INDENT]

---

### Post by varunendra on 2013-10-10
> **BarryD9545 said:**
> Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.

So what happens when you try what it suggested ^^ -
```
sudo apt-get clean
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by BarryD9545 on 2013-10-12
Hadn't tried your commands before, I'm kinda too new at this to have known it, and got new results.

ttf-mscorefonts-installer installed!
(yay)

Thanks varunendra!

(how do I mark this solved?)

---

### Post by oldos2er on 2013-10-12
> **BarryD9545 said:**
> (how do I mark this solved?)

At the top of the page, click the drop-down menu under Thread Tools.

---

