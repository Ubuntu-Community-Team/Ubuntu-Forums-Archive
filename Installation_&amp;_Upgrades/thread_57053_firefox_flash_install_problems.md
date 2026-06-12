---
title: "firefox flash install problems"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by ShagzModo on 2005-08-15
Hi there... 
I installed hoary 5.0.4 on intel x86.
After installation i enabled root, Added extra repositories for apt-get; and upgraded firefox to version 1.0.6. What i want to install in macromedia flash for firefox, i can't download this plug in or get it installed with apt-get command sudo-apt-get install 

Does anyone have the same problem?

How do i get this flash to work?

thnx
Paul Amsterdam
(ShagzModo)

---

### Post by manicka on 2005-08-15
flashplayer-mozilla is in the multiverse repo.

check that multiverse is enabled in your /etc/apt/sources.list

---

### Post by ShagzModo on 2005-08-16
[QUOTE=manicka]flashplayer-mozilla is in the multiverse repo.

check that multiverse is enabled in your /etc/apt/sources.list[/QUOTE]
 i edited sources.list with multiverse repositories and backports info, still it gave package not found. I even edited my firefox version to 1.0.4 as told in other posting (did not solve anything) After this i decided to download the flashplayer from the macromedia site and i installed it without any problems by following the installation instructions... I still have my doubts about the backports i added in sources.list. Anyway i solved my problem, and i now have everything working fine.

Best regards, and thnx for the help.

Paul

---

