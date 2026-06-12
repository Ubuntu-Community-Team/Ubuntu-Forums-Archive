---
title: "[SOLVED] Not able to load build-essantial package"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-09-22
I get the following error message while trying to load the build-essential program:
> aaiterminator@terminator-desktop:~$ aai build-essential 
[sudo] password for terminator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done


---

### Post by xebian on 2008-09-22
> **alienexplorers said:**
> I get the following error message while trying to load the build-essential program:

Not sure what you mean by 'load'. I'm guessing here that you are trying to install it?  I'm guessing too that you did an update prior to executing aai?

Also, it would be nice if you tell us exactly what 'aai' means so we can try to figure out what's wrong.  I'm guessing it's an alias/script for apt install?

---

### Post by alienexplorers on 2008-09-22
aai is a alias for sudo aptitude install.  Yes I was trying to install not load the files.  Yes I ran sudo aptitude update before trying to install build-essential.

---

### Post by alienexplorers on 2008-09-22
Any body know how to fix this error.

---

### Post by xebian on 2008-09-22
> **alienexplorers said:**
> aai is a alias for sudo aptitude install.  Yes I was trying to install not load the files.  Yes I ran sudo aptitude update before trying to install build-essential.

I think build-essential is already installed.

Pls post the result of

aptitude search build-essential.

---

### Post by Nullack on 2008-09-22
I dont use aptitude. What happens when you try to do

sudo apt-get install build-essential?

---

### Post by Foaming Draught on 2008-09-23
> **Nullack said:**
> What happens when you try to do

sudo apt-get install build-essential?The very question I asked myself when I saw a similar thread here saying that g++ was a dependency which wouldn't be met with Synaptic.  sudo apt-get install build-essential worked fine (Alpha 6, 32 bit) and pulled down all dependencies including g++

---

### Post by alienexplorers on 2008-09-23
Tried Aptitude again with new Kernel and it worked fine.  And yes build-essential is installed.

---

### Post by dawynn on 2008-09-23
This part was an indication that apt-get had nothing to do.  The package was already installed.
> No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used. 

Still, I can imagine that this error was a bit disconcerting:
> 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = (unset),
LC_ALL = (unset),
LANG = "en_US.UTF-8"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory


This is not so much an issue specific to apt-get, or even to installing a particular package.  This is more general to your system, and indicates that you may not have the locale tools that its looking for.

Honestly, as a US-English speaker, I've been known to strip packages that do things like set locales.  When I do that, errors like the above are not uncommon.  The reassuring bit is found here:

> 
perl: warning: Falling back to the standard locale ("C").


That would be the code for standard English.  Generally, if you're having no problems understanding the messages on your screen, locale errors should not concern you overmuch.  Locale settings are what lets Linux know what language you understand.

As for what needs to be installed to stop seeing these locale message, I'm not certain.  The issue here is not build-essential.  It has to do with locale tools.  Perhaps someone else can help identify the source of the locale problem?

---

