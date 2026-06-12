---
title: "switching betw multiple gcc version"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by spamalot on 2010-03-24
Hello,

I need to test my code under different versions of GCC. At leat GCC 3.4 in addition to the default. I was hoping I could simply do the switch from CodeBlocks's build settings... Of course, it's not that simple. Would anyone kindly suggest a good place to start for this need?

By the way, GCC 3.4 is not even in synaptic manager. I suppose some apt-get install command can do it. 

Please note : ideally I'd like to be able to switch between versions. I've heard of ccontrol, but I'm cautiously posting here before for any advice before blowing up my set up.

---

### Post by srs5694 on 2010-03-24
In Gentoo, there's a tool called gcc-config that does what you want (well, aside from IDE integration; I'm not sure about that). I don't see it on my Ubuntu system, though. There's a chance you could download the Gentoo package information and get it to build on Ubuntu; [here's the Gentoo package reference.](http://gentoo-portage.com/sys-devel/gcc-config) OTOH, it's possible that it's a Gentoo-specific tool that relies on Gentoo-specific features, so it may not be very easy to graft onto Ubuntu. You might also try a Web search on "gcc-config Ubuntu". When I did this, I didn't see anything obviously useful in the first few hits, but I didn't look at that many of the hits, so maybe there's gold somewhere in there.

Another option, albeit an ugly one, would be to install an older distribution that uses GCC 3.4 in a virtual machine or another physical computer and use that for testing the older compiler. Once installed and booted it probably wouldn't be that painful; you could run the virtualized system without X or most other memory-hungry applications and just SSH into it or use its virtualized console directly, with NFS to share your development directories.

---

### Post by spamalot on 2010-03-26
So is this 

[INDENT][/INDENT]export CC=/usr/bin/gcc-3.4 

all it takes? What all the hoopla about gentoo and ccontrol then?

Meanwhile, I'm stuck with this:

[INDENT][/INDENT]sudo apt-get install gcc-3.4
[INDENT][/INDENT]Reading package lists... Done
[INDENT][/INDENT]Building dependency tree       
[INDENT][/INDENT]Reading state information... Done
[INDENT][/INDENT]E: Couldn't find package gcc-3.4

---

