---
title: "Basic help regarding package errors (unresolvable packages - libxine1)"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by torqued on 2009-11-24
Hi there.

I've got a question related to the packages "libxine1" and "libxine1-x".

I am trying to install these packages on my fresh install of Ubuntu 9.04, but I am unable to do so.

When I try to mark libxine1 for installation the error I get is:

> The following packages have unresolvable dependencies.

libxine1:
Depends: libxine1-misc-plugins but it is not going to be installed or
libxine1-plugins but it is not going to be installed
Depends: libxine1-x but it is not going to be installed
Depends: libxine1-console but it is not going to be installedWhen I try to mark libxine1-x for installation the error I get is:

> The following packages have unresolvable dependencies.

libxine1-x:
Depends: libdirectfb-1.2-0 but it is not installable--

The repositories I have added are:

> deb [http://apt.boxee.tv]("http://apt.boxee.tv/") jaunty main
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main

--

I am following a guide at: [http://lifehacker.com/5406563/build-a-cheap-but-powerful-boxee-media-center#commentform](http://lifehacker.com/5406563/build-a-cheap-but-powerful-boxee-media-center#commentform)

--

Hope someone is able to help me out :)

---

### Post by torqued on 2009-11-25
What's the source of these unresolved dependencies / broken packages anyway?

Is there a way to fix it? I wasn't even able to install mplayer because libfaac was an unresolved dependency. This is coming from a fresh install of Ubuntu Jaunty.

Is there a chance the repository is screwed, or am I the one who's screwed :)

---

### Post by henwyn on 2009-11-25
Sometimes this can be caused by one package being upgraded before the upgrades of the packages that it depends on making it into the repository. If that is the case, waiting a few hours to a day will usually resolve the issue. What you might try though is checking out the  Comprehensive Multimedia & Video Howto under Mutimedia & Video. That will give you detailed directions on adding necessary repositories and packages that should clear this right up. HTH

---

### Post by torqued on 2009-11-25
Thanks for the tip! :)

Unfortunately I never got it working, so I switched over to Linux Mint and got libxine1 and libxine1-x installed without hiccups.

---

