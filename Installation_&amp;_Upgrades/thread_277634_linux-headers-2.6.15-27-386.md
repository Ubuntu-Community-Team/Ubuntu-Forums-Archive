---
title: "linux-headers-2.6.15-27-386"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by blah19 on 2006-10-14
Hi,
I have been trying to install VMWare and it asked me for the location of the headers, which I realized were not installed(to my knowlage) so I ran a [PHP]sudo apt-get install linux-headers-`uname -r` [/PHP]
and I got this error:
[PHP]E: Couldn't find package linux-headers-2.6.15-27-386[/PHP]
I also ran a 
[PHP]sudo sudo apt-get update[/PHP]
still no go. I'm fairly new to linux, so take it easy please.
Thanks a lot!

BTW: I'm running Ubuntu Dapper with the KDE environment installed.

---

### Post by wieman01 on 2006-10-14
It appears that you don't have an internet connection, is that right? Then simply insert the Ubuntu Live CD and run these commands:
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`

---

### Post by blah19 on 2006-10-14
nope I'm on the internet now, I tried using my CD repository to intall the header via synaptic, but it was an older version then what was being used.
the cd was linux-headers-2.6.15-26-386  I need linux-headers-2.6.15-27-386

---

### Post by wieman01 on 2006-10-14
> **blah19 said:**
> nope I'm on the internet now, I tried using my CD repository to intall the header via synaptic, but it was an older version then what was being used.
the cd was linux-headers-2.6.15-26-386  I need linux-headers-2.6.15-27-386
Then how did you get the higher kernel version in the first place? With no CD & no internet connection I am afraid you won't be able to install the headers.

_**EDIT:**_
Yes, the version number of both kernel & headers must match.

---

### Post by blah19 on 2006-10-14
> **wieman01 said:**
> Then how did you get the higher kernel version in the first place? With no CD & no internet connection I am afraid you won't be able to install the headers.

_**EDIT:**_
Yes, the version number of both kernel & headers must match.

no I _**HAVE**_ an internet connection... Im on the internet right now.

---

### Post by wieman01 on 2006-10-14
> **blah19 said:**
> no I _**HAVE**_ an internet connection...
I am sorry... It's too early in the morning here. Can you try this:
> sudo [COLOR="Red"]aptitude[/COLOR] install linux-headers-`uname -r`

---

### Post by blah19 on 2006-10-14
Alright I get this, prob not a good thing.
[PHP]Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-headers-2.6.15-27-386"
The following packages have been kept back:
  desktop-base gdm gnome-session libdb3 libglib1.2 libgtk1.2
  libgtk1.2-common libungif4g wine
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[/PHP]

---

### Post by wieman01 on 2006-10-14
One more thought: Are you behind a proxy?

---

### Post by blah19 on 2006-10-14
> **wieman01 said:**
> One more thought: Are you behind a proxy?

Uh, Yeah, on a collage campus(dang your preceptive)

---

### Post by wieman01 on 2006-10-14
If you have a GUI, then you can change the proxy settings using Synaptic:
> sudo synaptic

[COLOR="Red"]Settings->Preferences->Network[/COLOR]

---

### Post by blah19 on 2006-10-14
> **wieman01 said:**
> If you have a GUI, then you can change the proxy settings using Synaptic:


[COLOR="Red"]Settings->Preferences->Network[/COLOR]

Actuly I already have the proxy on the synaptic set up, I've even added some universal repositories and got some extra software.
[ATTACH]17588[/ATTACH]

---

### Post by wieman01 on 2006-10-14
Alright. Do you see the headers in Synaptic? If you press reload the should be found in there.

Also make sure that this file:
> sudo gedit /etc/apt/sources.list
...has these 2 lines:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by blah19 on 2006-10-14
Alright, 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse was NOT in that file, so I added and saved, then reloaded and closed, and NOW ran my [PHP]sudo apt-get install linux-headers-`uname -r`
[/PHP]
still get the same error

---

### Post by wieman01 on 2006-10-14
Why don't you use **[COLOR="Red"]Synaptic[/COLOR]** to install the headers? They should be listed in there. Do you see them? 

Then right-click->Mark for Installation, then press "Apply". That should work...

---

### Post by blah19 on 2006-10-15
The Highest it goes with the search "linux-headers" is 2.6.15-26-386 I need 2.6.15-27-386. and it skips a few versions in between that one and the previous one(linux-headers-2.6.15-23-386)

---

### Post by wieman01 on 2006-10-15
> **blah19 said:**
> The Highest it goes with the search "linux-headers" is 2.6.15-26-386 I need 2.6.15-27-386. and it skips a few versions in between that one and the previous one(linux-headers-2.6.15-23-386)
Mmm... I don't get it. When I scroll down a bit I can see all the necessary versions (screenshot). 

Have you pressed "Reload"? It's definitely in the repositories.

---

### Post by blah19 on 2006-10-15
This will show everything (MY screen shots) I did reload (tried 26, they do not work win VMWare)
[ATTACH]17596[/ATTACH][ATTACH]17597[/ATTACH][ATTACH]17598[/ATTACH][ATTACH]17599[/ATTACH][ATTACH]17600[/ATTACH]

---

### Post by blah19 on 2006-10-15
And One More
[ATTACH]17601[/ATTACH]

---

### Post by wieman01 on 2006-10-15
> **blah19 said:**
> This will show everything (MY screen shots) I did reload (tried 26, they do not work win VMWare)
[ATTACH]17596[/ATTACH][ATTACH]17597[/ATTACH][ATTACH]17598[/ATTACH][ATTACH]17599[/ATTACH][ATTACH]17600[/ATTACH]
Ahh... You're still using Breezy. Not sure how up-to-date those repositories are. I am using Dapper... So I recommend that you replace your 'main' and 'multiverse' lines with these:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
That at least let's you make use of the Dapper's repositories. You can restore your repositories later.

---

### Post by blah19 on 2006-10-15
I Now have this, still no fix on reload:

[PHP]# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse 


##deb http://archive.ubuntu.com/ubuntu breezy main restricted
##deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
# deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
# deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
# deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
# deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://wine.budgetdedicated.com/apt dapper main
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
[/PHP]

---

### Post by wieman01 on 2006-10-15
I would disable (comment out) the Breezy respositories for a minute and then reload. If that does not work then I don't know...

---

### Post by blah19 on 2006-10-15
YES!!!!!! I did a find+replace after saving a backup of breezy to dapper and I got it!!!! Thank you SOOO much man. I owe ya

---

### Post by wieman01 on 2006-10-15
> **blah19 said:**
> YES!!!!!! I did a find+replace after saving a backup of breezy to dapper and I got it!!!! Thank you SOOO much man. I owe ya
Glad it worked. There is a useful source-list generator should you ever have problems again: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by blah19 on 2006-10-15
> **wieman01 said:**
> Glad it worked. There is a useful source-list generator should you ever have problems again: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

I Bow to the GURU

---

### Post by wieman01 on 2006-10-15
> **blah19 said:**
> I Bow to the GURU
No... I am really not. Just using common sense most of the time. That's why my "performance" is down early in the morning & picks up only after a cup of coffee or two. Haha... See you next time! :-)

---

### Post by Kulgan on 2006-10-16
after having installed the headers, what directory should they be located in? I am also installing VMWare, and I'm even fresher than you :P

thanks,
-K



**
oh nvm, they are in /usr/src/linux-headers-<nr>/ after all... that was stupid...

---

