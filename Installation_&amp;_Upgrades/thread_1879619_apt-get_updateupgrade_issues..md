---
title: "apt-get update/upgrade issues."
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by sazhagianambi on 2011-11-11
Hello All, 

I am still newbie for Ubuntu. Please let me know if you need more info for helping out. 

When I run

sudo apt-get update
sudo apt-get upgrade 

I started to see below error for last 2 days. It was working fine earlier. 


 Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.31.0+git20111107.f09e71af-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111107.f09e71af-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111107.f09e71af-0ubuntu1~11.10~ricotz0 is installed
E: Unmet dependencies. Try using -f.


So I tried sudo apt-get -f install and it gives below error


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0
The following packages will be upgraded:
  libglib2.0-0
1 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,879 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 188351 files and directories currently installed.)
Preparing to replace libglib2.0-0 2.31.0+git20111107.f09e71af-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement libglib2.0-0 ...
dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0_amd64.deb (--unpack):
 './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I didn't have much clue as how to fix this. Any Help is much appreciated.

Thank you very much. 

-Nambi

---

### Post by gravyplaya on 2011-11-11
I get the same exact error. I think ricotz needs to fix his packages. 

Not sure how to fix this. Not sure its anything we can fix. :confused:

Heres the error I get. 
E: /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0_amd64.deb: './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system

Fixed it.
run this command: sudo rm /usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz

then redo the upgrade. it will succeed this time.

---

### Post by sazhagianambi on 2011-11-12
Awesome, Thank you gravyplaya!.   That solved the issue. 

From what I saw it seems updating higher version causing issue? Hope it wont happen again.

---

### Post by odror on 2011-11-16
> **gravyplaya said:**
> I get the same exact error. I think ricotz needs to fix his packages. 

Not sure how to fix this. Not sure its anything we can fix. :confused:

Heres the error I get. 
E: /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0_amd64.deb: './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system

Fixed it.
run this command: sudo rm /usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz

then redo the upgrade. it will succeed this time.

It did not work for me
after deleting the above file.

When I type ap-get upgrade I get:
> # apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.0+git20111113.fac9e8d2-0ubuntu1~11.10~ricotz0) but 2.31.0-0ubuntu1~oneiric1 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.31.0+git20111113.fac9e8d2-0ubuntu1~11.10~ricotz0) but 2.31.0-0ubuntu1~oneiric1 is installed
E: Unmet dependencies. Try using -f.

I tried the -f option as well. It did not help.

---

### Post by sazhagianambi on 2011-11-16
I didn't understand whether its correct to do but I do had same issue once again yesterday then. Again I did the the same which seems to help.

 sudo rm /usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz

I am sorry it didn't work for you, may be somebody else could chime in.  I'll change Solved status, so some experts can peek in. 

Regards,
Nambi

---

### Post by mortenbrekk on 2011-11-16
It helped to me to remove the file, but I had to run 
sudo apt-get -f install 
before I ran
sudo apt-get upgrade

---

### Post by odror on 2011-11-16
> **mortenbrekk said:**
> It helped to me to remove the file, but I had to run 
sudo apt-get -f install 
before I ran
sudo apt-get upgrade

I tried it exactly like that, I got the same error. I would like to mention that since this upgrade I am not able to use gnome 3.

---

### Post by nexus_dublin on 2011-11-16
Worked fine for me (thanks!).
* Removed file
* Ran apt-get install -f
* Ran apt-get upgrade

---

### Post by kstac13 on 2011-11-18
I am having the same issue.
#Removed the file.
#Ran apt-get install -f
#Ran apt-get upgrade
 
Still getting an error.

The following packages have unmet dependencies:
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0 is installed
E: Unmet dependencies. Try using -f.

---

### Post by raja.genupula on 2011-11-18
first do this and  dont go for upgrade now , paste here

```
sudo apt-get install -f
```

---

### Post by kstac13 on 2011-11-19
> **raja.genupula said:**
> first do this and  dont go for upgrade now , paste here

```
sudo apt-get install -f
```

I did sudo apt-get install -f and I got the following:

Correcting dependencies... failed.
The following packages have unmet dependencies:
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111027.9782598b-0ubuntu1~11.10~ricotz0 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by raja.genupula on 2011-11-19
Hi man 
         I have seen some similar old threads with your problem but i need to confirm again .Have you installed Ubuntu or upgraded ? If upgraded then in what way you did ? I mean directly from 10.10 to 11.10 or some thing else ? 

I need this details man.

---

### Post by kstac13 on 2011-11-19
I upgraded. I installed 11.04 and then upgraded to 11.10.  I then installed gnome-shell which I think is what is causing the problem I have had 11.10 since from its official release day and installed gnome shell awhile ago. I didn't have any problems until about a week ago.  If it means I have to remove gnome-shell to get this to go away I will. Just not sure what to do. Hope this info helps.

---

### Post by raja.genupula on 2011-11-19
Hi man issue looking some what complex but i will try man .
open your synaptic and look for this pkg libglib2.0-0 and any broken pkg's and try to install that pkg and all its dependencies from there .

all the best.

---

### Post by Bobhuber on 2011-11-19
> **kstac13 said:**
> I upgraded. I installed 11.04 and then upgraded to 11.10.  I then installed gnome-shell which I think is what is causing the problem I have had 11.10 since from its official release day and installed gnome shell awhile ago. I didn't have any problems until about a week ago.  If it means I have to remove gnome-shell to get this to go away I will. Just not sure what to do. Hope this info helps.
You need to get rid of ricotz PPA and re-install gnome shell from the package manager. Also if you have the gnome3/team/gnome3 PPA  installed it should be removed or disabled. Both of these are development and will cause things to break.For gnome-tweak and the extensions use the web8 PPA.

---

### Post by newalopez on 2011-11-20
I know it's quit dirty, but just deleted the changelog file mentioned there from my system, them updated with -f, and works.

---

