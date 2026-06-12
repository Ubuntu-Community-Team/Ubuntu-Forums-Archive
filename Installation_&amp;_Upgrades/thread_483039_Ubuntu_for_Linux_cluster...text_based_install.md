---
title: "Ubuntu for Linux cluster...text based install"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by technomaniac on 2007-06-24
I am doing my Bachelor's in Computer Science. We are running a cluster of 8 computers(P III 833 Mhz, 128 MB RAM, 100 GBps LAN). This is just a trial. We will go for better and bigger cluster once we learn more about cluster management. 

I want to know if it is possible to install Ubuntu in text mode. We are using RHLE 7 right now but I want something more latest. And I want Ubuntu because its community support is superb. We need to run OpenMosix, Oscar and MPI on it.

 We dont want a GUI. Just SSH and the stuff.

---

### Post by Turboaaa2001 on 2007-06-24
This is a really good question. When this is answerd I'm printing it out and placing it in my "Linux Binder".

I'm actually more interested on a beowolf cluster than redundency. I have many computers and my collection is growing. I want to beable to link them together and use all their processing power together. This is more a hobby thing than actuall productivity...

I also want to know how to install in text mode, I'm having problems witht the gui install when I'm not going to use it.

---

### Post by Herman on 2007-06-24
:D Hello there technomaniac and Turboaaa2001, 
Maybe the following link will be a little bit helpful to you if you are interested in using the 'text mode' ('Alternate CD') installer, [Illustrated Dual Boot.]("http://users.bigpond.net.au/hermanzone/")
Happy computing,
Regards, Herman :D

---

### Post by rillip on 2007-06-25
Just be aware that you're forging into largely uncharted territory; the number of people working on grids out there is miniscule compared to other projects because it's so new.  So don't look for *too* much help with it.  But yes, the alternate CD as Herman posted is the way to go for a textual installer.  If you end up with a gui, it's easy to uninstall, or you can just not use it.  If you end up in a gui login screen, i.e. kdm or the gdm, login managers allow you to switch to a console session before logging in and starting the full gui.

---

### Post by technomaniac on 2007-06-25
Yeah clustering is still a uncharted territory. I get most of my help from beowulf mailing lists and a research institute which has deployed a cluster. But if I ever need some help in tweaking Linux, this community will be of great help. And yes, I have got my answer. I am downloading the alternate CD right now.

---

### Post by tutomlin on 2007-08-10
Not sure how far you've gotten from this but the stable version of OpenMosix is on the 2.4.26 kernel, and I know that the latest versions of the x server distributed with ubuntu won't work on that kernel. (I know you don't want gui stuff but my point is other stuff may not work well either.)

There is another project called kerrighed which is supposed to do the same stuff, but seems to be much more up to date that the openmosix project.

Also I'm not sure how kernel level cluster solutions like mosix and kerrighed interact with software level packages like Oscar (which I've avoided because it is red hat based, with the RPM based packages)  Does this actually work?  If so what are the benefits?  I ask because I'm looking into putting together my own cluster for large finite element problems, and I always thought that Oscar type packages would just ignore kernel level clustering.

Cheers

Tucker

---

### Post by ajt on 2007-11-25
Hello, Tucker.

That's not true! I'm running X11 apps. in gdm without any problems under Ubuntu 6.06.1 LTS with an openMosix kernel (linux-2.4.26-om1). I've posted about this on the forums already (search for mosix).

I'm interested in using the Kerrighed patches to the Linux kernel too, but I've not tried Kerrighed out yet. I'd be interested to hear from ayone who has?

Tony.

> **tutomlin said:**
> Not sure how far you've gotten from this but the stable version of OpenMosix is on the 2.4.26 kernel, and I know that the latest versions of the x server distributed with ubuntu won't work on that kernel. (I know you don't want gui stuff but my point is other stuff may not work well either.)

There is another project called kerrighed which is supposed to do the same stuff, but seems to be much more up to date that the openmosix project.

Also I'm not sure how kernel level cluster solutions like mosix and kerrighed interact with software level packages like Oscar (which I've avoided because it is red hat based, with the RPM based packages)  Does this actually work?  If so what are the benefits?  I ask because I'm looking into putting together my own cluster for large finite element problems, and I always thought that Oscar type packages would just ignore kernel level clustering.

Cheers

Tucker

---

### Post by tutomlin on 2007-11-28
Hmm,

Admittedly I got my "it breaks X" info second hand:
[http://ubuntuforums.org/showthread.php?t=210205&highlight=cluster+mosix](http://ubuntuforums.org/showthread.php?t=210205&highlight=cluster+mosix)
( post #8 )

not sure what the difference is between that setup and yours (other than a year or so of patches between that post and this one) so I can't really say why the poster In the above thread had problems with X.  On the whole I'm glad to hear that it works.

The kerrighed dev's have finally released the SMP support version of their kernel patch, so I was planning on setting up a ubuntu kerrighed cluster soon.  (Sadly my main desktop is down with motherboard issues and all the computers I was going to cluster are currently diskless so I need to resolve some hardware issues prior to proceeding.)

If I get anywhere useful I'll be sure to post.  If not I may follow your example and check out the OpenMosix 2.4 patches under recent versions of Ubuntu 


Tucker

---

