---
title: "Determine repo"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by alistairh77 on 2011-06-19
Hi,

How do you determine which repo a package will be downloaded from?

I'm using the Server edition and using apt rather than a GUI.  Sorry - I know this is really easy but haven't been able to find the answer.

Thanks

---

### Post by dino99 on 2011-06-19
[http://wiki.vpslink.com/Linux_Command_Reference:_aptitude_%28Debian,_Ubuntu%29](http://wiki.vpslink.com/Linux_Command_Reference:_aptitude_%28Debian,_Ubuntu%29)

---

### Post by Cheesehead on 2011-06-19
Try the 'apt-cache' command
```
apt-cache show packagename
```
Look in the 'Filename' field. For example, the 'hello' package is in Main
```
my-system:~$ apt-cache show hello | grep Filename
Filename: pool/main/h/hello/hello_2.5-1_i386.deb

my-system:~$ apt-cache show hello | grep Filename | cut -d'/' -f2
main

my-system:~$ apt-cache show skype | grep Filename | cut -d'/' -f2
partner

```


Tip: apt-cache also has a very handy search feature, if you don't know the package name.```
apt-cache search skype
```

---

### Post by amauk on 2011-06-19
```
apt-cache policy <package>
```

will show you the installed version, any updated versions available and which repositories each version is in

---

