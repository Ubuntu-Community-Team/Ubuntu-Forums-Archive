---
title: "upgrade from 16.04.5 to 18.04.1"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by jgw on 2018-08-14
I just installed 18/04.1 on my laptop from the internet (not a dvd)   My system:
hp laptop
Processor	Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
Memory	3988MB (2440MB used)
Machine Type	Notebook
Operating System	Ubuntu 18.04.1 LTS

I used the directions found at: [https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)
In re-reading this it then had a link to [https://linuxconfig.org/things-to-do-after-installing-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/things-to-do-after-installing-ubuntu-18-04-bionic-beaver-linux)  which had a link to [https://linuxconfig.org/8-best-ubuntu-desktop-environments-18-04-bionic-beaver-linux](https://linuxconfig.org/8-best-ubuntu-desktop-environments-18-04-bionic-beaver-linux)
In that last they had a link to installing the gnome desktop (as well as other iterations of ubuntu 18.04  which I found interesting.

I also did:
greg@greg-laptop:~$ unity --version
unity 7.5.0
greg@greg-laptop:~$ sudo apt purge ubuntu-unity-desktop
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'ubuntu-unity-desktop' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, I have a unity version but no unity

Apparently the update I did left out the supposed gnome desktop from the getgo.  I think I will do all the rest of the stuff and see what happens.

It seems to be working ok but it is also a lot different from the upgrades I did on my other computers.  For instance, the docker.  What I seem to have, in lieu of the gnome docker is a launch bar and it may be the unity docker.  System settings is also much different.  

What I would like to know is what I have done and what I now have as it seems to be much different.  There is also a program called qpdfview and I am wondering what that is.  It says itgs a document viewer but seems to have a lot of capacity for a viewer.

I also googled 'docker'.  The top item was directions to install docker.  I did that and then thought I had best stop right there and get some help before I really screwed things up.  

Thoughts?

---

### Post by Impavidus on 2018-08-15
Things change. Unity has been dropped in favour of gnome shell, which changes the appearance. qpdfview is just one of about a dozen pdf viewers available from the official repositories. Different releases and different flavours install different viewers by default. A fresh install replaces the old default applications by the new defaults, an upgrade just upgrades the old default applications (and may add the new defaults alongside).

---

### Post by jgw on 2018-08-15
Thanks for the reply

I guess I wasn't clear.  I am still running unity on my laptop after my upgrade.  My system settings, for instance, are exactly the same as they were when I was using 16.04.  When I installed and took a look at gnome tweak there was not a line for extensions.  In other words, I upgraded, from the internet, from 16.04.1 to 18.04.1  when it was done I checked and I was told I was now running 18.04  I checked again this morning and got:
greg@greg-laptop:~$ lsb_release -a
LSB Version:	core-9.20170808ubuntu1-noarch:printing-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

My problem, for starters is that the upgrade, from the net, did not remove unity.  The upgrade itself left all my stuff on this laptop but I can always deal with that one.  I am tempted to simply put the live 18.04 dvd into this laptop and reinstall but I would prefer not to do that if at all possible.  I thought it was a little strange that there was a tutorial on how to install the docker for 18.04 which is why I did it and then stopped because, even though the installation went fine I thought it was strange.   I find it really strange.  When I upgraded I checked for a new version and assumed, as it took right off, that it was ready for installation - now I am not too sure.

I have checked a number of things like "what to do after installing 18.04", "x number of things to do after installing 18.04", etc.  All of those assume there was a replacement of unity to gnome.  I don't think that happened when I upgraded (I could be wrong).  So, I guess, my question is what am I supposed to do now?

Thoughts?

---

### Post by jgw on 2018-08-17
I surrender.  I have now re-installed from a dvd and everything is dandy.  Can't really recommend upgrading straight from the internet, strange things happen (probably missed something)
will mark this one as solved

---

