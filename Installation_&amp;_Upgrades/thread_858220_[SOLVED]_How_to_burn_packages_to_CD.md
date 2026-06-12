---
title: "[SOLVED] How to burn packages to CD?"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by simonz on 2008-07-13
I would like to burn some or all the packages on Ubuntu 8.04.1 system to a CD.  Then take the CD to another similar system that has no internet connection, and use the CD as Repository.

How would I do this?

simonz

---

### Post by PeteBraven on 2008-07-13
Funny you should ask this, I had a real nightmare trying to get my version of Nero to actually use the ISO to unpack the image to make the CD a bootable yesterday!
It was my geek son who suggested I downloaded 'infrarecord' and use the 'burn disk' 'from image' options. Yes it's free and open-source from source-forge. I had no problems burning the image, just getting my system to run is a headache due to some driver issues on my old kit here.
Trust me, the burner works fine, you will have to have a DVD burner though, it wouldn't fit on a normal CD.

---

### Post by simonz on 2008-07-13
Pete, infrarecord doesn't solve my problem.  I already have two programs to burn CD/DVDs (brasero and nautilus). I'm looking for information on how to get the packages from my computer to a CD.  In other words how do I bundle the packages so they look like a repository?

simonz

---

### Post by PeteBraven on 2008-07-13
Hmmm,.. you could 'unpack' the ISO image to a folder and use those. I have done that here (not intentionally but handy!) and that might work for you. The resulting images can be burnt to normal CDs,.. two of them.
I did this on a windows based machine and now have all the files to  look at individually. I should point out that some of them are written in other languages than English which caused some amusement this end!

---

### Post by simonz on 2008-07-17
Bump...

How do I copy packages from one Ubuntu computer to CD and install same packages to other Ubuntu computer?  

The second computer has no Internet accesss, so can't upgrade that way.

Thanks,
simonz

---

### Post by bigken on 2008-07-17
apt on cd might work worth a try

---

### Post by soxs on 2008-07-17
use APTonCD:
[http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html](http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html)

---

### Post by Vivaldi Gloria on 2008-07-17
You can download packages manually from ubuntu package search

```
http://packages.ubuntu.com/
```

and then burn them on a cd.

On a side note, what aptoncd does is to make an iso out of packages in

```
/var/cache/apt/archives
```

I don't bother with aptoncd and do it by hand.

---

### Post by Archmage on 2008-07-17
Just a small comment:

You normaly don't need the security fixes if you aren't connected to the internet. Therefore they wouldn't be much use for this updates on the PC without internet.

Later if you want to upgrade to a new Ubuntu-Version: Simply use the alternate CD and plug it into the CD-Rom. Than you can upgrade without an internet-connection.

---

### Post by simonz on 2008-07-17
I'm going through all this with packages because I need to get the Network Connection Manager 'wicd' and this isn't on my computer.  The regular Network Manager isn't working, but wicd does work for me and I removed it by mistake (another story).  

The command to get wicd is this:

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

I've run this on a computer with Internet access and it got wicd, but can't figure out to copy wicd to a CD or which package it is contained in.

simonz

---

### Post by Archmage on 2008-07-18
> **simonz said:**
> The regular Network Manager isn't working, but wicd does work for me and I removed it by mistake (another story).

```
sudo aptitude install wcid
```

> **simonz said:**
> I've run this on a computer with Internet access and it got wicd, but can't figure out to copy wicd to a CD or which package it is contained in.

```
aptitude search wcid
```

---

### Post by simonz on 2008-07-18
It it was suggested here that I should use AptOnCD to port my packages to computers without an Internet connection.  

Here are the results:  I installed AptOnCD on the computer with Internet access and burnt a CD of all the packages. I brought the CD to another computer without Internet connection. And, voila.  It automatically brought up Synapic Package Manager without a hitch and added the AptOnCD to the local repository.  So, without an internet connection, I'm now able to install packages on a CD taken from another computer.

My first attempt at using AptOnCD, a couple of weeks ago, created a CD that when used in Synaptic Package Manager would give some kind of an "E: file not found" error.  It must have been a bad burn.  

Now everything is wonderful and I got wicd on to my computer without Internet access. 

Posters, thank you for suggesting AptOnCD, it solved my problem perfectly.

simonz

---

### Post by bigken on 2008-07-18
> **simonz said:**
> It it was suggested here that I should use AptOnCD to port my packages to computers without an Internet connection.  

Here are the results:  I installed AptOnCD on the computer with Internet access and burnt a CD of all the packages. I brought the CD to another computer without Internet connection. And, voila.  It automatically brought up Synapic Package Manager without a hitch and added the AptOnCD to the local repository.  So, without an internet connection, I'm now able to install packages on a CD taken from another computer.

My first attempt at using AptOnCD, a couple of weeks ago, created a CD that when used in Synaptic Package Manager would give some kind of an "E: file not found" error.  It must have been a bad burn.  

Now everything is wonderful and I got wicd on to my computer without Internet access. 

Posters, thank you for suggesting AptOnCD, it solved my problem perfectly.

simonz



yep its a super piece of kit pleased your sorted :)

---

