---
title: "Kubuntu to Edgy upgrade issues (using a CD iso file) - please help me!"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Bigglez on 2006-10-28
I currently have : Kubuntu 6.06 
I downloaded the *kubuntu-6.10-desktop-i386.iso* file because I want to upgrade to it.

**First Attempt:**
I have read the instructions at 
[http://kubuntu.org/announcements/6.10-release.php]("http://kubuntu.org/announcements/6.10-release.php")
 but I don't want to burn the CD. I will if I don't get anywhere, but I want to see if I can do an upgrade without 'wasting' a CD.

I mounted the iso like so:
```
sudo -i
mkdir /kubucd
mount -o loop ~/kubuntu-6.10-desktop-i386.iso /kubucd
```

I go into that folder and do an 'ls'. There I find a script called 'cdromupgrade'. I read it's contents and they say use sudo and a full path, so:
```
sudo "sh /kubucd/cdromupgrade"
```

It gives me this error:
**can't find DistUpgradeViewGtk**

Full stop so far..

**Second Attempt:**
A vain attempt at following *buntu instructions, which don't make any explicit mention about Kubuntu, but they don't exclude it either ...
see : [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")
So, I tried:
```
kdesu "update-manager -c"
```
But there is no such program on Kubuntu.


Right, that's my story. Please help!

---

### Post by Bigglez on 2006-10-29
Awwwwww. Bump.

---

### Post by Bigglez on 2006-10-30
No one? Not one Kubuntu user reads this list?

---

### Post by Orion2000za on 2006-10-30
If I understand it correctly you can not use the Desktop CD for CD-install but need the "alternate" CD.
the Desktop (live) CD does not contain the "deb"packages as such.

Sinclair

---

### Post by Bigglez on 2006-10-30
Whoa - you just totally confused me! What does the desktop-live-cd have on it then? I mean, I installed Kubuntu 6.06 from one of them.

Thanks for the response, I was getting blue. At least I have a small lead, I'll go look into this alternate CD thing.

---

### Post by ashrack on 2006-10-30
> 
**Second Attempt:**
A vain attempt at following *buntu instructions, which don't make any explicit mention about Kubuntu, but they don't exclude it either ...
see : [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")
So, I tried:
```
kdesu "update-manager -c"
```
But there is no such program on Kubuntu.

The way I see it U have 2 choices:
1. why don't U just change all DAPPER to EDGY in /etc/apt/sources.list
and then do ```
sudo apt-get dist-upgrade
```
2.Im not usre about this method since it involves installing a GTK+ package, but I believe it should work.
 ```
apt-get install update-manager
```
and from then on U could do:
```
kdesu "update-manager -c"
```

---

### Post by Bigglez on 2006-10-30
> **ashrack said:**
> 1. why don't U just change all DAPPER to EDGY in /etc/apt/sources.list
and then do ```
sudo apt-get dist-upgrade
```
For some reason I assume this will do an online update? I have already spent almost 30 hours just downloading the .iso ... My Internet is not very reliable and it's damn slow.

> 2.Im not usre about this method since it involves installing a GTK+ package, but I believe it should work.
 ```
apt-get install update-manager
```
and from then on U could do:
```
kdesu "update-manager -c"
```[/quote]
Good thinking.
This did flit across my (mostly empty) mind, but I am worried what other stuff is also missing ...

If Kubuntu does not use/have 'update-manager' then why are they so vague on the official upgrade page I linked to in the OP? They should say "*buntu means Ubuntu, H.A.N.D"

Okay, thanks for the input!

---

### Post by ashrack on 2006-10-30
well on my KUBUNTU install I use UPDATE-MANAGER and also SYNAPTIC without problems! Since the KPACKAGE, ADEPT that KDE has, offers very little options. Which is kinda ironic since the main reason I moved to KDE from GNOME was because KDE offers a lot more options to the user.

---

### Post by Bigglez on 2006-10-30
Okay, no worries. I hear ya.

I am leaning towards just staying on Dapper for the time being.
I don't want to format and reinstall and I don't want a b0rked system, so I'm gonna just stick my fingers in my ears and chant the nah-nah-nah, and pretend that there is no Edgy :D

---

### Post by msandersen on 2006-10-30
> **Orion2000za said:**
> If I understand it correctly you can not use the Desktop CD for CD-install but need the "alternate" CD.
the Desktop (live) CD does not contain the "deb"packages as such.
That is right, you need the Alternate CD to upgrade from. I don't know about mounting ISOs except I have a Nautilus script for that.
Of course, by now you could have burnt a CD and done the upgrade. I should imagine using a mounted ISO is faster, but if you have fast broadband, since you need the other CD anyway, maybe simply using apt-get over the internet is just as fast. I found having someone download the Alternate CD for me, the installer script on the CD still needed to download over 300MB of updates.

---

### Post by Bigglez on 2006-10-30
Sheesh - 300mb over and above the entire CD? That's harsh.

I'm confused about the "upgrade from the alternate CD" thing. Does this mean one cannot upgrade from the normal (live) CD? If not, why does it have a 'cdromupgrade' script on it? (it's b0rked, but it's there).

---

### Post by davarino on 2006-10-31
Bigglez (and others)

This may be a large part of why there are so many gorked out machines: Kubuntu.

I was updating a Kubuntu (installed over Ubuntu 6.06, updated from 5.10) installation and had to use the roundabout method (no gksu... of course I didn't try kdesu because it wasn't mentioned - I tend to be very literal). Everything died at the wrong times.

Of course my machine is just laying there staring at me, unable to speak or anything else. But now I think I know why.

Definitely worth staying away from Edgy right now if there's anything different from vanilla Ubuntu on your compu. At least that's how I see it. Things will change.

As for me, I'll just reinstall Kubuntu from scratch and call it a lesson in trusting "the team".

At least the deadline of October 26 *was* met. I gotta give credit for that. Heaven knows we have to meet deadlines on interim projects that are for some people to play around with and for other people to learn to hate Ubuntu with.

---

### Post by Bigglez on 2006-11-01
Alright - let's assume there's something the matter with Kubuntu 6.10 ...
Will there be other upgrade options from **6.06** upwards that do **not** go through 6.10 ?

I mean can I go from 6.06 LTS to 8.01 (in 2008, for example) and skip all the "18 monthers" in between?

I am a *little* hacked-off because I specifically dropped Fedora because I was sick of the format->reinstall cycle. I wanted to upgrade. So I came to Kubuntu, but I must say there's no clarity at all.

Is there some official word about upgrade paths from Dapper?

---

### Post by nerval on 2006-11-01
i believe everything that wasn't tried or not sure at all shouldn't be recommended on any post (and if there is, they must be deleted).

there is no proper upgrade, you can change all edgy to dapper as said; but the proper solution would be to give this sources.list as a code here. because almost everyone has a different sources list, and changing all to edgy (habracadabra) might crash your system, you can even end up screwing up everything. most kubuntu users doesn't even have update-manager, and a gnome user shouldn't recommend anything on kubuntu.

so please don't listen;

the best (so far) solution is this; download the iso for the latest; burn it into a cd (hopefully it burns without any fault) and then back up everything you have, then two options ahead of you 1) either install it into the empty partition of your hd, or 2) format and install it.

i tried to upgrade ubuntu dapper to edgy, listening to similar recommendations; yet i ended screwin' up the X, then boot doesn't load up and it somehow gives error 18 or error 17.

my last back-up was a week ago, so i felt a little bad about what i have lost during the last week; then i had my kubuntu cds for 6.06 i got from ubuntu. (gave away all ubuntu ones) installed kubuntu 6.06 and then tried to upgrade it listening posts around here; and everything was screwed up once again.

i don't know how many of you have free 20-30 hours updating your computer; yet if you are working and have a job then you are screwed. 

i wish there was an offical and proper recommendation on how to upgrade from dapper to edgy on kubuntu; yet i started hating every new versions under ubuntu.

because each time, i end up backing up all into cds and install it once again.

why not have one offical release for the rest of the time, and one test release. (just like gentoo) let the release upgrade itself every time it is needed, and let the test versions be a toy to developpers.

well, who the hell am i to say such things..

good luck.

---

### Post by ashrack on 2006-11-01
> **nerval said:**
> 
well, who the hell am i to say such things..

a user who's sick of having to reinstall everything to get a newer version of UBUNTU:mrgreen:

---

### Post by Bigglez on 2006-11-03
I agree - reinstallation is overkill. There are all those apps that you have taken time and bandwidth to install and now you must start making lists and backups of all kinds of things (like UPS and VPN scripts). Then kill everything and start over again...

I dunno.

:(

---

### Post by Bigglez on 2006-11-03
PPS - I always laugh at my Windows friends who are re-installing every few months. They do so because they don't have the time to learn the skills to keep Windows running smoothly, so when too much is going wrong, they format and re-install.
I always wonder what they actually do with their computers since they never suffer the "data backup" blues.

Anyway, I wanted Kubuntu to be better than that! Maybe it is, but after reading all the alarming upgrade anecdotes, I am hesitating on the upgrade.

---

