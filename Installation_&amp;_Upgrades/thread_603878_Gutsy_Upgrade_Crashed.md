---
title: "Gutsy Upgrade Crashed"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by chaskins on 2007-11-05
Hi,

During the upgrade process to Gutsy it crashed. I restarted and completed the upgrade but now when I install any packaged I get errors about:

 gij-4.2
 gij
 java-gcj-compat
 libglib-java-gcj
 libcairo-java-gcj
 libgtk-java-gcj
 libswt3.2-gtk-gcj

When I run sudo 'apt-get install -f' I get the following message:

> 
chris@Manta:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gij-4.2 (4.2.1-5ubuntu5) ...
Exception during runtime initialization
Aborted (core dumped)
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.2 (>= 4.2.1-5); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.2 (>= 4.2.1); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
Setting up libglib-java-gcj (0.4.2-7ubuntu1) ...
Exception during runtime initialization
dpkg: error processing libglib-java-gcj (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libcairo-java-gcj:
 libcairo-java-gcj depends on libglib-java-gcj (>= 0.4.2); however:
  Package libglib-java-gcj is not configured yet.
dpkg: error processing libcairo-java-gcj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-java-gcj:
 libgtk-java-gcj depends on libglib-java-gcj (>= 0.4.2); however:
  Package libglib-java-gcj is not configured yet.
 libgtk-java-gcj depends on libcairo-java-gcj (>= 1.0.8); however:
  Package libcairo-java-gcj is not configured yet.
dpkg: error processing libgtk-java-gcj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libswt3.2-gtk-gcj:
 libswt3.2-gtk-gcj depends on gij-4.2; however:
  Package gij-4.2 is not configured yet.
dpkg: error processing libswt3.2-gtk-gcj (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.2
 gij
 java-gcj-compat
 libglib-java-gcj
 libcairo-java-gcj
 libgtk-java-gcj
 libswt3.2-gtk-gcj
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anyone have any ideas how to resolve this?

Thanks

Chris

---

### Post by louieb on 2007-11-05
Might try this.
[http://ubuntuforums.org/showthread.php?t=565837](http://ubuntuforums.org/showthread.php?t=565837)
it says:
```
 sudo dpkg --configure -a
```

---

### Post by chaskins on 2007-11-06
Hi,

Thanks for the help. Howeverits does not solve the problem. I get the same/similar message as before 

> 
chris@Manta:~$ sudo dpkg --configure -a
[sudo] password for chris:
Setting up gij-4.2 (4.2.1-5ubuntu5) ...
Exception during runtime initialization
Aborted (core dumped)
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libswt3.2-gtk-gcj:
 libswt3.2-gtk-gcj depends on gij-4.2; however:
  Package gij-4.2 is not configured yet.
dpkg: error processing libswt3.2-gtk-gcj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on gij-4.2 (>= 4.2.1); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.2 (>= 4.2.1-5); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
Setting up libglib-java-gcj (0.4.2-7ubuntu1) ...
Exception during runtime initialization
dpkg: error processing libglib-java-gcj (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libcairo-java-gcj:
 libcairo-java-gcj depends on libglib-java-gcj (>= 0.4.2); however:
  Package libglib-java-gcj is not configured yet.
dpkg: error processing libcairo-java-gcj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-java-gcj:
 libgtk-java-gcj depends on libglib-java-gcj (>= 0.4.2); however:
  Package libglib-java-gcj is not configured yet.
 libgtk-java-gcj depends on libcairo-java-gcj (>= 1.0.8); however:
  Package libcairo-java-gcj is not configured yet.
dpkg: error processing libgtk-java-gcj (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.2
 libswt3.2-gtk-gcj
 java-gcj-compat
 gij
 libglib-java-gcj
 libcairo-java-gcj
 libgtk-java-gcj
chris@Manta:~$



Is it a case of re-install Gutsy from scratch :(

---

### Post by bulldog on 2007-11-06
Reinstalling from scratch is done in half an hour.
How long did the upgrade take?
Maybe you can create a separate /home partition so your personal data won't be lost all the time.

I have 4 Linux distro's installed and they all use the same /home partition and the same swap.
Just use different login names for the distro's and you get separated folders in the /home folder,so you can copy data between them,but won't be bothered by preferences you don't want.[the . folders]

---

### Post by talkeetnik on 2007-11-26
Nasty upgrade crash for me too!

was able to get things up and running with rebooting and tweaking
but similiar java, gij issues as well

Every apt-get install or update would give
"Setting up gij-4.2 (4.2.1-5ubuntu5) ...
Bus error (core dumped)
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gij-4.2
E: Sub-process /usr/bin/dpkg returned an error code (1) "

Always have hated "Core Dumps"

Tried the suggestions in this thread and found that the reinstall suggestion was not
necessary (as well as a show stopper for new users)
At least for me anyway this is how I resolved the problem

basically tracking down the offending packages and
apt-get remove <package name>
gij took me awhile to figure out as it needed the full
apt-get remove gij-4.2
to work.....
So now no error messages with apt-get . Of course this did not harm the system
before but I wonder if the issues  did in fact cause the "upgrade crash" which
would certainly be a "freak out" for new or unwounded veterans of the Linux battles :o)

HTH

WH Bouterse
Planetary Citizen

---

### Post by clubsoda on 2007-11-27
Yes, removing gij seems like a good idea.  
[QUOTE="talkeetnik"]I wonder if the issues did in fact cause the "upgrade crash" [/QUOTE]Almost certainly.  See here:-
[http://wiki.debian.org/ArmBuilddWatch](http://wiki.debian.org/ArmBuilddWatch)

---

