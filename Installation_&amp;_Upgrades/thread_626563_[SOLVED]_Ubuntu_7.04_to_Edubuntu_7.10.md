---
title: "[SOLVED] Ubuntu 7.04 to Edubuntu 7.10"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by src2206 on 2007-11-29
Hello

I hope this forum allows questions regarding Edubuntu.

I have recently received a **Edubuntu 7.10 CD** (Thank you ShipIt). I already have **Ubuntu 7.04 installed**. Could anyone please clear my following doubts?

1. Is it possible to **upgrade from Ubuntu 7.04 to Edubuntu 7.10**? And if I do **will all my customizations in Ubuntu and programs will run as usual**?

2. What edubuntu use as DE- **KDE or GNOME** ?

3. Will the** interface remain all the same** if I upgrade?

4. I tried to search but could not get a **complete list of packages** available in Edubuntu 7.10, so is there any list?

Please let me know.

Thank you.

---

### Post by src2206 on 2007-11-29
Could please someone help me out? :(

Sorry for bumping.

---

### Post by src2206 on 2007-12-02
Bump...... :(

---

### Post by confused57 on 2007-12-02
Just upgrading from Feisty 7.04 to Gutsy 7.10 runs a risk of failing, which would require reinstalling from scratch.  I don't think it would be possible to upgrade from Feisty 7.04 to Edubuntu 7.10.

You could try installing edubuntu-desktop to your current Feisty 7.04:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install edubuntu-desktop
```

Then you can choose which session(desktop) you want to log into at the login screen...in my opinion, this would probably be your best option, since you want to keep your current configurations.  You can remove edubuntu-desktop with:
```
sudo aptitude remove edubuntu-desktop
```

A Google search of edubuntu-desktop should give you an idea of the packages found in edubuntu.   Edubuntu uses Gnome...

---

### Post by src2206 on 2007-12-02
Thanks

As I put the Edubuntu CD (it is not Desktop version, so it can not be tested as Live CD); Ubntu informs me about availability of the Upgrade Package in the CD. As both are based on Debian and as Edubuntu seems to be just a different bundle of our favorite Ubuntu targeted to a specific user base, I was just wondering why should not it can be a simple upgrade like upgrading to Ubuntu 7.10. Core wise Ubuntu and Edubuntu seems to be the same.

---

### Post by confused57 on 2007-12-02
> **src2206 said:**
> Thanks

As I put the Edubuntu CD (it is not Desktop version, so it can not be tested as Live CD); Ubntu informs me about availability of the Upgrade Package in the CD. As both are based on Debian and as Edubuntu seems to be just a different bundle of our favorite Ubuntu targeted to a specific user base, I was just wondering why should not it can be a simple upgrade like upgrading to Ubuntu 7.10. Core wise Ubuntu and Edubuntu seems to be the same.
I haven't seen anyone upgrade using a different Desktop version of Ubuntu, but it may work, using the alternate cd:
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

As with any upgrade, there's always a chance it will fail, so you might want to backup any important files.

---

### Post by src2206 on 2007-12-02
Thanks very much... :)

I'll give it a try and post the feedback here.

---

### Post by src2206 on 2007-12-03
Ok, here is the update:

As I put the CD in the drive Ubuntu 7.04's package manager recognized it as an update and asked me whether I want to upgrade. As I agreed, Ubuntu was upgraded without any problem to **Ubuntu 7.10, not to Edubuntu 7.10 **as I would have liked.

So should I follow Post #4 to install packages from Edubuntu as well as Edubuntu Desktop?

---

### Post by confused57 on 2007-12-04
> **src2206 said:**
> Ok, here is the update:

As I put the CD in the drive Ubuntu 7.04's package manager recognized it as an update and asked me whether I want to upgrade. As I agreed, Ubuntu was upgraded without any problem to **Ubuntu 7.10, not to Edubuntu 7.10 **as I would have liked.

So should I follow Post #4 to install packages from Edubuntu as well as Edubuntu Desktop?

I thought that may happen, but glad you successfully upgraded to 7.10.  Yes, you could use the instructions from post #4 to install the edubuntu-desktop...if you don't have a fast internet connection, you could possibly use the Edubuntu alternate cd as a repository source.

---

### Post by src2206 on 2007-12-05
> you could possibly use the Edubuntu alternate cd as a repository source.You mean as a source for softwares- right? Do I need to manually add the disc to Synaptic Package Manager? BTW, I need to upgrade Automatix too.
One more thing, will the commands posted in Post #4 install all the packages available in the Edubuntu CD?

---

### Post by confused57 on 2007-12-05
> **src2206 said:**
> You mean as a source for softwares- right? Do I need to manually add the disc to Synaptic Package Manager? BTW, I need to upgrade Automatix too.
One more thing, will the commands posted in Post #4 install all the packages available in the Edubuntu CD?
Here's how to add the edubuntu alternate cd to your sources.list(if it isn't already listed):
[http://ubuntu-tutorials.com/2007/01/09/manually-adding-a-cdrom-to-your-repositories-ubuntu-610/](http://ubuntu-tutorials.com/2007/01/09/manually-adding-a-cdrom-to-your-repositories-ubuntu-610/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adding_a_CD-ROM_or_DVD_repository](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adding_a_CD-ROM_or_DVD_repository)
You would insert the edubuntu alternate cd, then add it from synaptic or from the terminal:
```
sudo apt-cdrom add
```

You can check your sources.list to see if the edubuntu alternate cd is already listed:
```
gedit /etc/apt/sources.list
```
if it's listed, make sure it's not commented out(has a # in front of).

If you have a relatively fast internet connection, then you can follow the instructions in post #4...if you don't, you can probably omit the update and upgrade, for now?

For Automatix, might be a good idea to uninstall your current version(Feisty 7.04), remove any references to it in your sources.list...then go to getautomatix.com & install Automatix2 for Gutsy 7.10...see the getautomatix.com website for instructions on uninstalling automatix.

If for some reason aptitude install doesn't want to cooperate, you can try:
```
sudo apt-get install edubuntu-desktop
```

---

### Post by src2206 on 2007-12-05
Thank you very much mate, I shall let you know the result as soon as I try out all the resources you have kindly provided.

---

### Post by src2206 on 2007-12-12
Hello confused57

Sorry for this delayed response. Well I have installed Edubuntu afresh 'cause I was unable to locate the application suited to be installed from this flavor of Ubuntu.

To my utter surprise, even after a fresh installation, none of the educational software seems to have been installed from the Edubuntu CD I got from ShipIt! I have added the CD as a repo to the Synaptic package manager and I can see the available packages in the Synaptic Window. But I have no idea which are the softwares I am looking for as the names are mostly generic in nature.

**So how exactly can I add the Educational Softwares that is supposed to be present on the Edubuntu CD?** This is important for me because I am planing to use this Edubuntu in my school too.

Please help me out. :(

---

### Post by confused57 on 2007-12-12
You might want to check out the add-on cd  for 7.10:
[http://www.edubuntu.org/UsingAddOnCd](http://www.edubuntu.org/UsingAddOnCd)

---

### Post by src2206 on 2007-12-12
> **confused57 said:**
> You might want to check out the add-on cd  for 7.10:
[http://www.edubuntu.org/UsingAddOnCd](http://www.edubuntu.org/UsingAddOnCd)

Thank you my friend, you have been of great help. :)

So does it mean that the main installation CD does not contain any Specific Educational Applications. :?:

---

### Post by confused57 on 2007-12-12
> **src2206 said:**
> Thank you my friend, you have been of great help. :)

So does it mean that the main installation CD does not contain any Specific Educational Applications. :?:
I set up an old computer for my wife's nephew with Edubuntu  6.06.1, which had quite a few educational tools & games for various age groups.  I was unaware that an extra add-on cd was required for 7.04 & later:
> With each new release Edubuntu provides more great educational programs and classroom server features. As of the 7.04 (Feisty Fawn) release, Edubuntu no longer fits on a single CD. The classroom server add-on CD was introduced to allow users to install additional applications and language packs that do not fit on the installation CDs.

Some of these threads may give you some idea of the educational tools & games Edubuntu offers:
[http://ubuntuforums.org/search.php?searchid=32928954](http://ubuntuforums.org/search.php?searchid=32928954)

---

### Post by src2206 on 2007-12-13
Thank you so very much confused57 :)
You have been of great help.
I shall go through the threads you have provided and I shall post the feedback here.

---

