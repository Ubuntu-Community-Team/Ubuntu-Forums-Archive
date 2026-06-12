---
title: "JRE doesn't want to be on my computer (Java Runtime Environment)"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by rugglesworth on 2006-11-26
Hi guys, first post!  This is an Edgy Eft problem.  I'm trying to install Java Runtime Environment for use in firefox.  In terminal, I enter:
> $ sudo apt-get install sun-java5-jre sun-java5-plugin
Everything is fine until
> sun-dlj-v1-1 license could not be presented
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive

dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...

sun-dlj-v1-1 license could not be presented
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive

dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3360
Wrote literal globs at 3360 - 33c4
Wrote suffix globs at 33c4 - 674c
Wrote full globs at 674c - 6770
Wrote magic at 6770 - bd80
Wrote namespace list at bd80 - bd90
***
Selecting previously deselected package sun-java5-plugin.
Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-08-0ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks for reading!!
Ben

---

### Post by deanjm1963 on 2006-11-27
install it via synaptic because a window comes up asking you to agree to the license, otherwise it aborts the installation

---

### Post by rugglesworth on 2006-11-27
I forgot to add.  When I try to use apt get afterwards, it gives me the following error:
> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-08-0ubuntu1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-08-0ubuntu1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-08-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

After this I just do what is says
> sudo apt-get -f install
And it fixes the problem, but this may or may not be of note..

---

### Post by rugglesworth on 2006-11-27
Sorry, I posted my addition before I heard your answer.  I installed via synaptic, and now those two packages are installed, but I still don't have java in firefox.  I am installing the right packages, no?  The particular page I'm using to test:

[http://chir.ag/stuff/sand/](http://chir.ag/stuff/sand/)

---

### Post by deanjm1963 on 2006-11-27
check again in synaptic to make sure you didn't miss a file that "might" need to be installed.

---

### Post by rugglesworth on 2006-11-27
I think I have everything.  I checked my list of what I have against the Ubuntu Wiki article and everything was installed.  I looked through synaptic and there are no broken packages or missing dependencies whatsoever.  I want to point out I am using sun's java as opposed to blackdown java.  Am I doing something wrong?

---

### Post by dcstar on 2006-11-27
> **rugglesworth said:**
> Hi guys, first post!  This is an Edgy Eft problem.  I'm trying to install Java Runtime Environment for use in firefox.  In terminal, I enter:

Everything is fine until
......

What do you think this message is trying to tell you:
```
try '**dpkg-reconfigure debconf**' to select a frontend other than noninteractive
```
If you change the setting as advised, then you will be prompted to accept the licence terms for the Java install, and if you accept them it will install correctly.

---

### Post by rugglesworth on 2006-11-27
Please, pay attention to the current problem in the thread.

We took care of that, and the packages are already installed on the computer.  Java still doesn't work.

Sorry for the misunderstanding.

---

