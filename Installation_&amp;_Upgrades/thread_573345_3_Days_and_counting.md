---
title: "3 Days and counting"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Zabier6 on 2007-10-11
Hi thanks for looking at my post!!
  
      I have just installed Ubuntu 7.04 for the first time, 3 days ago. I have been to web site after web site and forum after forum I have gotten to the point of just wanting to reinstall windows on my computer.
All I want too know is once I download a file/program from the internet ( Like: Real Player, Java, graphics card drivers) HOW do I install them ( Like: .rpm, .deb, .tar, ECT. ) 
I keep trying all the advice from other Linux user and have gotten nowhere.

There has got to be a universal way for all the file types/from my DESKTOP

So what I would like to know is how do I use Terminal to install any file type that I have downloaded to my desktop. In NOOBIE friendly terms Please please please!!!!
I mean step by step ](*,)

and THANK YOU for YOUR help \\:D/

---

### Post by SuperDuck on 2007-10-11
I did a Google search for "How to install programs in Ubuntu", ;) and this is the first page that came up:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

It has everything you need right there.  About halfway down it starts talking about how to install .deb, .rpm, etc. manually.

Good luck!

---

### Post by cward002 on 2007-10-11
Try the link below:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

it should answer a lot of your questions about installing stuff in Ubuntu.

If you have any questions, just post back and I will help to the best of my 
ability.

---

### Post by cward002 on 2007-10-11
rats!!! SuperDuck beat me LOL

---

### Post by SuperDuck on 2007-10-11
Gotta be quick, mate. ;)

---

### Post by qpieus on 2007-10-11
Hi and welcome. Conrats for trying out a different OS. If you stick with it you'll see how neat linux is. Here's a link to a webpage that explains very well how to install stuff in linux:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

It has sections for you concerns - deb files, rpm, tar, etc.

For deb files, it's super easy. Simply right click on the file and you should see an install option. Click on that and it installs. One note though, not all deb files are the same. Some deb files are specific to the different versions of ubuntu. For example, a deb built for ubuntu 7.04 might not install correctly on ubuntu 6.06. So, if you are looking for a deb file for an app, look for something specific for your ubuntu version.

One other thing though, you should rarely have to download apps from the internet. Most apps you might want to try are located in the ubuntu repositories (application servers) and you can install any of them, painlessly, through an application called synaptic which you can find in your menus. That webpage I linked to discusses synaptic also.

Have fun!

---

### Post by jdfreshwater on 2007-10-11
The best way to install software with ubuntu is using the synaptic package manager, which will go out to the repositories and get the software for you.

If you are installing a downloaded .deb you can use the dpkg command to install.

If you are installing an rpm, then you must use alien to convert the package to a .deb and then use dpkg to install.  

.tar.gz or .tar are generally source files.  To install these you need to expand them, and then look at the readme.  in general you may have to run ./configure, you will run make and then make install.

At this time there is no given way to just install any type of package using the same command.  Each type has their own way of install.

---

### Post by qpieus on 2007-10-11
OK this is too funny. 3 people responding with the same link within a couple of minutes of each other. Low hanging fruit I guess.

---

### Post by Zabier6 on 2007-10-11
Thank You Alot 
Im sure you all get this alot 
                    :-k

---

