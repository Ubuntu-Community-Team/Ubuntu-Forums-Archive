---
title: "getting add/remove to use a cd"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by dorhelp on 2006-10-16
I have tried copying my /var/cache/apt folder to a CD so I can use it to load updates to other computers without having to download the files. I have tried just coping the folder, just the files in the archive, the contents of the apt folder. No matter what I do I get unable to load package list perhaps this is not debian. Any ideas on what I am doing wrong.
                   Thanks
                   Linda

---

### Post by aysiu on 2006-10-16
Repository CDs are not just a collection of .deb files. They have a uniform structure and an index of what files are contained within the repository.

If you know you want to install *all* the programs you've copied over (not just some of them), just put them  on the desktop of the new computer and paste these two commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` If you want to create a proper repository CD, follow these instructions:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

