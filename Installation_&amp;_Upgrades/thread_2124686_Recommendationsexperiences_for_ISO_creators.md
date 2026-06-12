---
title: "Recommendations/experiences for ISO creators"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by zembelaa on 2013-03-11
Hi,

We are thinking for our software office to use Ubuntu 12.04 32 bit which has long term support. We have more than 15 machines. First we want to make a new ISO which will include the updates and some extra packages.

The ISO should be stable. If it can not be done, please tell it.

Which application do you recommend for making this ISO?

-Remastersys project has stopped about 3 months ago.. Now it started again, but it does not update itself and the support is too bad.

-Re-linux didn't published any stable version yet.

-UCK's latest stable version gives me "dependency is not satisfiable libfribidi-bin" on Ubuntu 12.04. I don't think that is normal. UCK is already designed just for Ubuntu. It is possible to install 2.4.5 version of UCK properly, but it is published on 2011-11-30 which is before release of Ubuntu 12.04. I think they are kidding..

I could not find time to try these:

-Ubuntu builder seems nice app.

-reconstructor is cloud based. I want to make my own iso on my local machines. Also they are getting money for that.

Can you please tell me your experiences about all these applications? They are (or which are) stable do you think?

Thanks in advance...

---

### Post by zembelaa on 2013-03-14
Nobody can help me please :(

---

### Post by Stray Wolf on 2013-04-27
Wish I could help. Lately I've spent a lot more time trying to get Ubuntu apps installed and running correctly than actually using the apps once I get them working. Sad part is, these are mostly apps from Ubuntu's own software center. I tried UCK from the software center. It installed so that was good. But once I tried to use it I kept getting "Failed to copy resolv.conf, error=1". Then, I tried adding the stable ppa. Even though it showed up in software sources it never showed up in the software center (only showed 2.4.5) and installing from the terminal gave me the 2.4.5 as well.  I also tried the newer version from SourceForge (2.4.7) but of course: "dependency is not satisfiable libfribidi-bin". Needless to say - I'm getting frustrated. Hopefully someone knows something. Bump!

---

### Post by MAFoElffen on 2013-04-27
I tried Remastersys a few years ago and was satisfied in what it did, but found my needs exceeded those. This was good at taking a snapshot of a system as a LiveCD, but included "Remastersys" as part of the snapshot of that system. It was a good graphical utility for someone just starting out...

I currently still follow the tips of the wiki on creating my own custom LiveCD's. There I uncompressed the LiveCD and it's contents, mount the live image's filesystem to make whatever changes I want... then compress it back into a LiveCD ISO image. This can include adding updates... changing backgrounds of the login and desktop to a custom (company) logo, custom scripting (for local security policies),  custom applications suites, updating or changing the kernel, etc.

I found I needed more control over what I am doing by doing it that way, without adding fluff that doesn't need to be there. I found for my needs, I needed to include special hardware drivers that weren't included as a default. I also created custom installs for other people that had custom hardware, but were technically challenged to get around that on their own...

I know this next suggestion is not going to make things easier in your decision... but some of these can also be dealt with in a custom install pre-seeding file.

---

