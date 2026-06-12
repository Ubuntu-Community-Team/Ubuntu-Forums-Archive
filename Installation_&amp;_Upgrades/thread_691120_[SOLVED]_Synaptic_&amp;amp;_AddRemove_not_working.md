---
title: "[SOLVED] Synaptic &amp;amp; Add/Remove not working"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by jldeshpande on 2008-02-08
Whin I click 'Synaptic Pakage Manager',  following error is displayed-

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


HISTORY-
 I am new to Ubuntu & Terminal commands.I installed Ubuntu Studio 7.10 ,before 5 days, on 3 Feb 2008 .
Updated it [@ 200MB] 
Tried to install Adobe Flash Player,at last succeeded after 2 days.
But during this i fired commands as mentioned in forum

sudo apt-get install ubuntu-restricted-extras

sudo apt-get remove --purge flashplugin-nonfree

Since then,I think above problim started,

Updating synaptic P M updates few bites and stops.

Will anybody help please? 

I am new to commands,Used winXP for @4 years but want to switchover to Ubuntu,though I have to compromise with my multimedia likings.

J.L.Deshpande

---

### Post by jrib on 2008-02-08
Run ```
sudo dpkg --configure -a
``` and paste the results

---

### Post by AlanR8 on 2008-02-08
I've posted on this before. Had a similar experince after a fresh install whilst doing all the updates.

The answer for me was as follows:

Run 

> sudo dpkg --configure -a

and look at the output. I found that one of the upgrade files was clashing with an existing file and the output gave me the choice to keep the existing file which is what I did.

I then ran

> sudo apt-get update

Then

> sudo apt-get upgrade

and all was well.

---

### Post by jldeshpande on 2008-02-09
> **_jason said:**
> Run ```
sudo dpkg --configure -a
``` and paste the results

I had already don this ,reading from forum.But before 2 days it was asking for password other than the installation/admin pw. So i was totally helpless & posted in forum. OK,leave it pl.
When now i pasted the code  quoted above,terminal window displayed-


j@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for j:
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
j@ubuntu:~$ 


and it stopped at this.
 Now synaptic pakage manager asks to use broken filter to locate a broken package.
When i did it it showed

pakage     sun-jawa6-sdk


I clicked   'apply',then the following matter got displayed in the window[which can't be copied]

dpkg: serious warning: files list file for package  'sun-jawa6-bin' missing

and many more.
But now synaptic pakage manager worked,just now i upgraded firefox & have to restart it,so taking leave at present.

Very very thanks to you kind,noble hearted people.Because of your help i shall be able  to continue with Ubuntu.

:guitar:
J.L.Deshpande.

---

### Post by zvacet on 2008-02-09
Find in synaptic **sun-java6-bin** and install it.

---

### Post by jldeshpande on 2008-02-09
> **zvacet said:**
> Find in synaptic **sun-java6-bin** and install it.

Thanks,checked,it is already installed.

Once again thanks to all of you. 

J.L.Deshpande,

---

