---
title: "Basic Question About new install"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by xc_xtc on 2006-03-12
Hi all,

  This is my first exposure to linux. I installed Ubuntu easily but can not install anything else that needs to be compiled.

   I tried running so sudo (what is sudo??) command that i read would download the 'make' and etc... files but it only downloaded some parts.. i think.

  anyways, I just want the package installed 100% so I can try to start learning. What is the problem?

 Its saying 'no rule to make target 'install'. Stop.

 Thanks for your help in advance.

---

### Post by simon_is_learning on 2006-03-12
If you're trying to compile a program, then you need build-essential

sudo apt-get install build-essential

sudo is a program that let's you do something temporary as root. It's there becouse you can mess up thing if you are root and don't know what you are doing. 

EDIT: found a link: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

if you want to be root constant. Type sudo su.

---

### Post by xc_xtc on 2006-03-12
i tried to get that last night but i got errors (and lots of them) in the end.

  Is there a way to uninstall half installed proggies? (easily :p )

 Also do i have to reboot if not asked to after installs?

---

### Post by Klaidas on 2006-03-12
For uninstalling, go to Synaptic and search for the prgram there. Then, mark for Removal. By the way, what are you trying to install? Maybe there is a package in *.deb or in Synaptic already? :)
If you aren't asked to restart - you don't have to :)

---

### Post by xc_xtc on 2006-03-12
lol... for now, typical newbie stuff, ie airsnort; etc..

  The errors I got were due to servers not responding. Well... in anycase I remember them indicating the address were not correct.

 As for synaptic, I couldnt find it... only kynaptic....

---

