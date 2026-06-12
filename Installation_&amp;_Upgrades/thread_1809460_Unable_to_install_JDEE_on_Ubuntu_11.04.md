---
title: "Unable to install JDEE on Ubuntu 11.04"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by rpjohns on 2011-07-21
I have a new machine with a fresh install of ubuntu 11.04 64 bit. I'm trying to cobble together emacs/jdee java development environment. I was able to use package manager to install emacs23 but I can't install jdee. I've found it in package manager, but when I mark it for install I get the red exclamation point. 

So I understand that some dependencies are missing but it doesn't say what. I've combed over the dependent packages and find most of them, although there are few  I can't find, e.g.,  eieio, speedbar, and a few others. Is there a repository I can add that will pull in all of the dependencies needed for the emacs23./jdee combination?  If that's not possible, does anyone have a recipe for getting emacs23 and jde working under ubuntu 11.04 natty? I had emacs22/jde working under my previous config (ubuntu 10.04 LTS Lucid Lynx).

Any help would be much appreciated. Thanks

---

### Post by steve11911 on 2011-07-22
You may have seen these but just in case:

[http://pkgs.org/ubuntu-11.04/ubuntu-multiverse-i386/jde_2.3.5.1-5_all.deb.html](http://pkgs.org/ubuntu-11.04/ubuntu-multiverse-i386/jde_2.3.5.1-5_all.deb.html)

(scroll down)

and:

[http://packages.ubuntu.com/natty/jde](http://packages.ubuntu.com/natty/jde)

There are some bug reports associated with jde and 11.04 which might provide you with some resources:

[http://osdir.com/ml/ubuntu-bugs/2011-05/msg41116.html](http://osdir.com/ml/ubuntu-bugs/2011-05/msg41116.html)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=620341](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=620341)

One more thought:

If it ain't broke don't fix it...

---

### Post by rpjohns on 2011-07-22
Thanks for the reply. I did see this stuff, except the one new piece of info is that cedet-* has been subsumed in the emacs23 release -- at least that's the way I read it. Anyway, the synaptic package manager for natty 11.04 simply lacks some of the packages jde depends on.  It would seem that my only option is to grab the individual packages where ever I can find them and try to install everything by hand. Is this a dumb idea? Or can it be done if done carefully?  IOW, if I carefully unpackage everything into the proper directories (using my ubuntu 10 lynx as an example) can I succeed?

Another question. I'm trying to install under ubuntu 11.04 64 bit. Does that mean I have to seek out packages that are specifically 64 bit?

Oh, and I'm not sure what you meant by 'if aint broke....' but if you were referring to moving to 11.04, I have no choice. Anyway, thanks for the response, it was gettin a little lonely.

---

### Post by rpjohns on 2011-08-31
I wanted to let the forum know that I resolved this issue by scrapping 11.04 and  installing 10.04 LTS 64bit. After doing so it was straight forward to install emacs 22 and jde. Everything runs great. Special thanks to  steve11911 who really walked me through the issues to arrive at the best solution. Thanks for taking time Steve.

---

### Post by graemev on 2011-11-26
Damm I was hoping somebody had solved the issue of getting JDE  installed in natty.

I tried when natty 1st came out , gave up and needed to try again now.

In case it's not clear. With natty and standard repositories simply trying to use synaptic to install the JDE package causes the packages to be marked as broken.

Looks like not all the dependent  packages are available, possibly because the functionality has been subsumed.

#apt-get install jde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 jde : Depends: cedet-contrib (>= 1:1.0pre4-2) but it is not installable
       Depends: cogre (>= 1:1.0pre4-2) but it is not installable
       Depends: eieio (>= 1:1.0pre4-2) but it is not installable
       Depends: semantic (>= 1:1.0pre4-2) but it is not installable
       Depends: speedbar (>= 1:1.0pre4-2) but it is not installable
       Recommends: ecb but it is not going to be installed

---

