---
title: "Code red issue"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by Whiteice on 2008-08-22
Hello,
I am having a huge issue with my ubuntu upgrade. I start my system off with  feisty fawn. Everything was working well until i needed to run a virtual pc for my college courses. So i started looking for a version. Couldnt find one that would work the way i needed it to so i stumbled upon virtual box. now my sys did not have a version so i decided to use the upgrade utility to upgrade my versoin. So i jumped to gutsy. every thing went smooth but it couldnt find my python editer or something so i just let it do its thing. THen when i reboted the system I found alot of applications in my other folder. I didnt mind and figured i could work around it. So once again i went to virtual boxes website and downloaded the version for my pc. But i found out that they only supported amd64 archtecture. which then it was not able to work with this version. So with high hopes i started the upgrade again to the latest version. i spent all night downloading the packages to awake the next morning with a message saying something about smb. so i said whatever and hit ok. the install started and ran about half way when the upgrade program just froze. i let it sit for an hour and still nothing. so i turn of the laptop. (probley not smart) and when it boots it boots into kde 3.5. I cannot affored to lose the information on my sys because it is infact for school. i'm thinking something got screwy with the kernel and thus i am runing this now. I can however access my files but i cant remove them because a i dont have a drive that i can wright to due to the fact that it is ntfs and i have about 10gbs of files i need so fat 32 wont work either. and b i cannot set up a network because my networking is now not supported. So can anyone help here are my system specs

hp dv6324us lappy
2gbs of ram
amd turion 64x duel core proc 1.86ghz
toshiba 120gb drive

---

### Post by Partyboi2 on 2008-08-22
If you have enough space on your hard drive you could use gparted to create a separate partition of about 10gig for storage and copy over all your files you need to keep.
Since your upgrade froze and you had to reboot the machine I would suggest opening up a terminal and typing
```
sudo dpkg --configure -a
``````
sudo apt-get update
sudo apt-get upgrade
```
If you are unable to fix the upgrade problem and decided to do a fresh install atleast your data would be safe on another partition.

---

