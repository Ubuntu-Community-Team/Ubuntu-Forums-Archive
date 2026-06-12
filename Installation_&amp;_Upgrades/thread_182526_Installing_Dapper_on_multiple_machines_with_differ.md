---
title: "Installing Dapper on multiple machines with different hw"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by spmsrh on 2006-05-26
Hi,
I work in Bangalore, India, where I have a very good internet connection, I have been Ubuntu Dapper since the last few months and I really like it as far as newbies are concerned. However, I need to install Dapper in my hometown of Jaipur.

To be frank, I have very little idea about apt-get, because I have been primarily a gentoo user for the last 3 years and started using dapper as secondary about 2 months before. 

But without network and with so many machines, I can't install gentoo at jaipur. And with so many machines and most people using it absolute newbies (some kids and my old parents). I have to use a binary based distribution. Plus, I have to install it on many different machines at my home and my old school. 

I do not have internet at all on most machines and a pathetic slow internet (about 14.4kbps, yes that old) on one or two of them. Some do have DVD-ROM drives and and I have LAN cables.

I want to install mp3 support, multimedia codecs, KDE education programs and some other softwares which I need at home.

Obviously ubuntu does not support any of these out of the box. India has no legal issues with mp3 support, software patent or DMCA (thankfully). 

1. Is there some way for me to remaster Ubuntu, Edubuntu etc. CDs so that I can select a particular set of software configuration and burn a common DVD iso with those packages so Ubuntu can be used out of the box?

2. I thought about using images, but the diversity of configuration is too much (one is an old P300 64MB to all the way for a P4 with ATI card having 128MB graphics). So some amount of hardware detection and configuration should be automatic. I  can easily change KDE to XFCE for the lower end machines. But I can't sit and configure alsa on each machine.

3. Or, if I can't remaster Ubuntu CDs, is it possible for me to burn CDs to use as a repository with software? 

I have to burn whatever software I can in Bangalore and then install it in back in Jaipur. Even if I must burn a DVD iso or 10 CDs isos, I have no problems. 

If anyone can suggest a good solution, I would be very grateful.

Thanking you
Regards
SP

---

### Post by tkjacobsen on 2006-05-26
You can dowload the entire ubuntu repository and burn it to 3 dvds:
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

If you want the same packages to be installed on all the computers, you can install them on one using synaptic / adept. Then copy the contents fo /var/cache/apt/archives to a cd. Then on every computer go to the directory on the cd with the packages and  ```
  sudo dpkg -i *.deb 
```  then you'll install all the packages

---

### Post by spmsrh on 2006-05-26
Thanks a lot Troels. I will try both solutions. 

That is a Breezy Repository, but I guess I can install a local deb mirror here and do something.

Spacewise, I think the /var method is better.

P.S.
Ignore below:

Search Keywords: OEM, custom install, remaster, no network install, local repository

---

### Post by tkjacobsen on 2006-05-26
you can setup your own repository using this howto:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

just make sure only to use packages from the ubuntu repos.. (to get the most stable system). 


For better multimedia support maybe use som packages from seveas and chiperfunk unofficial repos

Entries to put in /etc/apt/sources.list
# Seveas extra repo
deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) dapper-seveas custom extras freenx java seveas-meta all

# Cipherfunk multimedia packages
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

---

