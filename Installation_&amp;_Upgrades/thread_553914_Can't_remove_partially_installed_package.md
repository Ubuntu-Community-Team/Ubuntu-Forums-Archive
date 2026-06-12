---
title: "Can't remove partially installed package"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by pacsum on 2007-09-18
I canceled a .deb install while it was installing and now I can't install ubuntu updates. I tried to remove the package but I can't find it, I have used all the search commands but I can't find the package to remove it. It shows me this 
> E:The package secondlife-install needs to be reinstalled, but I can't find an archive for it.' 
and when I try to reinstall it, it won't let me either.

---

### Post by Pumalite on 2007-09-18
sudo dpkg --configure -a

sudo dpkg --remove --force-remove-<packagename>

---

### Post by pacsum on 2007-09-18
it shows me this 
> capri@vleiL:~$ sudo dpkg --remove --force-remove-secondlife -install
dpkg: unknown force/refuse option `remove-secondlife'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


---

### Post by Pumalite on 2007-09-18
Remove '-install'. Let's see what happens.

---

### Post by pacsum on 2007-09-18
The problem is that I don't know where the package is.
then I did this and still nothing >
> capri@vleiL:~$ sudo dpkg --remove secondlife-install
dpkg: error processing secondlife-install (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 secondlife-install


---

### Post by Pumalite on 2007-09-18
Try:

sudo killall secondlife

---

### Post by forestpixie on 2007-09-18
```
sudo dpkg --remove --force-remove secondlife-install
```

try that - you didn't have a gap between remove and secondlife first time round and a gap between secondlife and -install

---

### Post by pacsum on 2007-09-18
I can't kill it because the app is not even installed. The .deb doesn't contain the installation files, from the .deb file it just starts downloading the files from the site, I canceled the downloading process.
Maybe if I could force the .deb file to run? because it won't run from the desktop. What is the command for that?

---

### Post by Pumalite on 2007-09-18
Try this:

sudo apt-get remove --purge <packagename>

---

### Post by forestpixie on 2007-09-18
did you try this

```
sudo dpkg --remove --force-remove secondlife-install
```

---

### Post by pacsum on 2007-09-18
neither of them work.

---

### Post by forestpixie on 2007-09-18
try this then 

```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

---

### Post by pacsum on 2007-09-18
> **forestpixie said:**
> try this then 

```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```
Ok finally this one worked, thx :guitar:

---

