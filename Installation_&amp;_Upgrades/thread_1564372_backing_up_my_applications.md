---
title: "backing up my applications"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by mbuotidem on 2010-08-30
Okay, i am trying to transfer all my installed apps from a desktop to a laptop. I would have used aptoncd but the laptop's cd drive is dead. 

so i searched for another solution and i saw a tutorial that gave the following instructions:

Open a terminal and paste the following into it:
```

$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1` 
```

then to install on the other end:


Navigate to the folder with the packages and input the following command in the terminal:

```
sudo dpkg -i *.deb
```

I tried this out but got this output:

```
mbuotidem@NET-SERVER-PC:~/dpkg-repack$ fakeroot -u dpkg-repack `dpkg –get-selections | grep install | cut -f1`
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
Usage: dpkg-repack [options] packagename [packagename ..]
	--root=dir	Take package from filesystem rooted on <dir>.
	--arch=arch	Force the parch to be built for architecture <arch>.
	--generate	Generate build directory but do not build deb.
	packagename	The name of the package to attempt to repack.

```


Please can you help me fix this?

---

