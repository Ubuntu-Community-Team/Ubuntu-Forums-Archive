---
title: "Install &quot;ubuntu-desktop&quot; on ubuntu server edition"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by linlay on 2007-11-02
Hi
I have ubuntu Server Edition on a Sun Sparc machine.
I want to install GNOME, on the server, so I run the following command. But no package is found. Any HELP plz?  Thanks!

linlay@proddev:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "ubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by arkara on 2007-11-02
the most possible is that ubuntu server is using different repositories, from the ubuntu deskotp edition so you won't be able to install ubuntu-desktop.
if you go on a kubuntu-desktop system and type the same command then you will get ubuntu-desktop also.

---

### Post by linlay on 2007-11-02
what do you meant go on a kubuntu-desktop first ?

The ubuntu server edition doesnt have any GUI at all ..no Gnome no KDE ...so i'm trying to install Gnome now :(

I searched the forum, and some other people said to do the apt-get install ubuntu-desktop .... but why mine doesnt work ?

---

### Post by Mimou on 2007-11-02
Did you try with apt-get install gnome?

Edit : Can you post your sources.list :)

---

### Post by az on 2007-11-02
Make sure that you are connected to the internet and enable the main and restricted repositories in your sources.list.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by arkara on 2007-11-02
> **linlay said:**
> what do you meant go on a kubuntu-desktop first ?

The ubuntu server edition doesnt have any GUI at all ..no Gnome no KDE ...so i'm trying to install Gnome now :(

I searched the forum, and some other people said to do the apt-get install ubuntu-desktop .... but why mine doesnt work ?

i meant if you do this on a pc running the kubuntu desktop edition.
 and about the apt-get install ubuntu-desktop. as i told you this command was given from desktop editions.
so if the server edition does not use the same repos as the desktop edition then it is very logical that your pc cannot find the packages needed because the packages are just not there

---

### Post by sillv0r on 2007-11-03
> **arkara said:**
> ...if the server edition does not use the same repos as the desktop edition then it is very logical that your pc cannot find the packages needed because the packages are just not there

I believe the repository list is changable.  So if this is the case, then a simple edit on the sources list will allow your apt-get to see the package.

> **Seisen said:**
> ...you manually edit you /etc/apt/sources.list or you if add or remove repositories in Software Sources.

---

### Post by linlay on 2007-11-04
Hi guys
Yeah there was a problem in my sources.list ...i've edited it ..and now i can install the 'ubuntu-desktop' 

Thanks!

---

