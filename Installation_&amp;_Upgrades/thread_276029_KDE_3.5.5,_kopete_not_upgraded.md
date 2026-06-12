---
title: "KDE 3.5.5, kopete not upgraded"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by larpon on 2006-10-12
Hey there...

I've just upgraded to KDE 3.5.5 and according to: [KDE.News]("http://dot.kde.org/1160580750/") there should be a new version of kopete bundled..
But during the upgrade and if I look at the available packages for kopete... There's no upgrade for kopete.. I'm still at
Kopete version 0.11.1?

Anything I've missed? And how do I get the newest kopete injected? :)

--edit--
The version of kopete should be 0.12.3 in KDE 3.5.5
and that's the version I'm looking for..

---

### Post by larpon on 2006-10-12
I got to think.. Are kopete in a seperate package mirror from the rest of KDE?

---

### Post by skymt on 2006-10-12
Are you using Edgy or Dapper? I have Kopete at 0.12.3 in Edgy.

---

### Post by larpon on 2006-10-12
I'm on Dapper

---

### Post by TheWizzard on 2006-10-12
> **larpon said:**
> Hey there...

I've just upgraded to KDE 3.5.5 and according to: [KDE.News]("http://dot.kde.org/1160580750/") there should be a new version of kopete bundled..
But during the upgrade and if I look at the available packages for kopete... There's no upgrade for kopete.. I'm still at
Kopete version 0.11.1?

Anything I've missed? And how do I get the newest kopete injected? :)

--edit--
The version of kopete should be 0.12.3 in KDE 3.5.5
and that's the version I'm looking for..

am i correct that you did a manual upgrade of kde? why? and why do you use ubuntu dapper? 

let me explain: 
when a new version of a programm is released, the ubuntu team compiles the package and puts it on a repo. in order to ensure the new package is perfectly integrated with your other packages they test it, so the release on ubuntu is somewhat later than the official release. 
manually upgrading is not something i would advice to ubuntu (dapper) users. if you want to have the latest stuff, install a bleeding-edge distro. or edgy of course (what's in a name). 
if you want a stable box, let dapper do it's work and you'll be only a few weeks behind in having the latest packages. 

btw if you keep your box up-to-date on the normal way, you already have kopete 0.12 in dapper

---

### Post by human_blip on 2006-10-13
> **TheWizzard said:**
> am i correct that you did a manual upgrade of kde? why? and why do you use ubuntu dapper? 


No - if he did a manual upgrade - I assume you mean not using kubuntu packages - he would not be asking the question he is asking. The fact is - at least as I write this - there is no kopete 3.5.5 in dapper updates, dapper backports, or Jonathon's [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main. It is there for edgy but not for dapper.

---

### Post by TheWizzard on 2006-10-13
> **human_blip said:**
> No - if he did a manual upgrade - I assume you mean not using kubuntu packages - he would not be asking the question he is asking. The fact is - at least as I write this - there is no kopete 3.5.5 in dapper updates, dapper backports, or Jonathon's [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main. It is there for edgy but not for dapper.

there is kopete 0.12.2 in dapper. i'm using it and i use nothing but what's in the standard repo's (exception: freemind). of course you'll have to activate universe, etc. 
cheers

---

### Post by human_blip on 2006-10-13
> **TheWizzard said:**
> there is kopete 0.12.2 in dapper. i'm using it and i use nothing but what's in the standard repo's (exception: freemind). of course you'll have to activate universe, etc. 
cheers

yes but kdenetwork in Jonathon's kde-355 dapper main repo requires kopete >= 4:3.5.5-0ubuntu1-dapper1 and it is not available in that repo or in the others I mentioned or in universe.

rats - make that kopete >= 4:3.5.5-0ubuntu1~dapper1

---

### Post by l.capriotti on 2006-10-15
Any updates on this? I'm on Dapper too, and it seems I am prevented to upgrade to 3.5.5 (via apt-get upgrade) due to kubuntu-desktop needing an updated kopete that is not available in any official repos.

TIA
Luigi

---

### Post by Cadeucean on 2006-10-17
I updated to KDE 3.5.5 when I saw [this announcement]("http://kubuntu.org/announcements/kde-355.php") in the kubuntu RSS feed. 

My kopete was updated to 0.12.3 but now it won't connect for me here at work. The old version connected fine as long as I overrode the default yahoo IM connection settings to port 20.

---

### Post by TheWizzard on 2006-10-17
> **l.capriotti said:**
> Any updates on this? I'm on Dapper too, and it seems I am prevented to upgrade to 3.5.5 (via apt-get upgrade) due to kubuntu-desktop needing an updated kopete that is not available in any official repos.

kde 3.5.5 is not in the official repo's as far as i can see (though i'm using a european repo [http://au.archive.ubuntu.com)](http://au.archive.ubuntu.com)). 
do you have additional repo's installed? 
be carefull with this. not all repo's are compatible with each other and may break your system. can you post ```
cat /etc/apt/sources.list
```   

actually, the need for unofficial repo's for kde in fedora was my reason to migrate to kubuntu. 

if you want to keep your system stable, it is wise to wait for new versions of software to appear in the official repo's.

---

### Post by larpon on 2006-10-17
Well... If the KDE Team are putting KDE 3.5.5 out as stable...
It's stable enough for me :) and if I wanted to run bleeding edge I'd run Gentoo as I've done for 5 - 6 years..

Anyway I appreciate your concern but I think KDE 3.5.5 is stable enough for me... trust me if I was on Gentoo, I'd probably be compiling it out of svn (still.. damn it took some time) ;)

Anyway I'll keep watching.. Seems my repository just don't have the newest kopete.. yet :)

Thanx for all of your replies so far gents...

---

### Post by TheWizzard on 2006-10-18
> Well... If the KDE Team are putting KDE 3.5.5 out as stable...
It's stable enough for me 
the stability of kde 3.5.5 is not my concern. my concern is breaking dependencies. i have had some bad experience with unofficial repo's on fedora.
good luck

---

