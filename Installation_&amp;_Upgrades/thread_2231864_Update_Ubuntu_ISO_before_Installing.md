---
title: "Update Ubuntu ISO before Installing"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by TJSL on 2014-06-28
Is it possible to update an Ubuntu ISO before installing it so that it is not necessary to download and install updates after a fresh Ubuntu install? I am playing around with configurations (reinstalling frequently) and the 400MB update download is taking a significant amount of time (and hammering the Ubuntu servers more than necessary). Ideally, I would like to be able to click one button and have a USB boot image created that is ready to go without the need for further updates. How can this be done?

---

### Post by ibjsb4 on 2014-06-28
Not an option with the iso that I know of.  You could create a backup or clone of your updated install.

---

### Post by LukeMorrison on 2014-06-28
You can also use the mini.iso which will pull down the latest packages during the install.  It is ncurses based, but I use it for my main installs.  

archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso for 32-bit
archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso for 64-bit

---

### Post by ibjsb4 on 2014-06-28
> **LukeMorrison said:**
> You can also use the mini.iso which will pull down the latest packages during the install.  It is ncurses based, but I use it for my main installs.  

archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso for 32-bit
archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso for 64-bit
I don't know about the netboot mini, but you reminded me of the remix mini.

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

There is a learning curve with this and some will not want to deal with.

---

### Post by TJSL on 2014-06-28
The objective would be to download all packages once, no matter how many times the iso is installed. If I understand you correctly, the same packages would have to be downloaded for every subsequent new install.

---

### Post by TJSL on 2014-06-28
> **LukeMorrison said:**
> You can also use the mini.iso which will pull down the latest packages during the install.  It is ncurses based, but I use it for my main installs.  

The objective would be to download all packages once, no matter how many  times the iso is installed. If I understand you correctly, the same  packages would have to be downloaded for every subsequent new install.

---

### Post by grahammechanical on 2014-06-28
Don't tick to install updates during installation, if all you are doing is experimenting with setups. You might want to look at this.

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

Ubuntu 14.04 will receive 5 point releases in the next two years. That is when the release ISO image is re-built to include all the updates that came out in between. And it is why 14.04 Trusty Tahr is still getting a daily image. The latest is 20140628 = 2014 06 28. It was built today.  A 1GB download of an ISO image every few weeks might mean less data downloaded when using the same old ISO image and updating the install during or afterwards.
 
Regards.

---

### Post by ubfan1 on 2014-06-28
After your first update, all the updated packages are sitting in /var/cache/apt/archives.  Just copy them onto a usb, and then for any new installations, copy them back (to the same location).  Updates should recognize the present packages, and install them without downloading again.  Or wait for the 14.04.1 point update in July, and you will have a pretty current set of packages in the iso.

---

### Post by uRock on 2014-06-28
APTonCD may be the way to go for doing this, though it does require installing updates on at least one system before burning the updates to a second disk. [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) 

APTonCD is in the repositories and installable via terminal or USC.

---

### Post by LastDino on 2014-06-28
I have been trying to look for something similar, but apparently you can't have those updates packages installed so that they are put into every machine you do the installation with it without doing anything extra.
But I did find this
[http://askubuntu.com/questions/127923/how-can-i-update-ubuntu-offline-without-using-synaptic-or-keryx](http://askubuntu.com/questions/127923/how-can-i-update-ubuntu-offline-without-using-synaptic-or-keryx)
This talks about many possible ways of doing similar thing as you want. Its not a exact answer and probably wont be much helpful as its old & I've not had chance to try anything of it, but I thought I would share it with you.
I'm personally interested in two concepts of it, Ubuntu builder and another one is copying your pr-downloaded updates to  certain directory on the PC you want to install them to and running 
```
sudo dpkg -i *.deb
```
in that directory to install them.

I'll say it again, this is not something I've tried yet, but it seems something close to what you want, so I'm just sharing and may not work at all.

---

### Post by TJSL on 2014-06-30
> **ubfan1 said:**
> After your first update, all the updated packages are sitting in /var/cache/apt/archives.  Just copy them onto a usb, and then for any new installations, copy them back (to the same location).  Updates should recognize the present packages, and install them without downloading again.  Or wait for the 14.04.1 point update in July, and you will have a pretty current set of packages in the iso.

Copying the updates from the cache folder worked like a champ, it was lightning fast. 

```

sudo cp -arv /var/cache/apt/archives/*.deb /path/to/backup/folder

sudo cp -arv /path/to/backup/folder/*.deb /var/cache/apt/archives && sudo apt-get update
```

---

### Post by ibjsb4 on 2014-06-30
Nice to know :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

