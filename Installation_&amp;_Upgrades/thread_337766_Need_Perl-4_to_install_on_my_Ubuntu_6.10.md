---
title: "Need Perl-4 to install on my Ubuntu 6.10"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-01-13
I need to install **Perl-4** (yep you read right) on my Ubuntu 6.10

Where can I get it ?


This is because at the office we have Perl-4 on UNIX AIX and there is no way the company is going to upgrade to anything else **EVER** (IBM lost rights to upgrade any software managed under AIX because they apparently illegaly copied some of the UNIX code and got sued for it - see Wikipidia).

So in order for me to improve our tools, I need to do it at home. I have no time at the office.

---

### Post by Browser_ice on 2007-01-14
Any one ?

---

### Post by po0f on 2007-01-14
Browser_ice,

You're going to have to download it from [here](http://ftp.funet.fi/pub/CPAN/src/unsupported/4.036/) and compile it yourself.  If you have any problems, post back.

---

### Post by qamelian on 2007-01-14
Doesn't seem to be available from any of the usual suspects. You may have no option but to locate the source code included with an old distro and "role your own".

Edit: Looks like I should have looked a bit further!

---

### Post by Browser_ice on 2007-01-15
I need step by step description on how I am going to compile this pupy

---

### Post by Browser_ice on 2007-01-18
I need step by step description on how I am going to compile this pupy

---

### Post by Browser_ice on 2007-01-21
I unpacked the package in a folder but when I type MAKE it gives me :

browserice@browserice-desktop:~/temp/src/perl-4.036$ ls
arg.h      cmd.c          cppstdin     form.c    installperl    Makefile.SH     perl.man      regcomp.h       toke.c
array.c    cmd.h          dec_osf1.sh  form.h    INTERN.h       malloc.c        perlsh        regexec.c       usersub.c
array.h    config.H       doarg.c      gettest   ioctl.pl       MANIFEST        perly.fixer   regexp.h        usub
Artistic   config.h       doio.c       h2ph      lib            msdos           perly.h       server          util.c
atarist    config_h.SH    dolist.c     h2ph.man  makedepend     os2             perly.y       solaris_2_1.sh  util.h
c2ph       config.sh      doSH         h2ph.SH   makedepend.SH  PACKINGLIST@33  pstruct       spat.h          Wishlist
c2ph.doc   config.sh.old  dump.c       h2pl      makedir        patch36         README        stab.c          x2p
c2ph.SH    Configure      eg           handy.h   makedir.SH     patchlevel.h    README.ncr    stab.h
cflags     consarg.c      emacs        hash.c    Makefile       perl.c          README.uport  str.c
cflags.SH  cons.c         eval.c       hash.h    makefile       perl-faq        README.xenix  str.h
client     Copying        EXTERN.h     hints     makefile.old   perl.h          regcomp.c     t

browserice@browserice-desktop:~/temp/src/perl-4.036$ make
Expect 27 shift/reduce and 57 reduce/reduce conflicts
/usr/bin/yacc -d perly.y
make: /usr/bin/yacc: Command not found
make: *** [perly.c] Error 127


So I though I needed to remove my current Perl-5 because it was probably conflicting with it but when I select Perl to be removed using SPM, it lists me just about every single package installed as being affected by this removal.

Now how do I do this without causing my system to be removed/disabled ?

---

### Post by Browser_ice on 2007-01-22
Anyone ?

---

### Post by Browser_ice on 2007-01-28
here go again,

ANYONE ?






The thing I hate the most about Ubuntu forums is that when you post a thread, it can sometimes go unoticed for months even if you keep replying back to it asking for help.

---

### Post by hitter on 2007-01-28
hi there..

install make 
$ sudo apt-get install make

Edited:
install gcc
$ sudo apt-get install gcc libc6-dev build-essential

let me know if it works..

---

### Post by Browser_ice on 2007-02-12
Thank you but it looks like I wont be needing it anymore.

I am moving to another floor and therefore, different responsabilities. So I do not need this anymore.

---

