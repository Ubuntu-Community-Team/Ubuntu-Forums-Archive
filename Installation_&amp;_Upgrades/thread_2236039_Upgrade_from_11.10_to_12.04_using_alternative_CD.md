---
title: "Upgrade from 11.10 to 12.04 using alternative CD"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by tiger2000 on 2014-07-24
Hello 

I decided (finally  !!) upgrade from 11.10 to 12.04. But, I have to consider that I use LVM with  encrypted disks and I found 
a question about issues during upgrade.
[http://askubuntu.com/questions/139401/failed-upgrade-from-11-10-to-12-04-on-an-encrypted-filesystem](http://askubuntu.com/questions/139401/failed-upgrade-from-11-10-to-12-04-on-an-encrypted-filesystem).
It seems , per the link, that I would be able to solve the issues.. however, I am not sure and I really do not want to spend a week to do upgrade without access to my data.

So, my guess is that I can upgrade from alternative CD - 12.04.4.
My questions are : 
1) Am I able to upgrade using the alternative CD ? (My guess is that the installation process is able to identify that the computer (desktop) already has a Linux installation and
can suggest me to only upgrade, but I am not sure).
Please , provide comments

2) If I decide install from scratch, should I be able to keep my LVM untouched , at least /home ? 


thanks in advance

---

### Post by sudodus on 2014-07-24
I'm afraid it makes it harder to succeed upgrading with LVM and  encrypted disks. So it is very important that you ***make a cloned copy*** (full copy or compressed image) of your present 11.10 system ***or at the very least backup all personal data*** (pictures, documents ...).

---

