---
title: "Late to the partay: upgrading to Kubuntu Edgy Eft (apt-get necessary?)"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Chake99 on 2007-02-21
I'm finally deciding to do the fateful upgrade to edgy however when I type the graphical command I get > bash: gksu: command not found

The kubuntu page does not mention the graphical update method, [http://www.kubuntu.org/announcements/6.10-release.php](http://www.kubuntu.org/announcements/6.10-release.php) , but the xubuntu page states that the graphical method works for all versions but it (lost page). 

I don't want to bork my system though, so I'm hesitant to apt-get unless necessary since it has been stated to be hacky. I've already updated my sources.list I'm just awaiting some confirmation.

Or is there someway to get the graphical upgrade to work?

---

### Post by angryfirelord on 2007-02-21
If you've switched the sources to edgy, all you have to go is a **sudo apt-get upgrade** & **sudo apt-get dist-upgrade**.

HOWEVER, I don't recommending getting edgy this way. I've read more stories about it breaking than succeeding. If you want edgy, doing a fresh install is the best way.

Personally, I liked dapper more than edgy so I'm sticking with dapper.

---

### Post by Chake99 on 2007-02-21
but I want to keep my stuff... I backed up the partition, so if it fails I'll simply restore it. Thankyou.

---

### Post by Kateikyoushi on 2007-02-21
The ubuntu docs recommend upgrading via the update manager. [LINK]("https://help.ubuntu.com/community/EdgyUpgrades")
I did myself and everything worked out fine but when edgy rolled out there were many for whom transition was not easy.

In my opinion you have nothing to lose if you have backup.

---

