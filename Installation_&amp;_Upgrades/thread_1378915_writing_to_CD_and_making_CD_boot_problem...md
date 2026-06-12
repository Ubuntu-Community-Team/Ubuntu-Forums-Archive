---
title: "writing to CD and making CD boot problem.."
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by sathyashrayan on 2010-01-12
Dear group,
  I have ordered a ubuntu CD in 2006 and received that through post. Till yesterday i have not got an idea to install it. when i install the CD (version 7.04) yeaterday I was not asked for any root password to set. During the first time running of the OS it counted the day from 2006 in the command line(text mood) and messaged in the right corner as [FAILED] in red. In spite of that I have sucessuly installed the version 7.04 and tryied an auto update mannager for latest software but it shown an error that there is a connection problem and some set of security software (around 40 ) can not be connected to the site(web link)..

So i have downloaed the latest ubuntu version (given in the home page now), followed the CD burning process and created a CD. Then I restart the system, changed BIOS for 1th boot to CD drive.. I was expecting a instillation process with GUI but the following shown in the command line..

---
ISOLINUX 3.63 Debian-2008-07-15 Copyright(C) 1994-2008 H Peater Anvin

boot:
---

What command should I give now? 'help' command does not work. '?' command does not work..

Am I missing something basic? Even after I install the new version can I be able to update the latest software with automatic support? Will I be able to create root user?

I am using is in my PC(stand alone) with the following system config..

AMD Sempron(tm) processor
2500+
704 MB RAM
ASUS mother board..

two HD, one 80GB with windows and 20 GB with old version of ubuntu

I am very eager to see the latest version and start working on it.. Please help

---

### Post by Impulser on 2010-01-12
Wait, did you install Ubuntu or this show up when booting with disc in the drive because the CD should take you pass that screen and you shouldn't have to enter any commands and it might just be the disc and how you burned it. I'm not sure if there is any commands that you can use. You will create a root user when installing Ubuntu and yes you will be able to upgrade to the latest software.

---

### Post by lisati on 2010-01-12
7.04 is no longer supported, updates will be difficult (impossible?) to make work. It might be a good idea to use a newer version.

---

### Post by sathyashrayan on 2010-01-12
> **Impulser said:**
> Wait, did you install Ubuntu or this show up when booting with disc in the drive because the CD should take you pass that screen and you shouldn't have to enter any commands and it might just be the disc and how you burned it. I'm not sure if there is any commands that you can use. You will create a root user when installing Ubuntu and yes you will be able to upgrade to the latest software.
>Wait, did you install Ubuntu or this show up when booting with disc in the drive

There is a previous version,7.04.. but when I have the CD with boot loader it is suppose to get me to the instillation screen and live CD rit?

>CD should take you pass that screen and you shouldn't have to enter any commands and it might just be the disc and how you burned it.

Yes, it should.. But in my case it is not.. It is showing the above mentioned text mode message with boot: comand prompt and waiting..

---

### Post by sathyashrayan on 2010-01-12
> **lisati said:**
> 7.04 is no longer supported, updates will be difficult (impossible?) to make work. It might be a good idea to use a newer version.
I am trying the same.. I am really love to work in linux..Any one please help..

---

### Post by sathyashrayan on 2010-01-12
I have created two CDs with the same .iso.. both are not working..

---

### Post by sathyashrayan on 2010-01-12
I have got this file ubuntu-9.10-desktop-i386.iso

and following are the files and directories..

please check the attachment..

---

### Post by sathyashrayan on 2010-01-12
I have installed RHEL in the same disk.. It was working good.. Is the latest ubuntu is not supported for my system config? Or is that a bug? I have searched google with those keyword and can not able to get a solution..

---

### Post by sathyashrayan on 2010-01-12
When I compared the CD I have received and the .iso files (new version) I see some files are missing.. especially the start.ini file. Do i have to create the start.ini and try? refer the attachment?

---

### Post by sathyashrayan on 2010-01-12
Any one faced this problem? I am slowly loosing hope with Ubuntu.. :(

---

### Post by sathyashrayan on 2010-01-12
with wubi.exe also showing error as "cannot unpak wubi.exe" as a dialog box.. (internal error box..)

---

### Post by pricetech on 2010-01-12
First of all, check the download.  There are winders programs which can check the md5 sum of the ISO and compare it with the sum shown on the download site.  Kana CheckSum comes to mind, available from kanasolution.com

Once you have verified the download, burn the disk at the slowest speed your software will let you.  When you boot to the disk, check it.  That's one of the options on the boot menu.

Once those tests have been passed, install.

Good Luck and welcome to Ubuntu.

---

### Post by lisati on 2010-01-12
> **sathyashrayan said:**
> I am trying the same.. I am really love to work in linux..Any one please help..

Like I said, v7.04 is an old version of Ubuntu, and getting a newer version will probably suit most people better.

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
[https://help.ubuntu.com/community/CommonQuestions#Releases%20and%20Version%20Numbers](https://help.ubuntu.com/community/CommonQuestions#Releases%20and%20Version%20Numbers)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by recluce on 2010-01-12
These problems come up daily - and always, they can be linked to one of the following:

1.) defective download. Check the MD5 or SHA1 of your downloaded ISO to verify this

2.) Crappy burn, for one of the following reasons:

