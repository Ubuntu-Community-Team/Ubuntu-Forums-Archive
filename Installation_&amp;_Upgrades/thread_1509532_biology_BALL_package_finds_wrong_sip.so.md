---
title: "biology BALL package finds wrong sip.so"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by rwohlhueter on 2010-06-14
I just upgraded to ubuntu 10.04, and installed the BALL biological package.  When I start the BALLview gui, I get the error message:   p, li { white-space: pre-wrap; }  ERROR: Version of imported sip module does not match the expected version!
 got (from <module 'sip' from '/usr/lib/pymodules/python2.6/sip.so'>) 4.10.1, expected 4.10


Where can I get the right version of sip.so?  Better yet, how can I persuade BALLview that 4.10.1 would do just fine?

---

### Post by Neil1 on 2010-09-29
Hi,

I got exactly the same problem. Have you solved it already? Could anyone help?

Thanx a lot!

---

### Post by hal10000 on 2010-11-16
Hello,
i have the same problem in kubuntu 10.10 with ballview.

This thread is marked as solved, but there is no hint on how the problem was solved.

[URL="http://ball-trac.bioinf.uni-sb.de/ticket/285"]On this page
[/URL] they assume it to be a packaging problem, and it seems that it only occurs in ubuntu.

I would appreciate if someone could tell how the problem can be solved

---

### Post by viherpeukalo on 2011-01-20
bump

---

### Post by Rasmuss81 on 2011-02-05
I had the same problem and solved it. 

Make sure you have gsl, flex, libfftw and all the other staff (just read the messages in the console) already installed. 

Get the ball-package from ballview.org and store it for example at /opt 

Copy sip.h from /opt/BALL-1.4.0/contrib/sip-4.11/sipgen to /opt/BALL-1.4.0/contrib/include

Build the package withe the ./autobuild command. 

Then it works partially - There are still problems with the gui but atoms and molecules are drawn correctly.

---

