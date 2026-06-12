---
title: "apt-get unable to fetch all archives for eclipse"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by noobad@linux on 2011-01-17
[B]i m working on ubuntu 10.04.01(LTS)

ravi@ravi-laptop:~$ sudo apt-get install eclipse[/B]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  eclipse-jdt eclipse-pde eclipse-platform eclipse-plugin-cvs
The following NEW packages will be installed:
  eclipse eclipse-jdt eclipse-pde eclipse-platform eclipse-plugin-cvs
0 upgraded, 5 newly installed, 0 to remove and 209 not upgraded.
Need to get 67.5MB/127MB of archives.
After this operation, 145MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe eclipse-platform 3.5.2-2ubuntu4.2
  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-platform_3.5.2-2ubuntu4.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-platform_3.5.2-2ubuntu4.2_i386.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

after this i tried apt-get update.. this worked properly but apt-get install eclipse showed same error

i tried changing source but that also didnt work
please help...**need it urgently**

---

### Post by daredevil82 on 2011-01-17
When did you try this?  I downloaded eclipse-jdt roughly 12 hrs ago, and got a 404 error when my router went screwy.  A simple reset fixed it and eclipse installed fine.

What language do you work in?  Maybe if you installed the language package instead...

---

### Post by noobad@linux on 2011-01-17
how did you reset it.....did you mean restarting networking ...?
i did /etc/init.d/networking restart.....still problem remains same 403 error

---

### Post by xuta on 2011-01-17
In fact, I recommend you to use Eclipse Galileo version [http://www.eclipse.org/downloads/packages/release/galileo/r](http://www.eclipse.org/downloads/packages/release/galileo/r) instead of aptitude version.
I've used both of them, so Galileo is better.

---

### Post by daredevil82 on 2011-01-17
by reset I meant turn the power on and off.  You can try downloading the tarball from the Eclipse site, but remember that Helios has several unfixed bugs regarding subclipse/subversion plugins, which is why I stayed with Galileo.

Another option would be for you to install eclipse using the Software Center.  However, if you do it this way, be prepared for several subclipse/subversive plugin errors that were somehow resolved when installing from aptitude.

Xuta, the aptitude version of eclipse is Galileo, no difference between installing from a tarball or aptitude.

---

### Post by noobad@linux on 2011-01-18
i tried doing reset and software center both...none these worked.... 
Does this error have anything to do with version of eclipse i am downloading   
because 403 forbidden error is not allowing me download any files anymore 
   but i am able to update apt-get...    

  apparently i found that only i am having this problem rest all my friends are using same settings still they are able to download all eclipse files  

AND MORE THING I WANT TO MENTION   
    we have a proxy server and they block download if file size is more than 50 MB.....is this error because of this?????  appreciate ur help...but need more :)

---

