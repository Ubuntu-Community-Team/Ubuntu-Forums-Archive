---
title: "using alien to convert rpm to deb?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by oberon_93 on 2008-03-23
i installed alien and i try to convert rpm to deb. i tried this....

--@ACER: ~/Documents$  alien realine-4.3-7.i386.rpm
Must run as root to convert to deb format (ro you may use fakeroot).


The i tried the other one....

--@ACER: ~/Documents$  sudo alien realine-4.3-7.i386.rpm
sh: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{NAME} readline-4.3-7.rpm":  at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482.


i also tried  'sudo alien --script -i realine-4.3-7.i386.rpm', but it still not working. anyone can help me ,thanks

---

### Post by carrett on 2008-03-23
Is rpm in fact installed? Try

```
which rpm
```

If it's not installed (which seems impossible since alien depends on rpm), try

```
sudo apt-get install rpm
```

Best of luck.

---

### Post by oberon_93 on 2008-03-24
[B]first of all, thanks

i tried  'which rpm'  and it returned nothing, then i tried the other one, it gave me the following messages.[/B]

Reading package lists....Done
Building dependency tree
Reading state information...Done
Package rpm is not available, but is referred to by another package.
this may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package rpm has no installation candidate.

:confused:

---

### Post by carrett on 2008-03-24
Hrm...what's in your /etc/apt/sources.list?

It should have [http://packages.ubuntu.com/gutsy/rpm](http://packages.ubuntu.com/gutsy/rpm)

it's in main.

---

### Post by oberon_93 on 2008-03-24
**i have a folder 'sourses.list.d', it has a 'd' at the end. actually there is nothing inside,i don't know.do i need to put those stuff in and how.....**

---

### Post by carrett on 2008-03-24
Um, sounds like you don't have a standard Ubuntu install there. Anyway, try creating a new /etc/apt/sources.list:

```
sudo nano /etc/apt/sources.list
```Add these lines to it:

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse (if you want backports, uncomment (and delete the stuff in parens))
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```
Once the file's been updated, run

```
sudo aptitude update && sudo aptitude install rpm
```
But really, you should be more concerned about why you have no /etc/apt/sources.list, that's a pretty standard file included with any install of *buntu (or any Debian-based distro for that matter).

Hope this helps.

---

### Post by zvacet on 2008-03-24
@ **oberon_93**

Try to reinstall alien from synaptic(just in case).be sure that you are in directory where rpm is (I know that you know that but you know...) and 

```
alien -d file.rpm
```

it should be the same as you did. If that doesn´t give any result install fakeroot and try again.**This time you will not need sudo. **

---

