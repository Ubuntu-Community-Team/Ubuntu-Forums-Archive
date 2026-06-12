---
title: "Problems with (installing) 'make'"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by mukatira on 2006-09-12
[B]Hi,
I was updating the CPAN library and ran into the follwoing problem:[/B]

[I]Writing Makefile for Net::Telnet
Can't exec "usr/bin/make": No such file or directory at /usr/share/perl/5.8/CPAN.pm line 4567.
  usr/bin/make  -- NOT OK[/I]

[B]So,
I downloaded 'make' :  sudo apt-get install make
check ..[/B]
[I]:~$ sudo apt-get install make
Password:
Reading package lists... Done
Building dependency tree... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]
[B]
The error above (usr/bin/make  -- NOT OK) persists!

Help!!

Sm[/B]

---

### Post by NewbieLearnLinux on 2006-09-12
first, you should install the build-essential (gcc, g++, make, etc...)

then you change directory to the respective folder, and configure it to check dependencies.

Then if the folder contains approriate files for "make", the command should do the job...

---

### Post by mukatira on 2006-09-12
[B]Thanks for the reply:
I installed build-essential[/B]

[I]/usr/bin$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

**The problem with /make -- Not OK continues :( **

[I]Can't exec "usr/bin/make": No such file or directory at /usr/share/perl/5.8/CPAN.pm line 4567.
  usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible[/I]

---

### Post by mukatira on 2006-09-12
[B]I think I figured the issues:
During the installation of CPAN, I did not have 'make'
Once I installed 'make' the config.pm file needed to be updated. 
I had to re-initialize CPAN to do that (i am sure there is a better way??!)[/B]

[I]CPAN> o conf init
:
:
:

Where is your make program? [/usr/bin/make]
.
.
.
.
[/I]**Now, I have no issues installing various modules**. 

Cheers

---

### Post by Sgurd on 2007-10-22
Same problem here.  Thanks for the fix.  - JD

---

