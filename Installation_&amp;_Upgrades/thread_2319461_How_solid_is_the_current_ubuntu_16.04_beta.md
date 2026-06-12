---
title: "How solid is the current ubuntu 16.04 beta"
date: 2016-04-04
forum: Installation &amp; Upgrades
---

### Post by alex351 on 2016-04-04
Hi guys,

usually I don't install developer versions - however I am still on 14.04 LTS and planning on upgrading to 16.04 soon. I want to do a clean install (ubuntu server) but won't have the time to properly set everything up in the months after the official release date of 16.04.
Therefore, I though about setting up the new system now with the current beta (which should be upgraded to the final version by the of the month - right?).
Hence my question: is the current beta already solid enough for a home server environment with file, print and web server applications? I could live with a few kinks but not if there a still major bugs to be squashed. I also need LXC (or LXD) to be working...

Thanks in advance for you opinions :-)

---

### Post by grahammechanical on 2016-04-04
I cannot comment on Ubuntu xenial xerus server edition as I have never installed it but I consider the 16.04 development branch of Ubuntu desktop to be stable and to have been stable since its development period first started. I have been using xenial xerus every day since the beginning. 

Others have asked these same questions and have been answered. There are always bugs in every software project. Reporting & fixing bugs is part of the on-going software development process. 

As for LXD/LXC, it is being developed on xenial xerus. And unlike 15.10 we do not need to install a PPA before installing LXD. It has also been backported to 14.04.

[https://www.stgraber.org/2016/03/15/lxd-2-0-installing-and-configuring-lxd-212/](https://www.stgraber.org/2016/03/15/lxd-2-0-installing-and-configuring-lxd-212/)

My advice is to set up a testing install of xenial xerus & LXD before upgrading a production machine. Make your decision based on your own testing of the OS. No one else can or should make promises about things like this.

Regards.

---

### Post by RobGoss on 2016-04-05
Hello and welcome, I have to agree Ubuntu 16.04 has been working great on my desktop even tho it's a beta release. I haven't had any major problems and it differently worth a try. I would have to say yes it's pretty solid...

---

### Post by buzzingrobot on 2016-04-05
16.04 is an evolutionary, not  a revolutionary, update. I've been running it as a desktop without any significant crash-and-burn problems.

If it was me and if I knew I was going to be pulling packages *only *from Ubuntu repos, I'd be inclined to commit to the server version now.   After all, you would be eliminating a desktop suite as a source of problems.

However, if I was going to need packages from a PPA or another third-party source, I'd want to verify that those packages had been, and would continue to be, tested on 16.04 until after its release. If not, I'd wait until the release of packages built on and tested against the release version of Xenial.

---

### Post by mastablasta on 2016-04-06
why not upgrade next year? 14.04 is still supported for a while...

---

### Post by kansasnoob on 2016-04-07
> **mastablasta said:**
> why not upgrade next year? 14.04 is still supported for a while...

+1! Ubuntu server Trusty is supported until April 2019.

---

### Post by alex351 on 2016-04-07
...because I would like to move to the 4.4 kernel as some major issues for my Seagate 8TB Archive drive have been fixed in recent kernels...

I already upgraded and am continuing to run the LXC containers with their 14.04.4 templates until all the PPAs etc. become available. Works well so far

---

### Post by QLee on 2016-04-07
> **alex351 said:**
> ...because I would like to move to the 4.4 kernel as some major issues for my Seagate 8TB Archive drive have been fixed in recent kernels...

You can use a 4.4 kernel with 14.04, it's available in trusty-updates main repository.

I agree with the advice above to set up a test situation and not test with your production machine.  Never test with something you need to "work".

---

### Post by alex351 on 2016-04-07
...I made a clonezilla copy of my boot drive in case things go south - but so far I am apparently lucky :-)

---

