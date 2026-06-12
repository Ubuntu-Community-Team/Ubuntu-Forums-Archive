---
title: "apt pinning to a ppa"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by doctordruidphd on 2011-09-16
What I want to accomplish is ensure that I NEVER get firefox betas, only stable releases.

The way to do that is to install the firefox stable ppa, and then pin firefox to that repository. PPAs are normally assigned a higher priority than normal repositories, so that's usually automatic. But I am running oneiric, and the ppa is not currently active. I will not use the betas, I would rather take the risks of installing versions built for natty (or at least trying it) than mess with the beta garbage. What I am doing now is using the downloaded version of firefox from the mozilla website, but that's 32-bit on a 64-bit system, which gets ugly with flash.

I could in theory do this by pinning firefox to the ppa in /etc/apt/preferences.d . But in order to do that, I need to know what the "release name" for the ppa is. Here is such a pinning file:

Package: firefox firefox-globalmenu firefox-gnome-support
Pin: release a=natty-updates
Pin-Priority: 600

This is what pins firefox to the natty-updates repository in natty. The "a=" part determines the repository used. What I can't figure out is what to put in the "a=" part for the stable ppa:

deb h-t-t-p://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu natty main

(I put the dashes in to keep the forum from messing up the display)

Yeah, we're getting beyond plug-and-play here, but it's an experiment, not a production system.

Thanks for any info on how to use pinning with a ppa.

---

