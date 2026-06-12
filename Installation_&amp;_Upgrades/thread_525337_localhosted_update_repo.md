---
title: "localhosted update repo"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by Alkaif on 2007-08-14
hi there,

i dont know whether if this has been answered before or not, or whether a tutorial already exists, believe me, i have googled high and low for some information on this, but the only information i got was from ubuntuguide.org where they tell you how to set up the repo.

Basically, to give an overview, i have 5 computers at home, all running ubuntu (woop :))... and updating all 5 can be an annoying and tedious task. In New Zealand, our ISP's like to rate-limit our bandwith meaning we can not download as fast as we can during off-peak times.

I've created a repo using the methods described at ubuntuguide.org.

I've also added the local repo to the sources.list file but for some reason, all updates still come through the ubuntu servers.

How can i make the computers locally to download everything from the locally hosted repo? This would greatly increase the speed at which the updates are applied (otherwise i'd have to spend a whole day with updates).

any help with this is greatly appreciated.

Thanks for looking at this thread even if you can not help me :).

Cheers,
Alkaif.

---

### Post by Seisen on 2007-08-14
If its added to your source list comment out the other lines, (put one of these[SIZE="4"] ** '#"**[/SIZE] in front of the other lines and then reload your source list.

---

### Post by irw on 2007-08-14
To get round this problem, I have just pulled out the conection to the internet.

Then, the local rep is found, so that is the one used; once running, I can plug back in and go back online

---

### Post by Alkaif on 2007-08-14
well i've tried that, but for some reason, it still does not pull it from there.. can you please tell me the steps u do to get ur repo to update through local network?

---

### Post by Alkaif on 2007-08-20
hey there.. .so i was wondering, has anyone been able to get a local repo working? cuz i still having issues with it :'(

---

### Post by Seisen on 2007-08-20
Post your source list and bold your local repository that you are trying to use.

---

### Post by Alkaif on 2007-08-21
its the standard repo listing when a fresh copy of ubuntu is installed with this line added to it that refers to the one created by following the repo guide posted in [www.ubuntuguide.org](www.ubuntuguide.org).

my line that refers to my home server is:
> 
deb [http://192.168.1.2/apt](http://192.168.1.2/apt) binary/


if you would like a web url to the repo, then this is it: **[http://alkaif.gotdns.com/apt/](http://alkaif.gotdns.com/apt/)**
the binary directory has a mirror copy of all the files in /var/cache/apt/

some packages are updated through the home ones, while everything else such as security ones are downloaded from nz.security.ubuntu.com or something (sorry, not at home at the moment).

any help would be appreciated.

OH and if this helps, everytime i add more packages to the repo (at home) i update the Packages.gz file.

---

### Post by Alkaif on 2007-08-23
hmm so anyone have a solution? seems like i have to bump this thread to get some attention :(

---

