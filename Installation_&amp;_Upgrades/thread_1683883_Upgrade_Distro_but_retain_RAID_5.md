---
title: "Upgrade Distro but retain RAID 5"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by tootlet on 2011-02-08
Greetings,
I use a server with 1 hard drive for the OS and 3 hard drives in RAID 5 for my important files. I use mdadm to administer the RAID and it is mounted as md0. I want to know how I can change the OS on the boot hard drive then mount md0 on this new OS without losing files on the RAID 5. I change between Ubuntu, Xubuntu and Lubuntu. I currently have one of my servers with openSUSE that is giving me problems and want to put an Ubuntu variant on it without losing the data on the RAID 5. 

Here are the steps I think I should take. 
Install OS on sda and update.
install mdadm.
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
make a mounting point

Here's where I'm confused. Since this was already a RAID 5 system do I have to make a file system? Can I just mount it? How do I edit mdadm.conf to show what I have? 

Any pointers appreciated. I would just try it but I'm afraid to lose my data! Thanks.

Tom

---

