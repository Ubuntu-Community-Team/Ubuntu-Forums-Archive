---
title: "[SOLVED] KDM fails to load"
date: 2008-06-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-06-25
I'm looking to Kubuntu users to see if this is unique to me or is kdm broken? I have been using gdm for a month or so, so I thought I would try again. If I use kdm or kdm-kde4 X fails to load:( but gdm starts ok? What I would like to know should I be looking further or is this a bug to be listed:confused:


Cary

---

### Post by meborc on 2008-06-25
is your system upgraded from hardy or are you using alpha/daily image fresh install?

---

### Post by caryb on 2008-06-25
dist-upgrade from hardy on day 1 of intrepid repo's being open!


BTW it worked for a while but died 4 weeks ago!


Cary

---

### Post by meborc on 2008-06-25
i would keep a virtualbox image of the latest greatest daily install to compare if there are any differences... dist-upgrading may lead to breakage that is not fixed by next upgrades

---

### Post by ronacc on 2008-06-25
where do I find the daily's ? all I see in the cd testing dir for intrepid are the md5sums.

---

### Post by caryb on 2008-06-25
I just found gdmsetup command, now I have Blue background & a blue Debian logon screen similar to KDM. Now I don't have that revolting orange/brown chunda:lolflag:


Cary

---

### Post by plun on 2008-06-25
> **ronacc said:**
> where do I find the daily's ? all I see in the cd testing dir for intrepid are the md5sums.

fwiw again....:)

I just followed this from Kubuntu

[http://kubuntu.org/announcements/kde-4.1beta2.php](http://kubuntu.org/announcements/kde-4.1beta2.php)

Changed hardy > intrepid


```
sudo apt-get update && sudo apt-get dist-upgrade

sudo aptitude install kubuntu-kde4-desktop

```


Aptitude will give you a few broken issues but for me it was OK.
(fully updated Intrepid with todays updates)


Really beautiful GUI.... :KS

---

### Post by nowshining on 2008-06-25
u could of also - kmenu - system - login window

---

### Post by ronacc on 2008-06-25
I'm already there as far as the hardy>intrepid goes , did that as soon as the repos opened :) I was asking about full daily images . I keep seeing them refered to and thougt mabye there was testing dir somewhere other than the daily live cd dir .

---

### Post by nowshining on 2008-06-25
the alpaha ubuntu versions will get updates fairly everyday or so, compared to the stable versions. just apt-get update - apt-get upgrade or so, etc.. to get the latest updates.

---

### Post by plun on 2008-06-25
> **ronacc said:**
> I'm already there as far as the hardy>intrepid goes , did that as soon as the repos opened :) I was asking about full daily images . I keep seeing them refered to and thougt mabye there was testing dir somewhere other than the daily live cd dir .

All daily images are broken as I knows but yesterday there was
several meta package updates. 

Example
[https://lists.ubuntu.com/archives/intrepid-changes/2008-June/002486.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-June/002486.html)

But I have not seen it for KDE4.


Nevertheless its easy then to just add packages that you wants

[http://packages.ubuntu.com/intrepid/kubuntu-kde4-desktop](http://packages.ubuntu.com/intrepid/kubuntu-kde4-desktop)

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=kde4](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=kde4)


Well, I am impressed....:)

---

### Post by caryb on 2008-06-26
Post Morten I can boot from GDM:( KDM totally fails:( KDM-KDE4 boots but comes to a dialog box with message missing wiget! I believe that kdm replaces kdm-kde4 as both are at the same version but as you see I must have something wrong with my config. I have installed all the updates & did the dist-upgrade (said the 3 hail Mary's) & accepted the file removals & still works just not the KDM:confused:


Cary

---

### Post by plun on 2008-06-26
> **caryb said:**
> Post Morten I can boot from GDM:( KDM totally fails:( KDM-KDE4 boots but comes to a dialog box with message missing wiget! I believe that kdm replaces kdm-kde4 as both are at the same version but as you see I must have something wrong with my config. I have installed all the updates & did the dist-upgrade (said the 3 hail Mary's) & accepted the file removals & still works just not the KDM:confused:


Cary

Well, it works just fine for me except kde4 systemsettings.

I am using gdm as GUI for login (have not checked kdm)

You can set it with:

```
sudo dpkg-reconfigure gdm
```

Several packages are being built or in que as also kubuntu.org writes.

---

### Post by scokar on 2008-06-28
a fresh install of kubuntu intrepid alpha 1 lets me into a kde4 session, i'm currently using it now.

---

### Post by caryb on 2008-06-28
:guitar: As the title says solved & did this from my other kde4 post as suggested by scokar apt-get install --reinstall kubuntu-desktop 


Thanks scokar:)

Cary

---

