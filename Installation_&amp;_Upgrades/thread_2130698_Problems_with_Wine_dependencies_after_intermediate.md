---
title: "Problems with Wine dependencies after intermediate upgrade"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by nicolamenicacci on 2013-03-30
Hi everyone,
Last week, as I was going through some USC update, I let the process take care of itself. At a certain point I read Wine was no longer necessary and was going to be replaced, as well as Virtualbox. The problem is that the line re-appeared in my mind right after I had clicked the Ok button (there is no paradise for jerks, we say here where I live, in Italy!).
So, when update was complete, I first fixed the problem with Virtualbox then simply went back to Ubuntu software center intended to re-install Wine.
Big trouble, it cannot be installed anymore, there is a dependency problem.
I asked for support in the Italian forum, they all said it was only a matter of time before dependencies could be solved. In the meantime, I checked with Synaptic if some packages were damaged, fixed everything using dpkg and recovery mode.
Again, no way.
I got another reassurance to wait, things would have been solved soon, but after 9 days I am beginning to be a little worried even because, needless to say, I need Wine for a couple of things and programs which runs only on windows (one of them I can easily manage using Virtualbox, not the second one - a cd-rom English-Italian dictionary - it seems virtualbox is unwilling to run .exe files from Cd-s and this dictionary does not require installation. Troubles never come alone!)
I also attempted to adjourn repositories and try the 1.5.26 Wine version, but there are still dependencies problems.
Any of you experienced the same issues? Did you manage to work them out? Do I really have to only wait and hope?
Many thanks everyone in advance. If something is unclear, please ask and I'll be more than glad to be clearer.

Nicola, Florence, Italy

---

### Post by kc1di on 2013-03-30
Here's what I would try:

go to a terminal and type the following commands (one at a time):

```
sudo apt-get purge wine
sudo apt-get update
sudo apt-get install wine

```


if you get any error messages to any of the commands list them here. 
good luck ;)

---

### Post by nicolamenicacci on 2013-03-30
First of all, thank you so much for your reply.
Second, the first two commands went fine, no problem at all.
The third, here is the message
```
 sudo apt-get install wine
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 wine : Dipende: wine1.5 ma non sta per essere installato
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati. 
```

which means in short
Some packages cannot be installed. This could mean an impossible situation was requested or, if you are using a developing distribution, some requested packeges have not yet been created or were removed by Incoming.
The following info may help solve the situation:
the following packages have unsatisfied dependencies
wine: depends wine1.5 but it is not about to be installed
Impossible to correct problems, some damaged packages are blocked.

Not a good situation at all, I guess.

---

### Post by kc1di on 2013-03-30
which version of ubuntu are you using?

---

### Post by kc1di on 2013-03-30
ok I'm running 12.04 lts and added the wine PPA Repository and wine 1.5 installs without any problems.  so I believe it's the repostitory your using. 

go to [this page]("http://www.winehq.org/download/ubuntu") and add the wine ppa as instructed. then try the commands I gave you again.

---

### Post by nicolamenicacci on 2013-03-30
> **kc1di said:**
> ok I'm running 12.04 lts and added the wine PPA Repository and wine 1.5 installs without any problems.  so I believe it's the repostitory your using. 

go to [this page]("http://www.winehq.org/download/ubuntu") and add the wine ppa as instructed. then try the commands I gave you again.

Hi again Dave,
well, I had done it already, but I did it again, adding the repository, then repeating the same commands you wrote before.
Exactly same outcome, same message.
I wonder if something could change by launching the live CD and choosing to fix Ubuntu from there.
My distro is 12.10, sorry for not saying that before.

---

### Post by kc1di on 2013-03-30
for sum reason the repostitory your using is not providing the needed dependencies. 

maybe try this first. 
go to SoftWare Center >Edit >Software Sources in the box that comes up almost at the bottom is a drop down dialogue click on that and change the server your using.
and try again. If that does not work please go to /etc/apt/sources.list and copy it here. let me take a look at how it's configured.

---

### Post by nicolamenicacci on 2013-03-30
Hi Dave,
different move, same outcomes, alas.
Here is the code you requested. I have two files like that, by the way-sources.list and sources.list.save and the content is exactly the same in both
Goes like this
```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal universe
deb http://it.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://it.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://it.archive.ubuntu.com/ubuntu/ quantal-security main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-security main restricted
deb http://it.archive.ubuntu.com/ubuntu/ quantal-security universe
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-security universe
deb http://it.archive.ubuntu.com/ubuntu/ quantal-security multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main

#samsung drivers
deb-src http://www.bchemnet.com/suldr/ debian extra
deb http://www.bchemnet.com/suldr/ debian extra
deb http://it.archive.ubuntu.com/ubuntu/ quantal-backports restricted main multiverse universe
```


Hope this helps

---

### Post by kc1di on 2013-03-31
I have to say I'm at a loss at this moment what to try.  

you could try this though I don't believe it would be the problem. 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
```
Then try to install wine again.

---

### Post by tlu on 2013-03-31
I'm not using wine so I can't reproduce your problem. Just one suggestion: You might try to install wine with aptitude instead of apt-get as aptitude is often more intelligent in resolving dependency problems. It usually offers one or more possible solutions to solve the existing problem. Worth a try ;)

---

### Post by nicolamenicacci on 2013-03-31
Hi Dave,

Unfortunately, same outcome :(

---

### Post by nicolamenicacci on 2013-03-31
Thanks for your tip.
I will see how to install from Aptitude, hoping I can manage, and keep you posted

---

### Post by nicolamenicacci on 2013-03-31
> **tlu said:**
> I'm not using wine so I can't reproduce your problem. Just one suggestion: You might try to install wine with aptitude instead of apt-get as aptitude is often more intelligent in resolving dependency problems. It usually offers one or more possible solutions to solve the existing problem. Worth a try ;)

Was not sure about what and how to do that, I preferred not to run any risks

---