2a.) bad cd burner
2b.) bad media
2c.) bad burner software
2d.) bus problems causing communication errors during the burn

To minimize the problems above, buy good media (not the cheapest junk), burn with verify, reduce burn speed.

To verify if you have any of the above problems: use another burner, use different media, use a different software and ALWAYS enable "Verify" while burning. Try to boot the CD on a different computer.

If your Ubuntu CD doesn't even get to the initial menu, I would bet that it is a bad burn. If you get to that first menu, the very first thing to do is **"Check CD for defects"**, the bottom option of the menu.

---

### Post by sathyashrayan on 2010-01-12
> **pricetech said:**
> First of all, check the download.  There are winders programs which can check the md5 sum of the ISO and compare it with the sum shown on the download site.  Kana CheckSum comes to mind, available from kanasolution.com


I downloaded that .iso from the home page and I have used the software(Kana CheckSum) to verify..It gives an md5 value (32 chrs)

> **pricetech said:**
> Once you have verified the download, burn the disk at the slowest speed your software will let you.  When you boot to the disk, check it.  That's one of the options on the boot menu.

I burned the iso as per the instruction given in the page [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  and went to the BIOS and changed the first boot as cd/dvd  still I am getting the same blank text mode screen and waiting for an command prompt with boot:[cursor blink]

> **pricetech said:**
> 
Once those tests have been passed, install.

Good Luck and welcome to Ubuntu.



> **lisati said:**
> 
Like I said, v7.04 is an old version of Ubuntu, and getting a newer version will probably suit most people better.


Yes that is what I am trying to do for the past 3 days.

> **lisati said:**
> 
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
[https://help.ubuntu.com/community/Co...sion%20Numbers]("https://help.ubuntu.com/community/CommonQuestions#Releases%20and%20Version%20Numbers")
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)


Very helpful links. 



> **recluce said:**
> These problems come up daily - and always, they can be linked to one of the following:

1.) defective download. Check the MD5 or SHA1 of your downloaded ISO to verify this

2.) Crappy burn, for one of the following reasons:

2a.) bad cd burner
2b.) bad media
2c.) bad burner software
2d.) bus problems causing communication errors during the burn

To minimize the problems above, buy good media (not the cheapest junk), burn with verify, reduce burn speed.


I have tried with two softwares. One is nuro burn that comes along when I buy the cd/dvd device and the another one is a Infra Recorder according to the link [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) both are not working.

> **recluce said:**
> 
To verify if you have any of the above problems: use another burner, use different media, use a different software and ALWAYS enable "Verify" while burning. Try to boot the CD on a different computer.

If your Ubuntu CD doesn't even get to the initial menu, I would bet that it is a bad burn. If you get to that first menu, the very first thing to do is **"Check CD for defects"**, the bottom option of the menu.
 

Yes..after lot of help from this forum I feel the same. Its the bad burn. But during the burn I have not got any error message from both the above mentioned two cd burning software..


@all
  Rather that trying hours together for burning the .iso and getting clue less I have decided to wait for some weeks. So yesterday I have ordered for the latest CDs through **Requesting an Ubuntu CD**  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) and ready to waite for some days to get it all going. Thanks for all the help..

---

### Post by recluce on 2010-01-13
> **sathyashrayan said:**
> I downloaded that .iso from the home page and I have used the software(Kana CheckSum) to verify..It gives an md5 value (32 chrs)

And did that hash value match the one published on the Ubuntu website? Everything you feed into a hash algorithm like MD5 will give a fixed length hash, the question is if it matches the reference!


> 
I have tried with two softwares. One is nuro burn that comes along when I buy the cd/dvd device and the another one is a Infra Recorder according to the link [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) both are not working.

Yes..after lot of help from this forum I feel the same. Its the bad burn. But during the burn I have not got any error message from both the above mentioned two cd burning software.. 

Did you burn with "Verify" enabled? For technical reasons, a CD burner is unable to recognize most burn errors during the burn process - so not getting an error means nothing. Only a good verify will indicate that the burn is most likely good.

> 

@all
  Rather that trying hours together for burning the .iso and getting clue less I have decided to wait for some weeks. So yesterday I have ordered for the latest CDs through **Requesting an Ubuntu CD**  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) and ready to waite for some days to get it all going. Thanks for all the help..

That might be the  easiest solution.

---

### Post by sathyashrayan on 2010-01-30
I have received the CD through postal today.. Thanks for all the help provided for checking .iso md5 checksum.

---

