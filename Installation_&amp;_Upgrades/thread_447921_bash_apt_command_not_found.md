---
title: "bash: apt: command not found"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by mailbox on 2007-05-18
so, i rebooted the other day and was reminded why i never reboot:
"bash: apt: command not found."
what happened here? how can i get apt back? naturally, i can't apt-get apt, and i can't get back into my gui, but all my data is still there.

---

### Post by bernied on 2007-05-18
Are you sure that apt is related to apt-get?
```
$ man apt
DESCRIPTION
       The tool apt, annotation processing tool, includes a set of new reflec&#8208;
       tive APIs and supporting infrastructure to process program annotations.
       The apt reflective APIs provide a build-time,  source-based,  read-only
       view  of  program  structure.  These  reflective  APIs  are designed to
       cleanly model the Java(TM) programming language&#8217;s type system after the
       addition  of  generics.  First, apt runs annotation processors that can
       produce new source code and other files. Next, apt can  cause  compila&#8208;
       tion  of  both original and generated source files, easing development.
       The reflective APIs and other APIs used to interact with the  tool  are
       subpackages of com.sun.mirror.

       A  fuller  discussion  of how the tool operates as well as instructions
       for developing with apt are in Getting Started with apt. @
       http://java.sun.com/javase/6/docs/technotes/guides/apt/Get&#8208;
       tingStarted.html
```

---

### Post by mailbox on 2007-05-18
hmm.
always thought they were connected.

brb.

---

### Post by girishv on 2007-05-18
Hi,

I am not sure about the apt you have got bernie, this is what man apt tells me on my feisty

> 

SYNOPSIS
       apt

DESCRIPTION
       APT  is	a  management system for software packages.  It is still under
       development; the snazzy front ends are not yet available.  In the mean
       time, please see apt-get(8).


but, when I try to run apt, I get the following error
The program 'apt' can be found in the following packages:
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
Make sure you have the 'multiverse' component enabled


So, I am confused about why there should be two man pages for the same application (which you can not find in the default installation )

Girish

Girish

---

### Post by bernied on 2007-05-18
I installed that java package just the other day, so that I could run limewire (not worth it, use frostwire instead), that's why I have that man page. I'm guessing the other man page is very old as it's clearly out of date. There are plenty of snazzy front-ends for apt-get and dpkg system, but I'm almost certain that none of them are called apt (aptitude, adept, and what's the one for gnome?).

So, mailbox, if you post some more details about your problem, someone here is sure to be able to help.
Does apt-get work, for instance?

I don't think you actually need any package manager to work in order to boot, even for a desktop, so it's probably something else.

---

