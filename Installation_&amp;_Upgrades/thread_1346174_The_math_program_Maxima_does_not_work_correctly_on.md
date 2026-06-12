---
title: "The math program Maxima does not work correctly on Ubuntu 9.10 64 bit?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by beta314xi on 2009-12-04
Hi, I am a beginner with Ubuntu. I just installed ubuntu 9.10 64bit. I then installed the math program maxima using
 	sudo apt-get install maxima
 when I run the program it works only for certain things. For example,
 

 sqrt(1);
 	1
 

 If I try,
 sqrt(2.0);
 	1.414213562373095
 

 but if I try
 sqrt(2);
 	I get a huge error message
 

 

 Universal error handler called recursively(: ERROR NIL
 							CONDITIONS:: CLCS-UNIVERSAL-ERR
 OR-HANDLER
 							'' ''
 							''Couldn't protect'')
 Universal error handler called recursively (:ERROR NIL
 						CONDITIONS:: CLCS-UNIVERSAL-ERROR-HAN
 DLER
 						'' ''Couldn't protect'')
 Maxima encountered a Lisp error:
 Error in CONDITIONS:: CLCS-UNIVERSAL-ERROR-HANDLER [or a callee]: Caught fatal e
 rror [memory may be damaged]
 Automatically continuing.
 To reenable the Lisp debugger set debugger-hoo to nil.
 

 

 Please help!

---

### Post by misterbk on 2009-12-04
> **beta314xi said:**
> 
 but if I try
 sqrt(2);
 	I get a huge error message
 

LOL that's awesome!

Like how you can see frames 0 through 251 of a 250-frame animation in QuickTime.

What is the result you expect to get from sqrt(2)?  In Mathematica, I would expect it to return the symbolic entity sqrt(2), because that symbol has been reduced to its simplest form.  Sqrt(2.0) automatically computes numerically, triggered by the presence of the decimal point.

---

### Post by mionescu on 2009-12-12
Maxima on Ubuntu is very buggy. There is a bug report about this type of errors:
[https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587](https://bugs.launchpad.net/ubuntu/+source/maxima/+bug/303587)

Some people said that the workaround from comment #14 following this bug report helped. I did not try it.

---

