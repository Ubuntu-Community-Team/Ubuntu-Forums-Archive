---
title: "Unmet Dependencies Problem"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by vzent on 2007-01-02
Hi,

Im using Ubuntu Dapper (6.06). Recently i have downloaded and installed xmms. 

However, problems happened when i try to install mysql server, i have got the following message:

root@ubuntu:~/Desktop# apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
  xmms: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
        Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
        Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
        Depends: libmikmod2 (>= 3.1.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I try to run "apt-get -f install", no luck too...what did i do wrong ?

---

### Post by bapoumba on 2007-01-02
Hello,
could you post the output to **cat /etc/apt/sources.list** ?

---

### Post by vzent on 2007-01-03
Hi bapoumba,

This is what i got after i did "cat /etc/apt/sources.list"...

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper beryl-svn

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the ‘universe’
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

I tried "apt-get update" and "apt-get upgrade"...i got the same error shown as below:
The following packages have unmet dependencies:
  xmms: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is installed
        Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
        Depends: libglib1.2 (>= 1.2.0) but it is not installed
        Depends: libgtk1.2 (>= 1.2.10-4) but it is not installed
        Depends: libmikmod2 (>= 3.1.10) but it is not installed
E: Unmet dependencies. Try using -f.

:-|

---

### Post by bapoumba on 2007-01-03
[QUOTE=vzent]Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed[/QUOTE]
I just looked for this unmet dependency. Do not know where it could be trying to get it from. 2.3.6-0ubuntu20 is the current dapper version, and I cannot find it in the beryl repos.

[QUOTE=vzent]libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is installed[/QUOTE]
Ditto.

Try to comment the beryl repos (you have 3 of them) and run **sudo apt-get update** again.
In addition, you have two entries for the backports. One is enough ;)

You may want to give aptitude a shot. Install it (**sudo apt-get install aptitude**) and run **sudo aptitude update**. Is the error message different ?

---

