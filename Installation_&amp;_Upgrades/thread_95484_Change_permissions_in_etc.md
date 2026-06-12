---
title: "Change permissions in /etc"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by waffen on 2005-11-26
Hello :

I make a stupid order in my console:

```
sudo chmod 777 -R /etc
```

and now I couldnt access: Synaptic, Root Terminal... :( 

Is possible fix this error??? or I reinstall the Ubuntu?? 

Thanks in advance!!

---

### Post by Xian on 2005-11-26
$ sudo chmod 755 -R /etc

---

### Post by lcg on 2005-11-26
[QUOTE=Xian]$ sudo chmod 755 -R /etc[/QUOTE]
That will give execute bits on all files in /etc, which probably isn't such a good idea. Whenever I need to recursively fix permissions below a directory, I use this method (in this example, fixing the files in /etc):
```
$ cd /etc
$ find -type d -exec chmod 755 {} \;
$ find -type f -exec chmod 644 {} \;
```
This will give you 755 permission on directories and 644 on files, if you need something else, just adjust the command lines accordingly.

Maybe someone has some use for this.

Lars

---

### Post by Xian on 2005-11-26
[QUOTE=lcg]Maybe someone has some use for this.
[/QUOTE]

Yes, good call Icg. Kudos.

---

