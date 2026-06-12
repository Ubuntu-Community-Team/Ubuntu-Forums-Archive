---
title: "Trying to install freemind on ubuntu"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by jon80 on 2013-05-14
I have encountered a bit of a problem trying to install FreeMind on Linux, and, I am not sure how to do it the right way, because it would seem that I cannot install rpm packages nor do I have the knowledge on replacing the current JDK version with sun java.

jonathan@ubuntu:~$ java -version
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.3) (6b27-1.12.3-0ubuntu1~12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)
jonathan@ubuntu:~$ 

 rpm -ivh freemind*.rpm jcalendar*.rpm jgoodies-forms*.rpm
Excerpt from [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Install_Java_the_Debian_way](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Install_Java_the_Debian_way).

---

### Post by TheFu on 2013-05-14
Ubuntu doesn't use RPMs.  Depending on the version of Ubuntu you are running, there is a friendly package manager - look for "software center" in the Dash or install and run** synaptic** and find freemind inside that GUI tool .... or just run:
$ sudo apt-get update
$ sudo apt-get install freemind
That should do it. All the dependencies will be handled, including the java needed.  It is best to avoid installing specific versions of any tool that is outside the repositories when you are new to an OS. It adds all sorts of program maintenance overhead that you probably aren't ready to handle.  A few years ago, I wrote an article for Lifehacker about Linux desktop system maintenance.  Here's a more current link to that article: [http://www.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://www.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

If you google "linux system maintenance", you'll find the Lifehacker article as the top link. A few other links about package management:

It is best to stay with program versions provided by a repository for your distribution OR through a PPA.  These links explain more about that: 
* [http://blog.jdpfu.com/2009/10/16/simple-os-and-application-management](http://blog.jdpfu.com/2009/10/16/simple-os-and-application-management)
* [http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches](http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches)
* [http://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop](http://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop)

Anyway, I hope this helps.

---

### Post by oldos2er on 2013-05-14
> **jon80 said:**
> I have encountered a bit of a problem trying to install FreeMind on Linux, and, I am not sure how to do it the right way

Does ```
sudo apt-get update && sudo apt-get install freemind
``` not work for you?

---

### Post by sg_2342 on 2013-11-03
Is there a PPA to install freemind version 1.0.0 under Quantal?

---

