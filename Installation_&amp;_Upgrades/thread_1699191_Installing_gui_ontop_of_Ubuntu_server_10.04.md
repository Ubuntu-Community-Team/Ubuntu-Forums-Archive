---
title: "Installing gui ontop of Ubuntu server 10.04"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by pangeh on 2011-03-03
Hi,

I am trying to install ubuntu desktop 10.04 gui on top of ubuntu server 10.04. I have been able to do this previously using 9.10 and never had problems. I am not sure what I am doing wrong.

The steps I perform after successfully installing ubuntu server 10.04 are same as before:

- start machine and login
- Insert Ubuntu 10.04 alternate cd
-Type in sudo apt-cdrom add
-sudo apt-get update
-sudo apt-get [names of whatever packages I need] e.g. 
                sudo apt-get install ubuntu-desktop 

before this would go through fine and I would then type in:
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

However, 

This no longer works. WHen I try to install a pcakge it builds the pages lists required and asks am I sure I want to install. When I press yes it goes through to start installing the packages but I get loads of lines like below for every package and nothing installs I have to press ctrl + c to stop it:
Error cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ -release i386 (20110211.3)/ lucid/main libc6-i686 2.11.1-0ubuntu7.8 file not found

When i ran sudo apt-cdrom add I did notice that 3 different lines saying for example: W: Skipping nonexistent file /media/apt/dists/lucid/main/binary-i386/Packages

When I check in sources.list there is an entry for the cdrom.

Not sure what I am doing wrong. I'm trying again and this time am not going to press ctrl + c to interrupt and see if anything installs at all.

Any assistance/advice with this issue would be greatly appreciated. I am installing on an Ubuntu VM in virtual box and the alternate cd iso is mounted.

Regards
P

---

### Post by pangeh on 2011-03-04
Tried again and ran the same commands but did not interrupt the sequence and still got the same problem. Even though in sources.list the cd is referenced correctly I still get file not founds when trying to install packages from the cd. Its as if apt only acknowledges part of the cd.

Not happened before. Any assistance is really appreciated.

---

### Post by mörgæs on 2011-03-04
Why do you want to install from the CD? If you have a running Ubuntu, it is mush safer to install from the online sources.

---

### Post by pangeh on 2011-03-04
Just adding what I find for anyone else who gets the same problem. Found this site on the internet which outlines the exact same problem.

[https://bugs.launchpad.net/ubuntu/+source/apt-file/+bug/159396/comments/10](https://bugs.launchpad.net/ubuntu/+source/apt-file/+bug/159396/comments/10)

Would like to try on a host machine, when I can get my hands on one, instead of a VM and see if this makes any difference as I have tried adding the cdrom using apt with several of the switches. Unfortunately I am still raising my knowledge of Ubuntu, Linux etc so I may be looking in the wrong place...all part of the learning process though.

Going to use the Server and alternate cds for version 9.1 Karmic Koal, which I have used several times in the past on host machines without any problems, on a VM in virtual box and see what happens.

If anyone has more information relating to a work around for this problem or knows the cause and resolution to the issue any pointers/advice is sincerely appreciated.

regards
p

---

### Post by pangeh on 2011-03-04
Hi Morgaes,

Thanks for your reply. I want to use the cd to install for cases when I do not have access to the internet and when I just want to load from the cd because I feel like it. 

This functionality is there and so should work. I would like to identify and find out why this isn't working. 

regards
P

---

### Post by pangeh on 2011-03-04
Just a quick update as to progress with this issue.

I have tried the following combinations using these commands after installing the server software:
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo etc/init.d/gdm start

the versions of ubuntu with alternate cd I tried are as per below. Please note I tested using Virtualbox VM's as I dont have access to another computer I can use as a host.

Ubuntu server 10.04.1 with altcd 10.04.1 - Gives the file not found error when trying to install packages.

Ubuntu server 9.1 with altcd 9.1 - Worked fine without any problems

Ubuntu server 10.04.1 with altcd 9.1 - Gives the file not found error when trying to install packages.

Ubuntu server 10.04.2 with altcd 10.04.2 - Gives the file not found error when trying to install packages.

It appears the issue lies with the 10.04 software. Maybe to do with the version of apt, not sure if its different in 10.04 will check. Everything is fine when using the internet connection instead of the alternate cd. 

Will have more of a look into this and post anything I find/workaround. Its good to be able to load the GUI from the alternate cd when having to install a server to sites where there is limited download bandwidth restrictions. This isn't a major issue as I guess we could always save all the necessary packages to a location on the disk and make an entry in the sources.list file manually to the disk location of the necessary packages. Just annoying that it no longer seems to be working in 10.04.

---

### Post by nicorac on 2011-03-16
Hello everyone, here's my workaround for this bug.

Open /etc/apt/sources.list
```
sudo pico /etc/apt/sources.list
```
then edit the original cdrom line
```
deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110214.1)]/ lucid main restricted
```
to read like (adjust to your mount position)
```
deb file:///media/apt/ lucid main restricted
```
and finally update package list
```
sudo apt-get update
```

The only drawback is you have to mount cdrom manually.
Hope this helps :D

---

### Post by pangeh on 2011-04-01
Hi Nicorac,

Thanks very much for your reply, its handy to be able to load from the cd. Will give this ago and let you know the outcome.

Regards
P

---

### Post by pangeh on 2011-04-17
Hi Nicorac,

The steps you provided worked perfectly. Was lucky to as the internet wasn;t working on the day we had to setup the server so we got the server installed with the desktop using this method.

Thanks again for your kind help and insight.

Kind regards
P

---

### Post by dkavraal on 2011-07-23
Thanks nicorac. It just worked after 4 hours solid without wireless (!) and desktop options.

for late-comers:
just changed as deb file:///media/cdrom  (or whatever you have) in sources.list

---

