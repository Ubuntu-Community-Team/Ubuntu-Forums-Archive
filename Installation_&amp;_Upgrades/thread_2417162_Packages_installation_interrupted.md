---
title: "Packages installation interrupted"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by learnlinux95 on 2019-04-21
Hi everyone, I'm new to Linux.

Recently, i tried to install LATEX. For the first step:
```
sudo apt-get install texlive-full
```

It showed 293 newly installed and I press [yes]. It stared to download packages.

Unfortunately,after downloading over a hundred of packages,my internet connection went down for a while, the terminal reported that it can not fetch and then it stop.

My question is:

[LIST=1]
[*]how can i continue the installation? 
[*]if not, when i restart the installation do i need to clear out the last interrupted download packages?
[/LIST]

---

### Post by Impavidus on 2019-04-22
I haven't encountered that problem myself in about 12 years, but I think you can just try again:```
sudo apt install texlive-full
```apt should automatically see where it was stopped. There shouldn't be any partially installed packages, as the operation was interrupted during the download phase.

---

### Post by learnlinux95 on 2019-04-23
Thanks for your answer. I've just migrated from Windows to Ubuntu. Just don't want to mess thing up!

---

