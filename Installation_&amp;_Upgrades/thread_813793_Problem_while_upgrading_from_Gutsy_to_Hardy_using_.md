---
title: "Problem while upgrading from Gutsy to Hardy using upgrade manager"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by vvinuv on 2008-05-31
Hi All
I am trying to upgrade from Gutsy to Hardy. I followed the instructions and used upgrade manager. I checked for new updates and installed them. But I could not see any message informing me of the availability of the new release. What is going wrong?
Thanks
Vinu V.

---

### Post by abhiroopb on 2008-05-31
go to system>administration>update manager and click on "Upgrade" where it says New distribution release...

---

### Post by vvinuv on 2008-06-01
Hi 
I could get that message by pressing Alt-F2 and then by the command
*gksu &#8220;update-manager -d&#8221;*

---

### Post by Bubba64 on 2008-06-01
Just make sure your updated in Gutsy before you upgrade, or that is what I see posted all the time.

---

### Post by gnr on 2008-06-03
hi, avoiding some of these patronising replies. I had the same problem.

gksudo gedit /etc/apt/sources.list
change every word gutsy to hardy (be sure to leave the # in front of cd) and save
sudo apt-get update
sudo apt-get dist-upgrade

---

