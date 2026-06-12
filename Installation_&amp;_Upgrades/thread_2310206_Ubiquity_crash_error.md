---
title: "Ubiquity crash error"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by zzixxus on 2016-01-17
Hello :)

I try to create my own linux distro based on ubuntu, when I run ubiquity I had error like this:

[IMG]http://s15.postimg.org/d0f83tsh7/Virtual_Box_5_17_01_2016_12_05_29.png[/IMG]

This system "version" I only change the system name in boot, hosts etc. but on previous version system who is installed before on Virtual Machine, after the change of the same value system operates normally. This copy runs in a live working well except that it can not be installed. or it may have something in common?

apt-get update command 
> Get:1 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) xenial InRelease [227 kB]
80% [1 InRelease gpgv 227 kB]Couldn't create tempfiles for splitting up /var/libIgn:1 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) xenial InReleaseal_InRelease
Hit:2 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
Hit:3 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) xenial/main Translation-en
Fetched 227 kB in 8s (27.1 kB/s)         
Reading package lists... Done
W: GPG error: [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: The repository 'http://nz.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.



Can you help me ?

---

### Post by matt_symes on 2016-01-17
Hi

Have you checked the missing packages *gnupg* and *grub (grub-common)* are installed and accessible from the live environment ?

Have you checked the paths and package permissions ?

How did you create the live environment ?

Kind regards

---

### Post by zzixxus on 2016-01-17
Can you help me to reprair my repository ? 

I had this error:
[IMG]http://s9.postimg.org/kc6gqp1zj/Przechwycenie_obrazu_ekranu_2016_01_17_23_05_50.png[/IMG]

and my sources.list it looks like this:

> ###### Ubuntu Main Repos
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) xenial main restricted 
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) xenial main restricted 


---

### Post by matt_symes on 2016-01-17
Hi

Please post the output of these commands.

```
dpkg -l | grep gnupg
```

```
echo $PATH
```

```
ls -l /usr/bin/apt-key
```

```
dpkg -C
```

Kind regards

---

### Post by deivid_the_clown on 2016-05-18
Hi, same problem here... @matt_symes, any ideas?
```

$ dpkg -l | grep gnupg
ii  gnupg                                1.4.20-1ubuntu3                     i386         GNU privacy guard - a free PGP replacement
$ echo $PATH
/usr/java/jdk1.7.0_25//bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
$ ls -l /usr/bin/apt-key
-rwxr-xr-x 1 root root 20771 Apr 14 07:41 /usr/bin/apt-key
$ dpkg -C
$

```

---

