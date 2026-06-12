---
title: "Package dependencies during installation and removal"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Seb_77 on 2011-11-07
Hi,

I am a linux newbie and I am concerned with the way all the linux tools that handle installation or removal of applications "live" together. I wish to know the best conduit to adopt to avoid breaking dependencies by removing critical packages but still save disk space by not leaving unused libraries on the system. 

Most linux users manage the installation/removal of their applications through various means:  the software center (SC), synaptic package manager (SPM), apt-get shell calls (APT) and from manual source compilation/copy with make (MC).  If I understood it right SC and SPM are mostly graphical front-ends to APT.  

Let's imagine a simple scenario where a user "manually" installs 2 new packages with the apt-get commands on a fresh linux box:
Step 1) A package A is installed: an executable EA and 2 libraries LA1 and LA2 are installed from A plus an extra package B which is automatically downloaded and installed since it is specified as a dependency to A.
  Step 2) A package C is installed: an executable EC and 1 library LC1 are installed; C 
additionally requires the package B and the library LA2.
  
Now the questions:
1) Are the dependencies of A and C on B specified in the packages A and C themselves?
2) What are the default paths where the executables and the libraries are installed? Are they ALWAYS specified in the packages themselves?
3) In step 2, will APT install LA2 and B or notice that it they are already "somewhere" and smartly link their paths with symbolic links in the required locations?
  4) Can the package A be safely removed  by APT without having C dependency on LA2 and B broken? Will APT at least remove EA and LA1?
5) Can the package C be safely removed  by APT without having A dependency on LA2 and B broken? Will APT at least remove EC and LC1?
6) What if A OR C had been installed by the software center or SPM, will the answers to 4 and 5 be the same?
7) What if A OR C had been installed manually from source, will the answer to 4 and 5 be the same?
8) If C is installed from source will LA2 (assume it is a dynamic library) be re-installed or will it be checked for presence first? Is this behavior controlled by the make file? If LA2 is a static library should the path to it be specified in the library path? If LA2 source included in the source code package will it always be re-installed or is this situation smartly handled?
9) How come the situation where obsolete packages are found by APT (which suggests to  remove them by autoremove) be raised? Is it always safe to use autoremove or might it be sometimes a problem? If so in which concrete scenarios?
  10) Altogether is it safe to use the 4 installation/removal ways or should one stick to manual source installation + a single package manager? If so which package manager? 
  Sorry for asking so many questions... what would be the best source to find the answers to them?

  Cheers!
  [FONT=&quot]Sébastien[/FONT]

---

### Post by snowpine on 2011-11-07
Welcome to the forums!

The following page should answer most of your questions (it's for Debian but of course Ubuntu package management is based on Debian's):
[http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.html](http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.html)

Looking over your lengthy question :) I think you basically understand how it works. The one piece of information I think will make it all fall into place for you is this: Installing a package automatically installs all of its dependencies, but uninstalling a package does not automatically remove these dependencies. That's what 'apt-get autoremove' is for.

[http://manpages.ubuntu.com/manpages/oneiric/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/apt-get.8.html)

---

### Post by Seb_77 on 2011-11-12
Thanks a million, extremely valuable source! I definitely have to go through it! I had the feeling the Debian crowd was made out of purists... 

You said removing a package does not remove automatically its dependencies. I understand that if these dependent packages are required by another package (that has been installed more recently) they should not be removed for the sake of stability but if it is not the case they should be removed, no? Said differently the auto remove feature should not be strictly necessary as the action could be taken automatically. Does it mean that the application leaves these packages behind because it is (for some reasons) not 100% sure it would not harm anything - maybe because all the dependencies of the system are not centralized in a single place? I read some people crashed their system with auto remove so I am still a bit worry about using it... is there a way to assess the damages that can be done or to easily backup and restore (be it in recovery mode)?

Thanks again!
Cheers,

Seb

---

### Post by snowpine on 2011-11-12
I don't know the answer specifically to your question, my guess is it's all about having fine-grain control of the system. When you uninstall a package, you can choose to uninstall its dependencies as well, or not, depending on your needs that day. Linux people generally prefer having a choice to not having a choice, all other things being equal. :)

---

