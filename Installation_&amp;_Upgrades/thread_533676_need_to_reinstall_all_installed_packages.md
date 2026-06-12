---
title: "need to reinstall all installed packages"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by miatawnt2b on 2007-08-24
I am trying to reinstall all of the installed packages on my system.  I have tried a few things, but cannot seem to get it to work.

First I tried reinstalling using the following command.
COLUMNS=200 dpkg -l | awk '/^ii/ {print $2}' | xargs apt-get -y --force-yes --reinstall install

but I get an error :
E: Couldn't configure pre-depend coreutils for debianutils, probably a dependency cycle.

I can't seem to find any solution for this.

I also was able to create a file of all of my installed packages using 
dpkg –get-selections | grep -v deinstall > ubuntu-files
but have no idea how to pass this file to apt-get --reinstall install (or if it would even work)

Can someone help?
THanks,
-J

---

### Post by Pumalite on 2007-08-24
Try AptOnCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by miatawnt2b on 2007-08-24
I downloaded this, but I'm not exactly sure how this helps me.  I don't think the actual package files are on my system, and even if they were, it appears as you need to go through and individually select the deb's with this, burn the cd then restore with the cd.  It seems as if this tool would be used to create a cd so that you could install the same packages on a fresh ubuntu install... not exactly what I want to do.

Or am I just being a dumb noob?

-J

---

### Post by it.henrik on 2008-02-02
Hi,

I have to do exactly the same thing.

Does someone have a solution to this?

I am also seeing this problem:
E: Internal Error, Could not perform immediate configuration (2) on gzip

Can someone please help me with how I can solve this?

---

### Post by mangaskahn on 2008-04-13
I found a "quick and dirty" work around for your problem after coming across your post while having the same problem.

#for i in `COLUMNS=200 dpkg -l | awk '/^ii/ {print $2}'`; do apt-get -y --force-yes --reinstall install $i; done;

This will reinstall all of the packages listed by your awk statement one at a time. dpkg will resolve any dependencies that need to be resolved, but because all of these packages are already on the machine, there shouldn't be any. 

I hope this helps.


Really, I'm not out to destroy Microsoft. That will just be a completely unintentional side effect.--Linus Torvalds
mangaskahn

---

### Post by elamericano on 2008-04-14
sudo dpkg –set-selections < ubuntu-files
sudo apt-get dselect-upgrade

Haven't tried it myself...

---

### Post by koenn on 2008-04-14
something like this maybe ?
```

# make a list of installed apps
dpkg --get-selections | grep install | cut  -f1 -  >my_packages

# become root  to run apt-get later
sudo -i

# reinstall packages from list
cat my_packages  |while read PKG; apt-get -y --reinstall install $PKG ; done

# close root session
exit

```

---

### Post by Lumenary on 2008-05-03
Hello All,


I wrote a tutorial on how to do this.  It is located here:


[INDENT][[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=735693&highlight=reinstall+all+packages+without+reinstalling+ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=735693&highlight=reinstall+all+packages+without+reinstalling+ubuntu")[/INDENT]


This should help with the dependency issue(s) you are mentioning.  Caveat emptor; be sure this is what you want to do...


> **miatawnt2b said:**
> I am trying to reinstall all of the installed packages on my system.  I have tried a few things, but cannot seem to get it to work.

First I tried reinstalling using the following command.
COLUMNS=200 dpkg -l | awk '/^ii/ {print $2}' | xargs apt-get -y --force-yes --reinstall install

but I get an error :
E: Couldn't configure pre-depend coreutils for debianutils, probably a dependency cycle.

I can't seem to find any solution for this.

I also was able to create a file of all of my installed packages using 
dpkg –get-selections | grep -v deinstall > ubuntu-files
but have no idea how to pass this file to apt-get --reinstall install (or if it would even work)

Can someone help?
THanks,
-J

---

### Post by kfazz on 2008-05-23
or you could:
first clean your cache:(to remove old debs)
```
sudo aptitude clean
```
then
```
sudo aptitude reinstall '~i'
```
the '~i' means all installed packages
it will fail with the coreutils debianutils cycle, but that's ok, it downlaoded all the packages
```
 cd /var/cache/apt/archives
sudo dpkg -i *.deb 
```
this is probably faster than running apt-get once per package.

---

### Post by xernos on 2008-05-24
Hi tray :

1) Create list of installed packages :
[COLOR="Green"]dpkg -l  | awk '{print $2}'| awk  'FNR>5' >> ~/list.txt[/COLOR]

This create list all installed package in your system - we copy only second column and remove first lines, because it's the header :D. 

2) Now we have list of installed packages so we may reinstall :D.
[COLOR="Green"]apt-get --reinstall install  'cat ~/list.txt'[/COLOR]
OR 
If you need you may reinstal packages and remove configs :D
[COLOR="Green"]apt-get --purge --reinstall install  'cat ~/list.txt'[/COLOR]

Bay

---

