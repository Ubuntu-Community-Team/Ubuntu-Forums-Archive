---
title: "common lisp"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by Craig_Baird on 2014-04-05
Hi, 

I've spent many hours getting emacs and slime set up on ubuntu 12.04LTS as I'm slowly trying to learn common lisp.  I want to upgrade to the new 14.04 LTS ubuntu, but not if I'm going to lose my current emacs/slime set up. So my question is: will I lose my emacs/slime set up if I upgrade to 14.04 lts?

Thanks in advance. 

Ralph.

---

### Post by tgalati4 on 2014-04-05
You will need to do some research to compare the versions of emacs on 12.04 vs 14.04.  If they are different, then your configuration files may not work properly anyway.  Because of the nature of emacs, I would guess that only small changes are made, so your config files will probably be compatible.  But back them up.  If you perform an in-place upgrade and it messes up, then you will have to perform a wipe and clean install.  I'm not familiar with *slime*.  But again I would compare versions available on both distros.

Versions on 12.10:

tgalati4@Mint14-Extensa ~ $ apt-cache policy emacs
emacs:
  Installed: 45.0
  Candidate: 45.0
  Version table:
 *** 45.0 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
tgalati4@Mint14-Extensa ~ $ apt-cache policy slime
slime:
  Installed: (none)
  Candidate: 1:20120525-2
  Version table:
     1:20120525-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by TomR55 on 2015-01-18
For what it's worth ... I had Slime working just fine in 12.04. I recently attempted to install slime and friends in 14.10, running the latest Emacs and ran into a persistent problem:

From what I can tell: cl-swank is trying to compile a Steel-Bank Common Lisp file

; 
; caught ERROR:
;   READ error during COMPILE-FILE:
;   
;     Symbol "CODE-TRACE-TABLE-OFFSET-SLOT" not found in the SB-VM package.
;   
;       Line: 1507, Column: 70, File-Position: 60197
;   
;       Stream: #<SB-SYS:FD-STREAM
;                 for "file /usr/share/common-lisp/source/slime/swank-sbcl.lisp"
;                 {CE26B21}>
; 
; compilation unit aborted
;   caught 1 fatal ERROR condition
;   caught 1 ERROR condition
;   printed 1 note

This is interesting, esp. since I'm intending to use CLisp. I will poke around and see what's up and report back should I find anything useful.

I mention this at this point of the Thread in case anyone else is running into this error.


Tom R

---

