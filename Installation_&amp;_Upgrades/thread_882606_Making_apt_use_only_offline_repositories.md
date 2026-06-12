---
title: "Making apt use only offline repositories"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by TPJ on 2008-08-07
Hello!

I have never used Ubuntu (nor Debian, for that matter).

I'd like to make apt use only my private repository (which I'm going to make an offline mirror of some running official repository...), and I'm trying to find out how can I do it.

I think it's possible as follows:
1) Put my repository on my hard disk, in some place (say, /my/repo).
2) Add the following line to the /etc/apt/sources.list:

deb file:///my/repo SuiteCodename main universe multiverse restricted

3) Download all the *.deb files and put them into proper directories (pool/...) in the /my/repo directory.
4) Download the Release, Release.gpg, and the proper Contents files, and place them in /my/repo/dists directory. Download the proper Packages.bz2, Packages.gz and Release files for all the repositories I want to mirror, and place those files in the proper directories in /my/repo/dists directory.

Will such a solution work as I want it to?

My intention is simple: I want to download all the repositories, and place them on my external hard drive. Then I want to install Ubuntu on my offline-working computer, and configure apt to use the repository from my external hard-drive.

Just as I'm doing it with my Arch machines.

---

### Post by sameerds on 2008-08-07
> **TPJ said:**
> 

I think it's possible as follows:
1) Put my repository on my hard disk, in some place (say, /my/repo).
2) Add the following line to the /etc/apt/sources.list:

deb file:///my/repo SuiteCodename main universe multiverse restricted



I think that sounds correct, do check the syntax in the manpages once.

> **TPJ said:**
> 
3) Download all the *.deb files and put them into proper directories (pool/...) in the /my/repo directory.
4) Download the Release, Release.gpg, and the proper Contents files, and place them in /my/repo/dists directory. Download the proper Packages.bz2, Packages.gz and Release files for all the repositories I want to mirror, and place those files in the proper directories in /my/repo/dists directory.


You don't have to do all this manually. Try tools like [apt-mirror]("http://apt-mirror.sourceforge.net/") instead!

> **TPJ said:**
> 
My intention is simple: I want to download all the repositories, and place them on my external hard drive. Then I want to install Ubuntu on my offline-working computer, and configure apt to use the repository from my external hard-drive.


Is your other machine totally off the net? If it is not, there is another option: you can configure it with normal repositories. But instead of installing anything directly, you can use apt-get or synaptic to generate a list of URLs for the required package. Then use this list to download the deb files on the other machine using wget or some such download tool.

Simply copy these to /var/cache/apt/archives on the first machine and run apt-get or synaptic again. These tools always check this directory to see if a necessary package is already present on disc, before trying to download it, and so the install will proceed without accessing the net.

The only network access required on the first machine is when you need to run apt-get update.

---

### Post by TPJ on 2008-08-07
Wow, a fast answer! Thank you!

[quote="sameerds"]Try tools like apt-mirror instead![/quote]

Thank you!!! :D

[quote="sameerds"]Is your other machine totally off the net? (...)[/quote]

Yes, it is.

Therefore I make mirrors of all the repositories every month, when I update my machines. I have one machine with very fast internet connection, one with a moderate one, and one with no connection at all.

---

