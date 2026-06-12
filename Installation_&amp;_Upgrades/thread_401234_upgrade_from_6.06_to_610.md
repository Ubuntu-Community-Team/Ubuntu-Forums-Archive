---
title: "upgrade from 6.06 to 610"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by garymc1 on 2007-04-04
Hi.
Can someone please help me, I am trying to upgrade from Ubuntu 6.06 To 610. I open up a terminal put the command in gksu "update-manager -c" and then the up-date manager opens and the option is there to upgrade to 610 but when I click on upgrade it says downloading file 1 of 2 for the update manager then it just hangs ???

I have tried this process a few times but it always hangs at the same place.

I have also tried rebooting.

Cheers

---

### Post by maheshjagadeesan on 2007-04-04
> **garymc1 said:**
> Hi.
Can someone please help me, I am trying to upgrade from Ubuntu 6.06 To 610. I open up a terminal put the command in gksu "update-manager -c" 

To use gksu "update-manager -c", you have to type it on a "run" prompt (Alt-F2 on a default configuration).

Good luck!

---

### Post by garymc1 on 2007-04-04
Hi I have tried the command gksu "update-manager -c"
in a "run" prompt (Alt-F2) but it still hangs at the same place 
when it says 
(downloading the up grade tool)
(downloading file 1 of 2 with unknown speed)

---

### Post by Feb29 on 2007-04-04
I think you should check your network connection and /etc/apt/source.list
to ensure the repositories are available.

---

### Post by garymc1 on 2007-04-05
I am new to this as you can tell,,
Thanks for the reply.
when I check my source list what should I be looking for ??
many thanks cheers Gary

---

### Post by cantormath on 2007-04-05
you want to uncomment the repos that have the software you need.  You can also open synaptic and change the repositories that way.  If you want to do it with terminal.....command line, open a teminal shell and type

```
:~$ sudo gedit /etc/apt/source.list
```

then look and see what is commented and what is not commented.  here is an example.

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

```

if you uncomment any repos, and save the file, you need to then

```
~$ sudo apt-get update
```

then you should be ready to go.  You know have access to the the other repositories of software.  instead of having just the microsoft server to update with, you have an endless supply of servers to retrieve software from.

if you plan to install things via commandline get familar with the apt-get command.  man apt......look on the web for explainations, its easy.  If you add universe and you want to try apt out, do this:

```
 ~$ sudo apt-get install cmatrix
```

Hit yes if any questions are asked.
this will install a small little program that is kinda cool for new folks. 
When its down, type cmatrix.  
hit ctrl+c to stop it.

have fun.

---

### Post by garymc1 on 2007-04-05
hear is a copy of my source.list what would I have to uncomment thank's for your time and help 
Cheers Gary

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

##Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by zvacet on 2007-04-05
Uncomment backports and security and comment Automatix and Wine.
```
sudo aptitude update
```
When you are finish with upgrade change your source list to Edgy.
```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

---

### Post by garymc1 on 2007-04-05
Hi I would just like to say thanks to the people that helped me out. I've got it upgraded now and its all working fine.
Thanks 
Gary  :guitar:

---

### Post by felin on 2007-04-05
Hi,

would someone be willing to spend a little time telling me what needs to be commented. I have tried to upgrade 3 times without success. I am very thankful.

> #
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
#AUTOMATIX REPOS END


---

### Post by la3875 on 2007-04-06
I've been playing with Dapper for a few months now and Feisty on a separate drive. I like the improvements I see so I decided to upgrade my Dapper install to Edgy. I followed the upgrade advice at ([https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)) and I think I'm close, but I don't want to break my install. I seem to be having a problem upgrading the x11 directory. See the attached screen shots with the error messages. What am I missing?

Thanks in advance!

---

### Post by cantormath on 2007-04-07
> **felin said:**
> Hi,

would someone be willing to spend a little time telling me what needs to be commented. I have tried to upgrade 3 times without success. I am very thankful.

you pretty much in this picture have all the repo's open so you are good.  What package are you looking for?

---

### Post by la3875 on 2007-04-12
I guess I need a shot of the package manager because its telling me I have two broken packages and I'm reluctant to force a reinstall or removal lest I break my current setup further. Thanks for giving this a look.

---

