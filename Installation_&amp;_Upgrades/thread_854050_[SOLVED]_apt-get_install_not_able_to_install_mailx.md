---
title: "[SOLVED] apt-get install not able to install mailx or mailutils on Ubuntu 7.10"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by durino13 on 2008-07-09
I want to install mailx, or mailutils on 7.10 and I get following error message:

```
marusiju@pinguin:/data/bin$ sudo apt-get install mailx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  exim4 exim4-base exim4-config exim4-daemon-light libdb4.3 liblockfile1
Suggested packages:
  mail-reader eximon4 exim4-doc-html exim4-doc-info gnutls-bin openssl libmail-spf-query-perl
The following NEW packages will be installed:
  exim4 exim4-base exim4-config exim4-daemon-light libdb4.3 liblockfile1 mailx
0 upgraded, 7 newly installed, 0 to remove and 42 not upgraded.
Need to get 156kB/2226kB of archives.
After unpacking 4846kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mailx 1:8.1.2-0.20070424cvs-1
  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mailx/mailx_8.1.2-0.20070424cvs-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mailx/mailx_8.1.2-0.20070424cvs-1_i386.deb)  302 Moved Temporarily
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I have also tried to change sources.list to other servers, but I always get this error .. If I install other packages, they work ..

My /etc/apt/sources.list is like this:


```
#
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
```

What could be wrong here?

---

### Post by Partyboi2 on 2008-07-10
I can suggest a workaround and that is to manually install the package. You can download it from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/gutsy/mailx")

---

### Post by durino13 on 2008-07-10
1.
I have downloaded following file:

[http://archive.ubuntu.com/ubuntu/pool/main/m/mailx/mailx_8.1.2-0.20070424cvs.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/main/m/mailx/mailx_8.1.2-0.20070424cvs.orig.tar.gz")

extracted using TAR, then cd'd into directory and executed make:

```
marusiju@pinguin:/usr/src$ cd mailx-8.1.2-0.20070424cvs.orig/
marusiju@pinguin:/usr/src/mailx-8.1.2-0.20070424cvs.orig$ ls
aux.c   cmd2.c  cmdtab.c   CVS    edit.c    fio.c      glob.h  lex.c   mail.1  Makefile  names.c      popen.c  rcv.h   strings.c  tty.c    v7.local.c  version.c
cmd1.c  cmd3.c  collect.c  def.h  extern.h  getname.c  head.c  list.c  main.c  misc      pathnames.h  quit.c   send.c  temp.c     USD.doc  vars.c
marusiju@pinguin:/usr/src/mailx-8.1.2-0.20070424cvs.orig$
marusiju@pinguin:/usr/src/mailx-8.1.2-0.20070424cvs.orig$ make
Makefile:20: *** missing separator.  Stop.
marusiju@pinguin:/usr/src/mailx-8.1.2-0.20070424cvs.orig$
```

I get the 'missing separator' error. What am I doing wrong?

2.
Atm, I just want to install a simple MUA ('mail') to be able to send emails from my scripts. Do I have to have MTA installed on localhost (machine, where the script is) for this?

3.
I really wonder, why does 'sudo apt-get install mailx' crashes

---

### Post by Partyboi2 on 2008-07-10
Have you tried installing the deb package from the link I gave you?

---

### Post by Tang on 2008-07-10
## Uncomment the following two lines to add software from Canonical's
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner


Should look like this?

---

### Post by durino13 on 2008-07-11
> **Tang said:**
> ## Uncomment the following two lines to add software from Canonical's
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner


Should look like this?

I uncommented the code, run 'sudo apt-get update' and again 'sudo apt-get install mailx', the same error however occured.

Thx for the help anyway ..

Juraj

---

### Post by durino13 on 2008-07-11
> **Partyboi2 said:**
> Have you tried installing the deb package from the link I gave you?

I went to the page you gave me and I've downloaded 'tar.gz' file from there. I didn't notice, there's a 'deb' file too. I have downloaded this file installed all dependencies using apt-get and finally 'dpkg -i mailx...' and .. :guitar: Works.

Perfect ..

Now I have to figure out, how to use it as my first test gave me this error: 'Mailing to remote domains not supported' ..

I'll study it and in case of questions, I'll be back here again. No need to bother with something I didn't read about yet.

Enjoy my 'thx' reward.

Juraj

---

