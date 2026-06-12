---
title: "APL2 on Ubuntu 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by birrcons@googlemail.com on 2010-09-05
Hi all,

I try to get IBMs Workstation APL2 V2, Service level 12 to run on Ubuntu 10.04. I followed the installation instructions on the CD and no error messages where presented. Prerequisites are glibc 2.3.2 or higher, Motif* 2.2 or later and X11R6 or later which all seem to be present on my system. When starting APL2 it shortly shows the main window and then returns following error messages :

chb@ubuntu:~# apl2
chb@ubuntu:~# Warning: translation table syntax error: Unknown keysym name:  XF86Paste
Warning: ... found while parsing '<KeyPress> XF86Paste: insert-selection(SELECT, CUT_BUFFER0)'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  XF86Paste
Warning: ... found while parsing '<KeyPress> XF86Paste: insert-selection(SELECT, CUT_BUFFER0)'
Warning: String to TranslationTable conversion encountered errors

Has anyone encountered this before and could give me some advice on how to resolve the issue ? I'm quite new to linux and have been working with windows for ages now

Greetings from lower bavaria
Christian Birr

---

### Post by birrcons@googlemail.com on 2010-09-09
To whom it may concern:

 the developers of APL2 at IBM help me to solve the issue. For everyone interested in the solution there is a link to the corresponding thread on developerWorks forum

[https://www.ibm.com/developerworks/forums/thread.jspa?threadID=345708&tstart=0](https://www.ibm.com/developerworks/forums/thread.jspa?threadID=345708&tstart=0)

So problem solved...

Christian :D

---

