---
title: "cant dpkg a file"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by roschell on 2008-02-28
anyone knows how to resolve the issue with .... following is the part of my command and report:

sudo dpkg -i lexmarkz22-z32_1.0-6_i386.deb
Password:
(Reading database ... 139551 files and directories currently installed.)
Preparing to replace lexmarkz22-z32 1.0-6 (using lexmarkz22-z32_1.0-6_i386.deb) ...
Unpacking replacement lexmarkz22-z32 ...
Setting up lexmarkz22-z32 (1.0-6) ...
/usr/local/lexmark/z32/lexmarkz22-z32: error while loading shared libraries: libvdkcompo.so.1: cannot open shared object file: No such file or directory
dpkg: error processing lexmarkz22-z32 (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lexmarkz22-z32

It seems that the libvdkcompo.so.1 is linked somewhere else...
Thanks

---

### Post by dstew on 2008-02-28
I assume you are trying to get your Lexmark printer to work. What model printer is it? What flavor of Ubuntu do you have?

EDIT: Are you trying to do [this]("http://ubuntuforums.org/showthread.php?t=609497")? If so, you need to create the links mentioned. The RPM package is designed for the Red Hat system, which has a different file structure than the Debian-based Ubuntu. You need the links to correct that problem.

---

### Post by roschell on 2008-02-28
Hi, thanks for reply. 

I am trying to install lexmark z32 on my laptop running 7.04, and possibly lexmark x215 of my mother's in law where is gutsy.
So far I have followed the link and linked all the files..., what means the 

Run the lexmark-foomatic-kit (reinstall something first)

---

### Post by dstew on 2008-02-28
> what means the Run the lexmark-foomatic-kit (reinstall something first)It means download [this]("http://openprinting.org/download/printing/lexmark-foomatic-kit.tar.gz"), expand it, and read the README file in the lexmark-foomatic-kit folder.

---

### Post by roschell on 2008-02-28
Just installed the foomatic, ./install, ran it by lexmarkinstall and when setting up it returned 
this:

Please enter a name for your printer: Lexmark32

Installing your printer under the name Lexmark32 ...
Use of uninitialized value in string eq at /usr/share/perl5/Foomatic/DB.pm line 2571.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Foomatic/DB.pm line 2571.
sh: /usr/sbin/lpadmin: not found
Could not set up/change the queue "Lexmark32"!
Could not install your printer with Foomatic! at /usr/sbin/lexmarkinstall line 237, <STDIN> line 4.

Im trying to get it working on parallel port...

---

### Post by dstew on 2008-02-28
Did you run lexmarkinstall as root? (That is, using sudo)

---

### Post by roschell on 2008-02-28
yes, I did, and still got the respond

---

### Post by dstew on 2008-02-28
Sorry, I am pretty much out of ideas.

---

