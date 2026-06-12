---
title: "How I do a manual installation of a package?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by linuxspy007 on 2010-06-08
For instance, how do I manually install or upgrade the gcc package (so that the g++ compiler is included)? The reason I ask is because I have a computer that is isolated from the Internet and needs to remain that way. So I need to download the package and be able to install manually.....Any suggestions?

---

### Post by darkod on 2010-06-08
[http://packages.ubuntu.com/search?keywords=gcc-4.2](http://packages.ubuntu.com/search?keywords=gcc-4.2)

Select the ubuntu version you need it for. The bad thing is you need to watch out on which packages it depends, and get them too. And then whether those packages depend on another package.

You need to download all of them, and hopefully the install should work.

---

### Post by linuxspy007 on 2010-06-09
Thank you.  I am running Ubuntu 9.1 I downloaded gcc-4.4_4.4.1-4ubuntu9_i386.deb (which I assume comes with a g++ compiler and everything else I need to compile a C++ hello world program?) and I get when I double click the deb file:
 
[COLOR=red]ERROR: Dependency is not satisfiable: gcc-4.4-base (=4.4.1-4ubuntu9)[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][/COLOR]

---

### Post by darkod on 2010-06-09
Do you have gcc-4.4-base installed?

I guess in a situation like this you need to go "backwards". First install the lowest level packages, that don't depend on another package but are needed for the "higher" level packages.
Then the next step, then next, etc, until you install gcc-4.4 with all other necessary packages already installed so it shouldn't complain about anything.

---

### Post by linuxspy007 on 2010-06-21
Thank you, I tried downloading the packages, now it seems I am stuck with circular dependencies. g++XX depends on libstdXX and libstdXX depends on g++XX. On a machine with an internet connection I was able to get g++ via sudo apt-get... Is there a way to burn a g++ installation to a CD and then stick the CD in the machine without the Internet connection and install?
 
EDIT: I just figured it out.  Apparently you can go into the synaptic package manager>Repositories>Ubuntu software settings and check the CD rom box.  Then do a sudo apt-get install g++

---

