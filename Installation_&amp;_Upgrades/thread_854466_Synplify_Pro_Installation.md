---
title: "Synplify Pro Installation"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by ranthal on 2008-07-09
Hi all,

I am trying to set up an installation of Synplify Pro (an FPGA synthesis tool) on my machine running Ubuntu 8.04.  Synplify is only supported on Red Hat and SuSE so it's taken some faking but I am almost there.  The shell script used to start the Synplify GUI gets hung up on this line of code:

SYN_HOMEDIR/$PLATFORM/mbin/$SYN_PRGM $SYN_ARGS >$ERRFILE "$@";

The first portion refers to the Synplify executable, the second passes the argument -pro to run the pro vertsion, and after the redirect it goes into an error file.  Has anyone tried this before and had this problem?  Oh and one more note, I am currently doing it on my 32-bit machine but the intention is to do it for a 64-bit server later.

I saw an earlier thread on trouble finding libc.so.6 but I already had this problem and solved it by telling the program that I was using kernel 2.6.24 instead of what it originally considered 2.4.1 and this worked.  Thanks!

---

### Post by ranthal on 2008-07-10
[SOLVE]
Since I searched all over and found nothing on this issue thought I'd post the solution and what was causing the hang up.

The big issue was that though Synplify 8.8.0.4 claimed to support kernel versions 2.6.* it really didn't do a very good job of it and this is what caused the hang up I ran into.

The solution, use 9.2.4 or 9.4 beta.  Of course if you are planning to use this for any product I would never recommend using a beta version, but in our lab we ran the install scripts for both and ran into one simple problem: it couldn't find libstdc++.so.5.  Our machines run the .6 version so first we tried setting up a symbolic link from .5 to .6 thinking if it were more up to date it should still work.  It didn't, so just do in the treminal:
sudo apt-get install libstdc++5

Then run the install script and you are good to go.

---

