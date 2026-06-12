---
title: "Problem with installing software in 13.04. Install tools are not working"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by spectatorx on 2014-03-06
Today i've installed ubuntu 13.04, installed some basic software (restricted-extras, skype, kadu, jockey-common, curl, steam, gpu drivers, etc.) and after reboot i can't install any software.

I'm getting error messages, in synaptic:
> 

Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Use of uninitialized value in subroutine entry at /usr/share/perl5/Debconf/Encoding.pm line 65, <> line 1.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin



This one shows in details when i'm trying to fix broken packages via synaptic.

How to fix it? Kernel 3.13.5

---

### Post by ajgreeny on 2014-03-06
13.04 is no longer supported so you really need to use a later version, I'm afraid.

---

### Post by spectatorx on 2014-03-06
I'm aware of it, i'm using 13.04 because of a reason. 13.10 is not working properly with my hardware, there is still too long time to 14.04 release and i do not want to use old LTS as it is old.

---

### Post by spectatorx on 2014-03-06
That's an output of sudo apt-get -f install:

> 

spectator@Arena-Fighter5:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin
The following NEW packages will be installed:
  libc-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1190 kB of archives.
After this operation, 3561 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)




---

### Post by ibjsb4 on 2014-03-06
Its really hard to get support on the no longer supported.

Why not just go ahead and install 14.04?  At least there is a good support forum for that :)

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

