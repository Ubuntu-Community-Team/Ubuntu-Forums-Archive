---
title: "Dapper to Edgy problem dist-upgrade"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by crixtiano on 2006-11-28
I'm trying to upgrade my Ubuntu Dappert to Edgy. But I'm having some problems.

Please, lookit the command I have used:

```
$ sudo aptitude update

$ sudo aptitude dist-upgrade

(...)

1079 pacotes atualizados, 227 novos instalados, 127 a serem removidos e 0 não atualizados.
É preciso obter 753MB de arquivos. Depois do desempacotamento, 209MB serão usados.
Os pacotes a seguir possuem dependências não satisfeitas :
  python2.4-libxslt1: Depende: python2.4-libxml2 (>= 2.6.17) mas não é instalável.
  hpijs: Conflita: hplip-ppds (< 1.6.9-0ubuntu2) mas 0.9.7-4ubuntu1 está instalado.
  libgnutls-dev: Depende: libtasn1-3-dev (>= 0.3.4) mas não é instalável.
  libvte4: Depende: libvte-common (= 1:0.12.2-0ubuntu1) mas 1:0.14.1-0ubuntu1 será instalado.
  upstart: Conflita: sysvinit mas 2.86.ds1-14.1ubuntu16 será instalado.
Resolving dependencies...
abrir: 9054; fechado: 4561; adiar: 0; conflito: 3                                                                                                           .Nenhuma solução encontrada dentro do tempo reservado. Insistir? [S/n]
```


The output is in portuguese, but i think you can understand. I have a problem with these packages: python2.4-libxslt1, hpijs, libgnutls-dev, libvte4, upstart

So, what do I have to do to upgrade my system whithout problems?

Thank you...

Cristiano

---

### Post by bapoumba on 2006-11-28
Hi,
could you post the output of **cat /etc/apt/sources.list** ? This will list the content of the sources.list file.

---

### Post by crixtiano on 2006-11-28
Off course, this is my sources.list file:

```
$ cat /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

 deb http://us.archive.ubuntu.com/ubuntu edgy main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu edgy universe
 deb-src http://us.archive.ubuntu.com/ubuntu edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

 deb http://us.archive.ubuntu.com/ubuntu edgy multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu edgy universe

```

Do you have a solution? 

Thank you. ;)

---

### Post by bapoumba on 2006-11-28
You sources.list looks fine (except last line, you probably ment multiverse ;))

One thing though, I cannot find anything related to python2.4-libxslt1 :
> ~ $ apt-cache policy python2.4-libxslt1
python2.4-libxslt1:
  Installed: (none)
  Candidate: (none)
  Version table:

and [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=python2.4-libxslt1&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=python2.4-libxslt1&searchon=names&subword=1&version=edgy&release=all")
or libvte4.

hpijs, (Installed: 2.6.9+1.6.9-0ubuntu2), libgnutls-dev (Candidate: 1.4.0-3ubuntu1) and upstart (Installed: 0.2.7-7) are in main.

So, did you use in the past some repositories that were not from Ubuntu ?

---

### Post by crixtiano on 2006-11-28
Hi,

thank you for try to help me.

But, look that, the packages are in dapper reppository:

python2.4-libxslt1
------------------
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=python2.4-libxslt1&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=python2.4-libxslt1&searchon=names&subword=1&version=dapper&release=all)


libvte4
------------------
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libvte4&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libvte4&searchon=names&subword=1&version=dapper&release=all)


So, what do I have to do now? :confused: 


Cristiano

---

### Post by bapoumba on 2006-11-28
Okay, should have looked ;)

My guess is that you have not yet performed the dist-upgrade, right ?
But if you have, have you cycled several times between update/dist-upgrade ? It is common, as far as I know, and I had to do that one one occasion. Do not restart your computer between the cycles, untill no errors come out.

(and aptitude rocks ;))

---

### Post by crixtiano on 2006-11-28
I did

$sudo aptitude update
$sudo aptitude dist-upgrade 

in the same time

but dist-upgrade show me that mesage.

---

### Post by bapoumba on 2006-11-28
So just do it again, sometimes several cycles are needed.

---

### Post by drphilngood on 2006-11-28
Many people have had problems updating.  Consequently, many choose to use the [alternate installer cd]("http://espelhos.edugraf.ufsc.br/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso")(right click to save) and follow these steps:

**1.** Boot into the alternate installer cd
**2.** shrink the partition Dapper is on
**3.** create a new ¨/¨ partition from the freed space
**4.** use the existing swap partition or create a new one
**5.** install Edgy to the new ¨/¨ partition
**6.** boot into Edgy and retrieve files from the Dapper partition.

In addition, you may find this guide helpful:

[Ubuntu Installation Guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html")

Just wanted to let you know your options.

Good luck!

---

### Post by crixtiano on 2006-11-28
i think not

---

### Post by bapoumba on 2006-11-28
Okay.
have you tried the -f (hard fix, check **man aptitude**) argument with aptitude ? you can run a simulation with -s.

I do not use these two "dapper" packages, as you have noticed, or my upgrade went smoothly for some reason. Do you know what there are here for ? In other words, can you just uninstall them and finish up the dist-upgrade ?

If you have a separate /home, reinstalling edgy (alternate) as suggested will be easy. But will leave us not undertanding what happened ;)

---

### Post by crixtiano on 2006-11-28
I think 
reinstalling edgy (alternate) as suggested in a separate /home, isn't the best solution...

:(

---

