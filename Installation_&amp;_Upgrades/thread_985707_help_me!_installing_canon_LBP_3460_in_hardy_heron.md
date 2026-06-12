---
title: "help me! installing canon LBP 3460 in hardy heron"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by icejack_outlaw on 2008-11-17
hai all.....im newbee in ubuntu....i hope somebody help and guide me how to install Canon LBP3460 in hardy heron.... i just downloaded the rpm file... but dont know to use it.... can any body help me....please:(

---

### Post by Partyboi2 on 2008-11-17
Open a terminal (Applications>Accessories>Terminal) and installing alien which is a program that converts rpm to debs.
In the terminal type
```
sudo apt-get install alien
``` Once it has installed change directory to where the downloaded file is, so if its on your Desktop
```
cd ~/Desktop
``` then convert it
```
sudo alien -d file name
``` Change file name to actually name of downloaded file. Once it has made the deb package you can install with
```
sudo dpkg -i package
``` change package here to actually name of the deb package that was created.

---

### Post by icejack_outlaw on 2008-11-17
thanks bro..... i get it now.... im will do it rite now... if any thing happen... ill ask u agin ok... thanks alot bro...

---

### Post by icejack_outlaw on 2008-11-18
partyboi bro..... when i try to install alien like u said.... the terminal appear this message >>>>

[Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libcarp-clan-perl lesstif2 libnumber-compare-perl
  libbit-vector-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.]

 so what i want to do now???

---

### Post by Partyboi2 on 2008-11-18
It means that you already have alien installed so move onto changing directory to where the download file is.

---

