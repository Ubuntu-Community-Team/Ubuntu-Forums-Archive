---
title: "Installing SSSD from http://launchpad.net"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by mistofeles on 2011-10-05
The sssd packet in 11.04 seems to be buggy and doesn't work, so I Googled and found that there is a new version in [https://launchpad.net/ubuntu/+source/sssd/1.5.13-0ubuntu1/+build/2815453](https://launchpad.net/ubuntu/+source/sssd/1.5.13-0ubuntu1/+build/2815453)
Now I do not know how to continue. 
When I try to install this packet, I get a lot of missing dependencies. There seems to be a tree of those: installing one with 'dpkg -i packet' asks me to install a bunch of others etc. 

Is there a simple command or parameter, which takes care of all these latest dependencies ?

I have had this problem before with other packages and found no way around ](*,)

I have a VMWare workstation installation to test this before I go to production machines. So, testing doesn't waste anything but time.

---

### Post by dino99 on 2011-10-05
looking at this link:

Built files

Files resulting from this build:

    libnss-sss_1.5.13-0ubuntu1_i386.deb (16.9 KiB)
    libpam-sss_1.5.13-0ubuntu1_i386.deb (20.0 KiB)
    python-sss_1.5.13-0ubuntu1_i386.deb (143.8 KiB)
    sssd_1.5.13-0ubuntu1_i386.deb (1.6 MiB)

so you can see that you need these 4 packages running in 32 bits version only.
Download them into an empty folder, then cd to that folder and run:

sudo dpkg -i *.deb

note: these packages are from oneiric repo, which will be released in a few days now (so that dont mean they will work on natty)

---

### Post by mistofeles on 2011-10-05
> **dino99 said:**
> looking at this link:
so you can see that you need these 4 packages running in 32 bits version only.
Download them into an empty folder, then cd to that folder and run:

sudo dpkg -i *.deb

note: these packages are from oneiric repo, which will be released in a few days now (so that dont mean they will work on natty)

Thank you, you found what I was meaning :)
If there is a new repo release coming, I might wait as well and not try it by force.

---

### Post by mistofeles on 2011-10-17
> **mistofeles said:**
> 
If there is a new repo release coming, I might wait as well and not try it by force.

I Installed Ubuntu 11.04 and apt-get install sssd there.
Now I'm looking for some simple information how to make it work. So far I have found but man pages.

This SSSD would be great if only there is some simple way ton configure it.

Is there some page describing the configuration process for a absolute beginning beginner ?

---

