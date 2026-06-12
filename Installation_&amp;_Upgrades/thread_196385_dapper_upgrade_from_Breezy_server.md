---
title: "dapper upgrade from Breezy server"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Compact on 2006-06-14
I have read this [guide]("https://wiki.ubuntu.com/DapperUpgrades") to know how to upgrade Breezy to Dapper. I have installed Breezy with the server edition so there is no desktop installed (like GNOME, KDE...) and in the upgrade guide i can read 
> 
1. Make sure that you have ubuntu-desktop, kubuntu-desktop, or edubuntu-desktop installed (depending on which distribution you are using). This is vital for apt to perform the **upgrade** successfully.


What I have to do to upgrade the breezy to dapper?

---

### Post by localzuk on 2006-06-14
I think that guide is talking about upgrading for those who have a desktop. All you need to do is edit the /etc/apt/sources.list file, changing all the breezy references to dapper followed by an apt-get update and an apt-get dist-upgrade

---

