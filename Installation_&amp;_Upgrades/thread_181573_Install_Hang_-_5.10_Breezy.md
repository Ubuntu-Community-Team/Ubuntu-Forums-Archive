---
title: "Install Hang - 5.10 Breezy"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by x12Networks on 2006-05-24
Greetings all!

  I am new to Ubuntu, and am attempting to be a Mandriva convert. :)  I wanted to try the "server" install on an OLD laptop I have and see if I cna get fluxbox on it...  Well the install itself started to go fine, however when it ejected the CD and told me to reboot, it comes to the "Installing packages" screen and just hangs there.  No HDD activitiy, no network activity, nothing.  I can change to another tty and login, so I tried to run the apt-get update and it gave me an error about stuff being locked.  

Any thoughts on how to get the package install to actually go? :)

---

### Post by Ptero-4 on 2006-05-24
You have to ensure that the tty with the "Installing packages" have no apt program runnning (dkpg, apt-get, aptitude) and then run apt again from the tty you ran it when it complained about locked stuff.

---

### Post by x12Networks on 2006-05-24
[QUOTE=Ptero-4]You have to ensure that the tty with the "Installing packages" have no apt program runnning (dkpg, apt-get, aptitude) and then run apt again from the tty you ran it when it complained about locked stuff.[/QUOTE]

So in other words, when tty1 comes up automatically with the installing packages, just login on tty2 and kill all of those processes that may be running?

Once they are killed try the apt-get update


My only question, is what packages should the installer be installing on that first reboot?  Will I be missing anything by killing that install?

---

### Post by Frank-Hamersley on 2006-05-24
This is similar to the problems I have installing Breezy on a hp dx5150 (AMD 64).  On two attempts now it has choked part way through.

The first was at the point of creating profiles, the second like this thread loading packages.

The system at the moment has enough of the base Breezy on the HDD to be bootable but I too am wondering how to get the missing packages of the CD or from the net?

BTW I suspect the root problem is in the CD arena - either (1) a bad burn, (2) a dud DVD/CD drive (brand new though) or (3) a dodgy driver.  I suspect the (3) is the issue but don't know how to prove it yet.

I booted as "linux noapic nolapic" - perhaps I need other switches.

Cheers, Frank

---

### Post by Ptero-4 on 2006-05-25
x12Networks. The first stage of the install installs the "ubuntu-base" package, the second part (after the reboot) installs the ubuntu(k)(x)(ed)-desktop" package.

---

### Post by jtm2006 on 2006-05-27
> BTW I suspect the root problem is in the CD arena - either (1) a bad burn, (2)
> a dud DVD/CD drive (brand new though) 
Insert the Ubuntu CD, 
hit F3, 
look for the advanced boot option.
Look for the Verify Disc option.  It will come up after the CDROM had been detected.

---

### Post by jtm2006 on 2006-05-27
Thanks for the help Ptero-4

I have the same problem as x12Networks.  
I haven't tried your solution yet.  I'm disappointed that the second phase of the installer has such an obvious bug.
I'm confused as to why this doesn't affect everyone using Ubuntu 5.10.

---

