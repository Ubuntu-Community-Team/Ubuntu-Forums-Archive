---
title: "network repository using apt-build for different cpu's possible?"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by snek on 2007-12-01
I have done some reading on apt-build and setting up repositories but I haven't really come across a way to setup a repo for different types of cpu's. I have multiple linux machines at home and one of these is a dead-slow p3 500mhz laptop.

Now, I have gotten xubuntu on it and want to build new deb files for it's architecture, but using my sempron64 3400+ running amd64 ubuntu to build, I think you can imagine why ;)

I have configured apt-build to optimize for pentium3 on O3..
Repository is setup to be written to /var/www/packages

So far it seems to build some packages for all architectures and some only for amd64.. There is also no i386 binary folder..

I hope someone can help me with this.. I'd rather have my server compile it in a few hours than having to leave my laptop on for a month ;)

If this is even possible, might there be a way to compile on a windows machine using cygwin or something? Got a core2duo for gaming, would be even nicer to compile using that..

---

