---
title: "I have upgraded a machine to 24.04.1"
date: 2024-10-07
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-10-07
I have upgraded a machine to 24.04 as its been a while and I figured it was now fine - its not.  So, my question is what should I do now?  Should I download 22 or, I noticed that they now have a 24.04.10 which is still in the work but it is available.  So which one should I get?

Thoughts?

---

### Post by grahammechanical on 2024-10-07
I am on Ubuntu 24.04.1 LTS and I do not experience problems. This is a fresh install. Did you do an online upgrade?

Do not install Ubuntu 24.10. It only has 9 months support. And then you will have to continue to do online upgrades every 8 months until you reach the next LTS release. Which is 26.04 LTS.

Regards

---

### Post by bobunderwood99 on 2024-10-07
What's wrong with it?

---

### Post by guiverc on 2024-10-07
Ubuntu 24.04 is the 2024-April release, and its current *upgrade/ISO *level is .1, ie. 24.04.1

Ubuntu 24.10 is currently in *beta* (actually *final* which means its currently at *Release Candidate* level so it's close to being release), HOWEVER Ubuntu 24.10 is part of the two year development cycle for Ubuntu 26.04 LTS, and the only connection it has with Ubuntu 24.04 LTS was that the final 24.04 product was the *starting* point for the work towards Ubuntu 26.04 LTS.

There is no Ubuntu 24.04.10 

Ubuntu 24.04.1 is updated media for Ubuntu 24.04 LTS,

 and 

Ubuntu 24.10 is a different (*later*) product.

[I]-----

If the 24.04.1 confuses you, I'll provide a link to [/I][https://fridge.ubuntu.com/2024/08/30/ubuntu-24-04-1-lts-released/](https://fridge.ubuntu.com/2024/08/30/ubuntu-24-04-1-lts-released/) where you'll read

> As usual, this point release includes many updates and updated  installation media has been provided so that fewer updates will need to  be downloaded after installation.

ie. the 24.04.1 is just updated media for the Ubuntu 24.04 LTS system; installed systems just upgrade and show 24.04.1 in the week *before* the release of the ISO; it's not a new product.

---

### Post by ActionParsnip on 2024-10-08
To "roll back" you will need to wipe 24.04 off and do a clean install of 22.04, then restore your user data from your backups

---

### Post by makitso on 2024-10-08
> **bobunderwood99 said:**
> What's wrong with it?   I tried to update my daily driver laptop to 24.04.1 and the resulting system was very unstable, crashes, blank screens, etc.   So, tried a clean install and that hung with my LUKS encrypted home  partition.

---

### Post by jgw on 2024-10-08
Thank you for all the replies!  I am going to move back to ubuntu-22.04.5-desktop-amd64.iso and I am currently down loading it.  I will clean up the ssd from everything that's on it and start over from scratch.  Makes sense to me!

---

### Post by guiverc on 2024-10-08
This maybe too late, but I wrote an answer about *unclean* re-installs here - [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

It applies to ISOs using the `ubiquity` or `calamares` installer; Ubuntu 22.04 LTS used the `ubiquity` installer, so its fully functional.

( *its not functional with ubuntu-desktop-installer at 24.04 & 24.10 due to forced format *)

Going backwards can cause software issues, as older software may not know or deal with decisions made by the developers on newer versions; and these are program/app or package specific; with me encountering issues with evolution, liferea other other apps... which is the reason why I mention *homework*, or reading package/app release notes to ensure you significant changes occurred that will cause problems when you move backwards; but in those circumstances you'll usually have issues with data restores anyway; which is the normal approach (*and problems of this type are the exception, or rare, but can occur** thus is matters if your data matters to you*)

The *unclean*  (*dirty or repair*) install assumes only official Ubuntu software, but it can work with some 3rd party too, but for best results I don't let it try 3rd party & just re-add that myself afterwards.

---

