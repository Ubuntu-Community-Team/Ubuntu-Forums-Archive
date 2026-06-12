---
title: "openshot upgrade error"
date: 2019-11-23
forum: Installation &amp; Upgrades
---

### Post by iamtheeggman2 on 2019-11-23
Hi,

Can anyone please advise? I wanted to try installing a video editor called open shot, however got the below message in both software and synaptic package manager:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/imagemagick/libimage-magick-q16-perl_6.9.7.4+dfsg-16ubuntu6.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/imagemagick/libimage-magick-q16-perl_6.9.7.4+dfsg-16ubuntu6.7_i386.deb)
  404  Not Found [IP: 2001:67c:1560:8001::14 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/imagemagick/libimage-magick-perl_6.9.7.4+dfsg-16ubuntu6.7_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/imagemagick/libimage-magick-perl_6.9.7.4+dfsg-16ubuntu6.7_all.deb)
  404  Not Found [IP: 2001:67c:1560:8001::14 80]

---

### Post by CatKiller on 2019-11-23
Run an *apt update*. The version that it's looking for has been superseded and replaced with a newer one.

---

### Post by iamtheeggman2 on 2019-11-23
I've used the one in windows now. however although i just did he above command, i did have an updated system according to the system updates program??????

---

### Post by deadflowr on 2019-11-23
It should be version libimage-magick-q16-perl-6.9.7.4+dfsg-16ubuntu6.8
Your's is somehow stuck at libimage-magick-q16-perl-6.9.7.4+dfsg-16ubuntu6.7

Are -updates and -security still shown in the apt update command listings, or in the /etc/apt/sources.list file?
The package is in the bionic-updates universe repository.

---

### Post by Impavidus on 2019-11-24
The update manager tells you that the system is fully up-to-date whenever all upgrades that it knows of have been installed. **apt update** checks for available upgrades and makes the upgrade manager aware of the latest upgrades. It runs automatically every day, week, two weeks or never, depending on how your system has been configured. When a package has been upgraded in the repositories after your computer has last checked for available upgrades, the version your computer expects to find may no longer be there.

---

### Post by iamtheeggman2 on 2019-11-24
Hi,

Assuming I can get it installed, do you think it would open up project files made In windows 10? I have spent some decent time doing a project in windows however for some strange reason it keeps on crashing. 

I will have to look into the updates issue tomorrow.

---

