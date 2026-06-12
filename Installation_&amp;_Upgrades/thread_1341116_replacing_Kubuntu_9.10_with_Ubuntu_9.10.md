---
title: "replacing Kubuntu 9.10 with Ubuntu 9.10"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by baiguai on 2009-11-29
I have Kubu 9.10 installed on my machine, but it has filled up my little hdd and I have barely any apps installed yet. I was going to go back to Ubu 9.10 until I get a bigger drive, but when I install Ubu (not in 'live cd mode') it still boots to Kubu as though nothing had happened. I am telling the installer to use the hdd that has my OS on it, and telling it to use the whole drive, but after my supposed installation the same amt of space is taken up on the drive and Ubu is no where to be seen.
How can I SAFELY clear out everything on this drive so I can get a clean, fresh Ubu 9.10 installation?

thanks in advance!

---

### Post by zvacet on 2009-11-29
I think that Kubuntu and Ubuntu are about same size,but if you want to install Ubuntu on top of Kubuntu use manual way for installation.Delete all partitions you have and then install Ubuntu.What is size of your HD?For minimal install you need 5GB of free space (maybe even less but you can not install apps later).Maybe give more info of your HD and then you can get better advice.

---

### Post by mikeac72 on 2009-11-29
Well, here's a code to install ubuntu but keep all your apps.

Go to Konsole:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
```
If you want to do a clean install, boot from the LiveCD, and Try Ubuntu.
Navigate your way to GParted, I think it is in Apps>accesories or System>Admin.
Select your disk and format it.
Go back to the desktop, click install ubuntu, and follow the prompts.

---

