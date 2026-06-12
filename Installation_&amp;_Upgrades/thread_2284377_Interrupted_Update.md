---
title: "Interrupted Update"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by wabbit46 on 2015-06-29
I am running Ubuntu 14.04. I started to install updates amounting to about 300MB. The installation was proceeding very slowly. At approximately one third of the way through I stopped the updates intending to install them later.

When I subsequently tried to complete the updates I received the message that the computer was up to date.

I tried using the terminal command **sudo apt-get updates** and received a list of packages to be updated. When I typed in the command **sudo apt-get upgrade** it said that it needed to get 7008 kB  of archives. I would like to get the computer up to date. 

How can I get the computer to download the 200 MB of data it previously thought needed updating?

---

### Post by westie457 on 2015-06-29
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Should get things sorted for you.
The last command is only necessary if some packages are held back. Also it will not upgrade to a newer release eg. 14.04 to 14.10

---

### Post by grahammechanical on 2015-06-29
Did you continue the second time with the update? As far as I can tell there are three parts to updating/upgrading.

1) downloading the package lists so the system can work out what packages can be upgraded. This is done when we run apt-get update.
2) download the packages that have been upgraded to replace existing packages that can be upgraded.
3) Install all upgraded and downloaded packages by removing existing packages and replacing them with the upgraded versions.

2 & 3 are done by the apt-upgrade command but all the packages have to be downloaded before the installing takes place. It is not unknown for packages to be downloaded but not installed because they depend on upgraded packages not yet in repositories. So, you might find that the packages you think are missing have actually been downloaded but not installed because you stopped the upgrade process.

Depending on the data transfer rate of our internet link the download part can be fast in comparison with the installing part. The most time consuming part of update/upgrade is not the downloading of the packages but the installing of them.

Regards.

---

### Post by wabbit46 on 2015-07-03
> **westie457 said:**
> ```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Should get things sorted for you.
The last command is only necessary if some packages are held back. Also it will not upgrade to a newer release eg. 14.04 to 14.10

I tried all these commands it still showed only 7MB of archives to be retrieved and updated very quickly. I assume that this is a far as I can go. Thank you for your assistance.

---

