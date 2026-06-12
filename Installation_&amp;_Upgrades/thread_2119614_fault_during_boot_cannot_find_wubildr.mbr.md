---
title: "fault during boot cannot find wubildr.mbr"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by nijunge on 2013-02-24
So I have come to a grinding hold on this 

What is done 

Used Wubi to start download 

I have two partisions on the ssd hard drive on my laptop and want to use one for windows one for Ubuntu 

There for the only thing I changed on the user info was the drive (could this be the problem) 

and ready to boot first time and it just tells me that the \ubuntu\winboot\wubildr.mbr could not be found 

Can anyone help on this 

N

---

### Post by nijunge on 2013-02-24
Oh yea by the way its on a win 7 64 bit laptop

---

### Post by oldfred on 2013-02-24
Normally Windows users who want a longer test of Ubuntu than the liveCD install wubi. It is then like a program in Windows, requires no repartitioning, boots thru Windows and is just a file inside the Windows NTFS partition. It then is easy to uninstall.

But if you want to install to another partition, it is better to do a full install from a liveCD/DVD/Flash drive.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)> 
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    

---

