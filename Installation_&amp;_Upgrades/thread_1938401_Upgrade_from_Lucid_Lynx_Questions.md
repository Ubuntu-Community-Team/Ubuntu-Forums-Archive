---
title: "Upgrade from Lucid Lynx Questions"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by gavin_attoe on 2012-03-09
I have Lucid Lynx and I'm thinking about upgrading to Oneiric Ocelot or Natty Narwhal.  Before I do, I have some questions if anyone has experience with either of these upgrades:

1. I have a lot of encrypted files by seahorse (pgp) with private keys.  A big issue with seahorse and Lucid Lynx is that you can't export and successfully re-import the keys to decrypt the files.  If I export the key with seahorse on Lucid Lynx, can I re-import with seahorse on a newer distribution successfully, or should I just decrypt all of the files for transfer, then re-encrypt them?

2. How many of your settings get deleted in the upgrade?
A. Will all of the desktop themes be gone?  
B. Will my program links on the task bar all be gone?  (I tend to use them more than desktop links)
C. Will programs and libraries I downloaded be gone? - java developer's kit, git, imagemagick, or even *gasp* fortune, cowsay, and xpenguins
D. Are your internet browser favorites deleted?
E. Are CompizConfig settings and/or the software transferred to the upgraded version?

Well that covers most of the questions I have.  Please either make me feel safe about upgrading or scare me out of doing it.

---

### Post by cogier on 2012-03-09
Have you tried a live CD of the latest Ubuntu with Unity? It is **VERY** different.

I can't answer all your questions but I would be in the "scare you away" camp on this.

I was unable to get Compiz to work with Unity. Gnome 2 desktop themes wont work in Unity. The "taskbar" is not the same as in Gnome 2.

Unless you are very sure I would stay with Lucid for now or you may be disappointed. Others will, I am sure, have a different opinion.

---

### Post by grahammechanical on 2012-03-09
There are big differences in the foundations of Ubuntu between 10.04 and 11.10/12.04.

The differences are not so great between 10.04 and 11.04 but there are some.

These differences are the reason, in my opinion, why upgrading beyond 11.04 leads to difficulties. Think seriously about doing a fresh install.

For a long time the Gnome part of Ubuntu was what is now called Gnome 2. That is no longer under development by Gnome organization.  They have switched to a new version of Gnome called Gnome 3.

Ubuntu has had to follow. So from 11.04 onwards Ubuntu is based upon the Gnome 3 desktop environment. Some things from Gnome 2 will still work on Gnome 3 but as Gnome 3 is developed and as it moves further away from Gnome 2 those utilities will have to be updated.

This is the process that has been taking place since the release of 11.04.  Themes and icons that work in 10.04 or 10.10 will not work in 11.10 - 12.04. Unless their developers have upgraded them.

This is the kind of issue you will face.

I suggest that you create a new partition and dual boot into 11.10. And try to set things up the way you want. See, if you can import your PGP keys and that stuff.

Your set up is unique to yourself. Can anyone really tell you what is safe and what is not? It is your data after all.

The Ubuntu team do a lot of testing of new releases but they are working in regards to basic, no modifications, default installs.

I have been trying for a week to run a series of tests on 12.04 Beta. I have just realized that the reason why the testing program was not working was because I was using a version of 12.04 that had been updated daily.

I have had to install 12.04 Beta 1 into a new partition for these tests to run. So, remember everything is based on a default install. And yet Ubuntu is easily modified. And that is where problems occur.

Regards.

---

### Post by gordintoronto on 2012-03-09
If you have a separate /home partition, life is a lot easier.

Without it, if you do a "clean install" you will lose everything. You can backup all your data (twice!).  But first, export your bookmarks from your browser, and "backup settings" if you use Evolution for email. Those steps will give you data files you can import after a fresh install.

Don't fool around with updating or re-installing until you are sure you have wonderful backup.

I have never used encrypted files; I figure there are many things which can go wrong, why add to the list. Mind you, I have a single-user computer.

I suggest you also make a list of apps you use before reinstalling.

Actually, we are so close to 12.04, which is an LTS release, I suggest you wait for it. Then try it from a Live CD or LiveUSB, and see how you like it. If you don't, have a look at Kubuntu, Lubuntu, Xubuntu or Linux Mint.

---

### Post by gavin_attoe on 2012-03-10
Thanks for your feedback so far.  To summarize what I'm getting out of your responses:

-Definitely try newer version in live CD/USB or separate partition first
-Ubuntu is created with clean installs in mind, not upgrades so don't expect any settings to transfer over
-Wait for a stable release of 12.0X before considering the jump to a new version of Ubuntu
-If I do upgrade, back all of my data up.

I'll wait for a few more people to weigh in before I change the status to solved, but so far I'm sticking with Lucid, in no hurry to upgrade.  I'd like to hear some people's experiences with Ubuntu upgrades, either with the versions I'm looking at or others.

---

### Post by darkod on 2012-03-10
Here is one more reason to wait for 12.04 LTS. Being a LTS, same as 10.04 LTS that you are running, you can upgrade directly to 12.04 LTS. If you are still considering an upgrade that is...

Just go into Update Manager options and set it to offer upgrades to long term releases only. That will offer LTS to LTS upgrade.

Otherwise, from Lucid you first need to go to Maverick, and only then to Natty, and if you decide to go to Oneiric that's one step more.

I really wouldn't have faith in three upgrades in a row, even if we are discussing linux and not windows. Too many things can go wrong.

So, you have about month and a half to investigate everything you need, until 12.04 gets released. Then you can decide upgrade directly to 12.04 or new clean install.

---

### Post by MSPdwalt on 2012-03-10
Useful command if you decide you're going to start from a fresh install, or just for research purposes. (check to see if the package is in 12.04)

```
sudo dpkg --get-selections > installed-software
```

This will dump your list of installed packages so getting all your apps back will be easier.

You'll probably want to backup your /etc/apt/sources.list file too so you can add the 12.04 versions of your extra repositories.

---

### Post by gavin_attoe on 2012-03-16
> **MSPdwalt said:**
> Useful command if you decide you're going to start from a fresh install, or just for research purposes. (check to see if the package is in 12.04)

```
sudo dpkg --get-selections > installed-software
```

This will dump your list of installed packages so getting all your apps back will be easier.

You'll probably want to backup your /etc/apt/sources.list file too so you can add the 12.04 versions of your extra repositories.

Thanks for the advice.  For anyone else reading this I didn't get any results with that sudo statement so I looked at the man page for dpkg.  Threre's just an extra space in the command MSPdwalt wrote, but I did not know that extraction of a full list of installed software was even possible like this before your suggestion.

```
sudo dpkg --get-selections >installed-software
```

The text file of information will be in your directory /home/username/

---

