---
title: "New installation without internet needs help"
date: 2018-07-01
forum: Installation &amp; Upgrades
---

### Post by timfraf on 2018-07-01
Hello, 

First let me apologise if this post has already been answered a billion times...

So I am trying to dual boot(windows10 and a linux distro) my newly built PC.  I am able to partition everything and install both OS and the grub boot loader. Some of the details of my issue: I used a USB and rufus to make the Ubuntu 18.04 installation USB, I am using a NETGEAR USB wifi adapter so I do not have internet upon installation of Ubuntu (I also do not have an ethernet port), my machine has hdmi, USB 2.0, and USB 3.0 ports available, there is a driver online which I have downloaded and have available, and I am using an external HDD for storage between OS and can see the drive in both windows and Ubuntu (it is NTFS formatted for dual use).  
The problem I am having is that in order to use the wifi adapter driver I need the make utility and thus far I have tried:
1) using Synaptic to build a list of packages that I need in order to get make and then take that script to a pc that has internet.
2) installing the make utility using the .tar from the package site
3) trying to make my own offline repository

and now my failures:
1) Synaptic requires make to build it, so you can see the circular logic...
2) I can get the make tar from Ubuntu but Ubuntu fails to install it when I click on the "open with software installer"
3) The made repository never is accessed even when I add it to the "other software" tab under software and updates.

I know that each one of these probably has solutions and I will continue to explore them but I would like to ask the community if there is an installation that has both the files for Ubuntu OS and the complete offline package repo so that I can have all of it baked into one place that I can install the os, run the make file on the Netgear driver, and then have wifi. I think this is best but I am also willing to take suggestions on other things to try. 

Best and TIA,

---

### Post by jeremy31 on 2018-07-01
In terminal there is a print-uris option.  You need package build-essential so in terminal ```
sudo apt-get install --print-uris build-essential
```
And terminal should show URL's to download the packages from along with MD5 sums.  Download when online and copy them to Ubuntu destop, then in terminal ```
cd Desktop
sudo dpkg -i *.deb
```

---

### Post by timfraf on 2018-07-01
Ugh, well I guess that Ubuntu doesn't know what build-essential package is. I just tried your code and Ubuntu responded that it doesn't recognize a package named build-essential. 

I will try and find a friend who is running Ubuntu and has an internet connection who can run this command for me. 

I will update as I go... thanks though

---

### Post by timfraf on 2018-07-02
Update: I tried adding main to source.list and it still will not recognize build-essentials as valid package.
I also tried making an offline repo but it is saying that the signature for the repo is not valid. This is really frustrating.  I am going to try and find a tutorial for compiling gcc offline and see where that goes.

---

