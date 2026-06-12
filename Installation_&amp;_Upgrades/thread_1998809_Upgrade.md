---
title: "Upgrade"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by groeswenphil on 2012-06-07
Hi group,

I've an Acer Aspire netbook which I believe is currently running UNR 9.04
I believe that there is a LTS release available but can't find an obvious way to upgrade.
Any suggestions,
Phil

---

### Post by snowpine on 2012-06-07
If you are running 9.04 then my recommendation is to back up your data and do a fresh reinstall of 12.04 LTS. (But test-drive the Live CD first.) There have been **massive** changes to Ubuntu in the past 3 years.

---

### Post by dino99 on 2012-06-07
you can upgrade by many ways, but there are some rules:  
- upgrading is available from previous to next, and from LTS to Lts  
- by the commanf: sudo do-upgrade -p 
- or by changing the release into sources.list :      gksu gedit /etc/apt/sources.list
- or by doing a fresh install : formatting / only and re-using /home & /swap

---

### Post by groeswenphil on 2012-06-07
I think I'll opt for the new install.

I was using Ubuntu Netbook Remix.
Do I just need the standard Ubuntu now?

Phil

---

### Post by snowpine on 2012-06-07
Ubuntu Netbook no longer exists as a separate entity; the current Unity interface is designed to work equally well on netbook, desktop, laptop, tablet, etc. :)

Also there are Lubuntu, Xubuntu, Kubuntu (different desktop environments).

---

