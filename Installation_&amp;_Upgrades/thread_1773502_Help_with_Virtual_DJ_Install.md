---
title: "Help with Virtual DJ Install"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by papadubz on 2011-06-02
****I am using 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
and my question/problem is how do I install Virtual dj app onto my linux? I am unsure on the website how to even download it because the only options are to download as a mac ([http://itunes.apple.com/us/app/virtualdj-home/id417934534](http://itunes.apple.com/us/app/virtualdj-home/id417934534)) or pc ([http://www.virtualdj.com/download/free.html](http://www.virtualdj.com/download/free.html)).  Also I would like to be walked through if there are other steps I would have to take in order to install Virtual dj...like if I would have to install other software in order to be able to run this program. Thanks for your time hope to get a reply soon. First thread.

---

### Post by Joe of loath on 2011-06-02
You could try running the Windows version under WINE, but I'd just look for a Linux alternative. There are lots of DJ programs out there, search in the software centre.

---

### Post by nzjethro on 2011-06-02
Hi there. It seems like Virtual DJ (or at least some versions) run well under WINE. WINE, if you didn't know, lets you run Windows software in Linux. I use it for Guitar Pro and Matlab. To download WINE, type into a terminal
```
sudo apt-get install wine
```
Alternatively, you could search for WINE in Applications>Ubuntu Software Centre, and install it from there. 
When WINE is installed, run
```
winecfg
```
to set up your fake C: drive in you user folder. Then, place the .exe file (probably setup.exe or something similar) for Virtual DJ in your home folder, and open a terminal and type
```
wine *nameofapplication.exe*
```
for example
```
wine setup.exe
```
This should install Virtual DJ. You can find it in Applications>Wine>Programmes.
For more help, go to [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

