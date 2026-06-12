---
title: "[SOLVED] update manager gone crazy!!"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by cespinal on 2008-08-21
hello to all

just need advice on how to fix this: 

there is a yellow warning sign in my upper panel's notification area. I click on it, opens the update manager, it says that my system is up date. Then I click on check and it starts to retrieve like 70 packege information items.. and then: 

W: Failed to fetch [http://les-ejk.cz/ubuntu/dists/hardy/Release.gpg](http://les-ejk.cz/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'les-ejk.cz'

W: Failed to fetch [http://les-ejk.cz/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://les-ejk.cz/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'les-ejk.cz'

W: Some index files failed to download, they have been ignored, or old ones used instead.

and this is it.. im not able to make any updates since 10 days ago.. 

any hints?

---

### Post by Pumalite on 2008-08-21
Put a # in front of this line in your /etc/apt/sources.list:
'http://les-ejk.cz/ubuntu/dists/hardy...tion-en_US.bz2'

---

### Post by DavidTangye on 2008-08-21
> **cespinal said:**
> http://les-ejk.cz/ubuntu/dists/hardy/Release.gpg[/URL]  Could not resolve 'les-ejk.cz'

W: Failed to fetch [http://les-ejk.cz/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://les-ejk.cz/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'les-ejk.cz' Remove or comment out these lines from /etc/apt/sources.list. This can be done from synaptic, the package manager, (menu System, Administration, Synaptic, then its menu Settings, Repositories, 'Third Party Software' tab). 

You might want to find out how you got to have these repositories in your list in the first place.

---

### Post by developer on 2008-08-21
I recieve the following error message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.4.1-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.4.1-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]
 I can't update my system!!

---

### Post by Pumalite on 2008-08-21
Try changing Server

---

