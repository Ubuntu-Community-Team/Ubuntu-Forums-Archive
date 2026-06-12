---
title: "Upgrading to New Versions of Ubuntu"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by FerretDefunct on 2010-02-05
I'm an Ubuntu newbie and recently decided to install it as the OS for my netbook. I believe that new releases of Ubuntu come out every six months or so and I'm curious as to how easy it is to upgrade. As a long time Windows user I'm used to "Clean install = the way to go" when it comes to updated releases, I'd like to know if this philosophy holds true in Ubuntu. 

Assuming it does, and clean installs are preferred I'd like to know how much of a headache installing a clean new release is, and how much data I'll lose. For instance will I need to reinstall all of my applications as I would with Windows? Will I need to completely re-customize the OS, starting from scratch? I installed Ubuntu keeping partition separate from the rest to store data (music, movies, etc.), I'm assuming that I can leave that untouched when reinstalling?

In short I'd just appreciate it if anybody could give me a brief idea of what to expect when moving to a new release of Ubuntu. Thanks for any help you all can throw my way.

---

### Post by llawwehttam on 2010-02-05
If you have a separate partition for /home then you will be able to keep your personal settings but still do a clean install.

I always prefer to do it this way as you don't get so many problems.
But if your willing to do a few fixes but want to keep all your programs then you run 

```
sudo apt-get update; sudo apt-get upgrade ; sudo apt-get dist-upgrade
```

in terminal and that will update you to the latest version.

---

### Post by cantormath on 2010-02-05
You have two options for version upgrades.  

1)
You can backup your system and do a clean install. (recommend).

2)
You can also do a version upgrade.  If you are using a LTS verion, i.e., hardy, you will not be prompted by the update manager to upgrade to the next version of ubuntu, say ibex.  

A Karmic upgrade howto
[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

Upgrade to hardy
[https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%207.10%20to%208.04%20LTS]("https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%207.10%20to%208.04%20LTS")

It is good to look for instructions that are specific to the version you are starting with and the version you want to end up with.  It is important to note that direct upgrades from one version to another, say Dapper to Karmic, are not always possible.  You often have to upgrade one version at a time.  

Another thing, I usually do a fresh install if I can.  Upgrading can sometimes cause issues.  I will say that the last three machines I have upgrade have not had noticeable issues.  The upgrade feature in ubuntu is getting much better.  I recently upgraded ubuntu server to karmic from hardy without any issue.  I have also upgrade ibex to karmic with out an issue.  Upgrade at your own risk.

> **llawwehttam said:**
> If you have a separate partition for /home then you will be able to keep your personal settings but still do a clean install.

I always prefer to do it this way as you don't get so many problems.
But if your willing to do a few fixes but want to keep all your programs then you run 


Keeping your home directory on a separate partition only saves your program settings.  This is a good idea if you want to reinstall the same version, but if you just install a new version of ubuntu with your old home folder, there is a chance that the programs you used will  be newer versions after the upgrade and this may cause problems.  It is worth a shot if you can take the risk.  Keeping your home directory on a separate partition is a good method to practice but can require some tweaking during upgrades.

---

