---
title: "can't install anything"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Warstrong on 2006-12-10
I have trouble installing anything because my comp with the latest Xubuntu doesn't have internet connection.  Any way i can install programs like unrar and other things without an internet connection?  The only way i currently know how to install things is with the terminal where you type in sudo apt-get and then the name of the program.  But i don't have an internet connection so it says that the package couldnt be found or whatever.  Any other way of installing things??? thx:-#

---

### Post by wpshooter on 2006-12-10
Probably could download the material from some other machine that had internet connection and then transfer to your via CD or something, but IMO would be more trouble than it would be worth.

Why do you NOT have internet connection ?

A computer these days that does not have an internet connection (especially if it is using Ubuntu) is not hitting on much !!!

---

### Post by jpkotta on 2006-12-10
Get the DVD, it has all of the packages in the official repos (but not universe and multiverse, I think).  unrar is not on the DVD though.  You can download individual packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), and install with ```
sudo dpkg -i packagename.deb
```  This can get very tedious if you have a bunch of dependencies (I don't think unrar has any).  Ubuntu can be a pain without internet.

DVD page: [http://www.ubuntu.com/products/GetUbuntu/download](http://www.ubuntu.com/products/GetUbuntu/download)

---

### Post by gborzi on 2006-12-10
You have two alternatives:
1) If you have access to a fast internet connection in your local school/university/library, you can download the DVDs with all the packages from here [http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en). Once you get the DVDs open synaptic and go to Edit->Add CDROM and add them (or use apt-cdrom).
2) In case 1) can't work for you, open synaptic, select the packages you need and instead of clicking apply, go to File->Generate Packages download script. Bring the script to a computer connected to internet (and equipped with wget), execute it, put the packages somewhere (e.g. an usb storage device), bring them to your computer and install them with > sudo dpkg -i *.deb
Hope this helps.

---

