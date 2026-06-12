---
title: "COMPAQ NC6000 installation issues"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by deftone_75 on 2012-09-20
Hello all. I have Ubuntu 12.04 installed on my Dell D610 laptop and it works better than new. I just purchased an HP Compaq NC6000 from the local pawn shop. It currently has Windows XP on it. When I tried to install Ubuntu 12.04.1, I get the following screen......

This kernel requires the following features not present on your CPU

pae

Unable to boot - please use a kernel appropriate for your CPU



What do I do now? Will 12.04 not work on this model? Its a 2004 model with Pentium M processer, 1 Gb ram, 80 GB hard drive, and dvd rom. I am totally frustrated. Im not real savvy with Linux at all. My Dell just works. I need help here in the worst way! Thank you all in adavance.

---

### Post by jrog on 2012-09-20
> **deftone_75 said:**
> Hello all. I have Ubuntu 12.04 installed on my Dell D610 laptop and it works better than new. I just purchased an HP Compaq NC6000 from the local pawn shop. It currently has Windows XP on it. When I tried to install Ubuntu 12.04.1, I get the following screen......

This kernel requires the following features not present on your CPU

pae

Unable to boot - please use a kernel appropriate for your CPU



What do I do now? Will 12.04 not work on this model? Its a 2004 model with Pentium M processer, 1 Gb ram, 80 GB hard drive, and dvd rom. I am totally frustrated. Im not real savvy with Linux at all. My Dell just works. I need help here in the worst way! Thank you all in adavance.
See here for your various options: [http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

The official Ubuntu 12.04 unfortunately requires PAE-capable CPUs. The easiest, but least "official," option may involve the fact that someone at Canonical has made an unofficial version of 12.04 that doesn't have this requirement, available here: [http://people.canonical.com/~diwic/12.04-nonpae/](http://people.canonical.com/~diwic/12.04-nonpae/). Do check out your other options, though.

---

