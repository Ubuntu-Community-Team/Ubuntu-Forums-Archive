---
title: "[SOLVED] 2 issues"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by lukydude on 2008-05-29
1) i cant install flash

2) should i upgrade to 8.04lts ubuntu or is it too bugy? i heard lots of people have trouble with it.

---

### Post by xfceuser on 2008-05-29
2) there are some important updates in 8.04 . but you might see, if your current version works perfectly, you can stay with it.
the best thing is to try the new version (8.04),  if it is working ok on your particular system then it is the best.

---

### Post by xfceuser on 2008-05-29
1) flash you can install by going to System menu -> add/remove programs
search for flash, take care to have chosen "all available applications" then check "macromedia flash plugin" for installation

---

### Post by lukydude on 2008-05-29
ok thanks

---

### Post by lukydude on 2008-05-29
how do i customize sound levels? ive tried but its always max

---

### Post by xfceuser on 2008-05-29
type in a terminal 
gnome-alsamixer

---

### Post by lukydude on 2008-05-30
where and what is gnome... how do i access it? and i'm upgrade to 8.04LTS now!

---

### Post by lukydude on 2008-05-30
i used the command it didn't work look at screen shot.

---

### Post by lukydude on 2008-05-30
when im the onlt user on my pc this makes no sense:

luke@luke-desktop-ubuntu:~$ gnome-alasmixer
bash: gnome-alasmixer: command not found
luke@luke-desktop-ubuntu:~$ gnome-alsamixer
The program 'gnome-alsamixer' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-alsamixer
bash: gnome-alsamixer: command not found
luke@luke-desktop-ubuntu:~$ apt-get install gnome-alsamixer
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
luke@luke-desktop-ubuntu:~$ apt-get install gnome-a;samixer
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bash: samixer: command not found
luke@luke-desktop-ubuntu:~$

---

### Post by lukydude on 2008-05-30
furhter help??

---

### Post by xfceuser on 2008-05-30
you should type:
sudo apt-get install gnome-alsamixer

---

### Post by lukydude on 2008-05-30
ok its working now but i dont get it (attached) is orange bar down or up or??.... ahh!!

---

### Post by xfceuser on 2008-05-30
the upper you bring the slider, the higher is the volume.

---

### Post by lukydude on 2008-05-30
thank you, also im wondring what other programs and things i can do with ubuntu

---

### Post by NetworkGuy on 2008-05-30
> **lukydude said:**
> when im the onlt user on my pc this makes no sense:

luke@luke-desktop-ubuntu:~$ gnome-alasmixer
bash: gnome-alasmixer: command not found
luke@luke-desktop-ubuntu:~$ gnome-alsamixer
The program 'gnome-alsamixer' is currently not installed.  You can install it by typing:
**sudo apt-get install gnome-alsamixer**
bash: gnome-alsamixer: command not found
luke@luke-desktop-ubuntu:~$ apt-get install gnome-alsamixer
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
luke@luke-desktop-ubuntu:~$ apt-get install gnome-a;samixer
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bash: samixer: command not found
luke@luke-desktop-ubuntu:~$

You missed the sudo at the start of your apt-get command

---

### Post by xfceuser on 2008-05-30
you can do with ubuntu everything that you can do with linux in general.
a list of programs with their description is in the add/remove section.
also there are more programs on internet to install. it depend what you are interested ...

---

### Post by lukydude on 2008-05-30
thanks well ive never used linux before lol

---

### Post by lukydude on 2008-05-30
couple more things:

is it possible to resize the ubuntu partiion without corrupting it?

can you dual boot kubuntu with ubuntu and xp pro?

---

### Post by xfceuser on 2008-05-30
for sure you can make kubuntu and ubuntu and ... multi-boot
you can install gparted,
sudo apt-get install gparted
and see if it has an option to resize ubuntu partition.
but i remember your ubuntu partition was already minimum, so maybe you should not make it smaller. but you can still make windows partition smaller.

---

### Post by lukydude on 2008-05-30
> **xfceuser said:**
> for sure you can make kubuntu and ubuntu and ... multi-boot
you can install gparted,
sudo apt-get install gparted
and see if it has an option to resize ubuntu partition.
but i remember your ubuntu partition was already minimum, so maybe you should not make it smaller. but you can still make windows partition smaller.

i want ubuntu bigger the others smaller is that possible?

---

### Post by lukydude on 2008-05-30
well?

---

### Post by xfceuser on 2008-05-30
Kubuntu is just the Ubuntu core with KDE desktop environment , originally Ubuntu uses Gnome. So if you like try Kubuntu, you can just install KDE (that I dont know exactly how, but must be on archive surely) this will save a lot disk space for you. also you will have choice to choose Gnome or KDE at the login.
just a tip: be a bit cautious with resizing etc. the partitions.
it is always advised everywhere that you backup anything important on your disks.

---

