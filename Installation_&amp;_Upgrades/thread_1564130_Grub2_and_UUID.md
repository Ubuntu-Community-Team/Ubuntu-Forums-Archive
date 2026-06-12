---
title: "Grub2 and UUID"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by seb2020 on 2010-08-30
Hi everybody,

I have a question : I use ubuntu 10.4. I have two partition. One fort Windows XP and one fort ubuntu. I do not want to use UUID in my grub.cfg

How I can make that ?

Thanks !

---

### Post by oldfred on 2010-08-30
Why?

UUID's are the more reliable way to know which partition you are booting. Grub's menu actually use hdX,Y as the default and then a search on drive by UUID.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by seb2020 on 2010-09-01
Yes, but I use a sort of ghost ([http://en.wikipedia.org/wiki/Ghost_%28software%29](http://en.wikipedia.org/wiki/Ghost_%28software%29)) 

So, when I redeploy my image on a new computer, the UUID change ! I do not want to reinstall Grub on every computer. Have you got a solution for that ?

I have a partition fort windows and an other for linux

---

### Post by dino99 on 2010-09-01
reinstalling grub-pc is very easy (uuids are the default)

but look at link below to use labels

[http://www.google.fr/search?as_q=grub2%2Blabel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=grub2%2Blabel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by seb2020 on 2010-09-01
[CENTER][LEFT]I have resolve my problem by decomenting [I][B]#GRUB_DISABLE_LINUX_UUID="true" 

and regenerating the grub config file[/B][/I]

Thanks
[/LEFT]
[/CENTER]

---

