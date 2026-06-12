---
title: "Tried to install firefox - adept crashed"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by rousp on 2008-12-01
Hi, first of all I'm new to kubuntu and linux, so please be patient :-)

I tried to install the firefox 3 internet browser using a guide I found.
[This guide]("http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html")

When I tried to add the third party link nothing happend. So I closed down  adept after a minute or so. Now adept won't launch. So my inpatience probably killed it.. Could you please help me unkill it?`;-) 

I'm familiar enough with terminal to use it, if you provide the codes I should use.

---

### Post by abn91c on 2008-12-01
sudo dpkg --reconfigure -a
sudo apt-get install -f

---

### Post by rousp on 2008-12-01
Here is the result of that:
kristian@stuepc:~$ sudo dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
kristian@stuepc:~$ sudo apt-get install -f
E: Type 'http://ppa.launchpad.net/fta/ubuntu' is not known on line 54 in sourcelist /etc/apt/sources.list
E: The list of sources could not be read.
kristian@stuepc:~$

---

### Post by taurus on 2008-12-01
Bet there is something wrong with the line, line 54, that you added to your /etc/apt/sources.list.  Usually, the line should start out with **deb** so you can either add deb to the front of it and see if that works or put a # in front of that line to comment it out.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by rousp on 2008-12-01
And this is what I've got:

kristian@stuepc:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
kristian@stuepc:~$ apt-get install gksu
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kristian@stuepc:~$

Should I just reinstall the lot and have a fresh start?

---

### Post by taurus on 2008-12-01
Sorry.  Forgot you are running KDE.  Try

```
kdesu kwrite /etc/apt/sources.list
```
And if you don't have kwrite, you can use a basic text editor then.

```
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by rousp on 2008-12-01
Here is line 54

[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy mainhttp://ppa.launchpad.net/fta/ubun$

I should change this to:
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

Would that be correct?

I did those changes. Still won't start... 

I wrote them out. That worked! Could I just delete these lines from the file then?

---

### Post by taurus on 2008-12-01
Just put a # in front of those two lines to comment them out.  Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by rousp on 2008-12-01
It works just fine now!
So if it's okay just to leave then written out I'll do that. 
If not, here his my siurces.list

kristian@stuepc:~$ cat /etc/apt/sources.list                               
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted                                                                
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to       
# newer versions of the distribution.                                           

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid universe                 
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid universe             
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates universe         
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates universe     

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
kristian@stuepc:~$

---

### Post by taurus on 2008-12-01
Apparently, you are running Intrepid so it is not a good idea to add Hardy entry in your /etc/apt/sources.list.  It could cause major problems later on.

---

### Post by rousp on 2008-12-01
Interpid? Don't know what  you are saying now =P

But I'll remove those lines from the list then? If I got you right?

---

### Post by taurus on 2008-12-01
8.10 = Intrepid
8.04 = Hardy

---

### Post by rousp on 2008-12-01
Thanks alot for all your help!! 

My first day with a linux based OS has been good. Honestly I'm suprised how good it is!

It even suports the main features on my Logitech diNovo Edge keyboard! 
I'm pretty sure that I'm going to keep linux!

---

