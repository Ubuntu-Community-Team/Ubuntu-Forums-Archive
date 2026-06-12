---
title: "Seperate Home Partition"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by desaivarun_104lts on 2011-03-08
Hi,

I am using Ubuntu 10.04 on Acer Aspire one 532H(A0532H).As for as my knowledge most of the AA1 users are facing three serious issues.They are 1) Battery Issue 2) Internal Mic Not working(Can't use VOIP softwares clearly) 3) SD Card Reader Not Detected(ENE Card Reader). 

Some part of the battery issue is solved by upgrading the bios to latest version,and the internal microphone is not yet been solved(Some people it has been solved by using pavucontrol and alsamixer,but in my case,still it is not resolved)and regarding the SD Card Reader,today i got a message from one of the Natty Testers,that SD Card Reader is working perfect in Natty Narwhal.

My question is : I want to upgrade to Natty from 10.04 .I want to do fresh install.Is there any way i can keep all my existing applications and documents in the system and i can install the new natty,other thank backup using apttocd,i cant use apttocd because i didn't have any CD/DVD writer(I heard that we can keep separate home partition,but while installing i didn't get any separate home partition,i installed on total hard disk) .

If i can do it now,please provide the detailed instruction how to keep separate home partition,so that i can keep all my applications and other data safe,without installing them again and again.

I am a new user to ubuntu,it will be very helpfull if you provide with screenshots.

If it is not the  correct thread for this,please excuse me.

---

### Post by mikewhatever on 2011-03-08
You can not preserve applications because Natty will have newer versions of every package, and the old ones simply won't work. As for personal files, just back them up.

---

### Post by Dutch70 on 2011-03-08
As for the rest of your question...
[[COLOR="Blue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

If you've already installed, but read it carefully. it's old...
[[COLOR="Blue"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by desaivarun_104lts on 2011-03-10
> **mikewhatever said:**
> You can not preserve applications because Natty will have newer versions of every package, and the old ones simply won't work. As for personal files, just back them up.
Hi,

That means i have to download all the applications again and again,once the new release is out..It seems very diffcuilt,i am in a place,where the internet is too slow.it takes long time to download an 700 mb image,after downloading,i have to install all the applications again :-(

Is there no way to keep all my applications?

---

### Post by Hedgehog1 on 2011-03-10
desaivarun_104lts,

The nature of the alpha release cycle is that there are large daily updates, so a location where internet is slow would hinder your using Natty even if you could keep your current applications.

You can move your '/home' data to it's own partition in preparation for the day Natty is ready for you.  Previous posts have the links.

Also - does your situation allow you to use a USB stick to back-up and store data?  Can you get by on this until Natty is ready and you can finally use your SD reader?

Just wondering,

***The Hedge***

:KS

---

### Post by desaivarun_104lts on 2011-03-10
> **Hedgehog1 said:**
> desaivarun_104lts,

The nature of the alpha release cycle is that there are large daily updates, so a location where internet is slow would hinder your using Natty even if you could keep your current applications.

You can move your '/home' data to it's own partition in preparation for the day Natty is ready for you.  Previous posts have the links.

Also - does your situation allow you to use a USB stick to back-up and store data?  Can you get by on this until Natty is ready and you can finally use your SD reader?

Just wondering,

***The Hedge***

:KS
Hi Hedge,

I am not concerned with the alpha release.To overcome my SD problem,i have to install the natty, once the stable release is out.What  i am asking is,if i can take a backup of my home partition,and if i install natty freshly,after installing the natty,can i paste the home partition into the new natty's home partition,and can i use it without any problems?will all my applications will work or not.

If not, every time when a stable release is out,some people interested to upgrade to the new version for different reasons, every time they should download the applications also?

---

### Post by tlcstat on 2011-03-10
Greetings,
I have a 500Gig HD on the way for my Toshiba laptop on which I plan to install Natty. I normally like a clean install. But I think I will copy my home dir over to a separate partition and see what I happens. I have never had a problem migrating my settings and data to a new installation. Bookmarks and Passwords can be exported to a save file. My Claws Email has it's own data dir that I can transfer over, all of the wine software can be saved by copying the .wine dir and then reinstalling wine, and then Office is all the same unless you have some special templates that you are using. Without some discussion of specific Software I not sure you would even have a problem. I tend to install all of the beta stuff and I still use everything that I settled on couple of years ago. Perhaps this upgrade will be different. I will let you know the results. Should have my HD first of next week and I will put home on a separate partition just for the fun of it. If it presents a problem I don't mind reinstalling, done it thousands of times. 
tlcstat

---

### Post by matt_symes on 2011-03-10
Hi

> it takes long time to download an 700 mb image

As for the iso have you considered zsync ?

```
man zsync
```

I don't use it myself as the internet is pretty zippy here but from what i have read it may help with the iso.

Kind regards

---

### Post by Dutch70 on 2011-03-10
> **tlcstat said:**
> Greetings,
I have a 500Gig HD on the way for my Toshiba laptop on which I plan to install Natty. I normally like a clean install. But I think **I will copy my home dir over to a separate partition and see what I happens**. I have never had a problem migrating my settings and data to a new installation. Bookmarks and Passwords can be exported to a save file. My Claws Email has it's own data dir that I can transfer over, all of the wine software can be saved by copying the .wine dir and then reinstalling wine, and then **Office is all the same** unless you have some special templates that you are using.  Without some discussion of specific Software I not sure you would even have a problem. I tend to install all of the beta stuff and I still use everything that I settled on couple of years ago. Perhaps this upgrade will be different.  I will let you know the results. Should have my HD first of next week and I will put home on a separate partition just for the fun of it. If it presents a problem I don't mind reinstalling, done it thousands of times. 
tlcstat

For what it's worth, I copied my .config folder from 10.10 over to 11.04 which is installed on my hdd yesterday & it made my system(11.04)look & act very weird. A lot of things just froze, and I did rename my original .config folder so I didn't have 2 of them. Of course, that, or the fact that it's still alpha3 could have caused the problem.

Also Natty will be using Libre Office. I think that's how you spell it...lol.

---

### Post by tlcstat on 2011-03-10
Greetings,
For Open Office not to run in Natty goes against the whole concept of "free" "open", you may be jumping the gun a bit. Natty hasn't been released in the final stage so Oracle may not have Oo fully ported yet but it can definitely be installed. You are using a beta version so expect problems. The fact that Libre Office is shipped default in Natty means nothing. Gee man! This is Linux!
tlcstat

---

### Post by desaivarun_104lts on 2011-03-10
> **matt_symes said:**
> Hi



As for the iso have you considered zsync ?

```
man zsync
```

I don't use it myself as the internet is pretty zippy here but from what i have read it may help with the iso.

Kind regards
@matt

What is zsync,i just installed,by reading the document,i think it acts like toreent..Is it correct?what is the main help if i download large mb with zsync with slow internet connection,will i get any help if i use this?

---

### Post by tlcstat on 2011-03-10
Greetings, 
Zsync will let you update your install iso file without downloading the entire iso over and over again. This is helpful since they change many of the files in the iso everyday. Since you wont have to continually download the entire iso you are conserving bandwidth on the site to make it available for the developers that also use the site. It is a matter of courtesy.
The command goes like this. Assuming that the iso you are updating is natty-desktop-i386.iso you would put it in the same directory as the zsync file in this case natty-desktop-i386.iso.zsync, the directory in this case being /home/username/Downloads 
Open terminal and give the following command. using the appropriate username. 

sudo zsync -i /home/username/Downloads/natty-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync)

The zsync file has a complete updated file list and only updates the changed files in the iso file. You would then have a updated iso.

check the file for accuracy by downloading the md5sum file and checking the number against the md5sum of the iso. It should match. There is a program called gisomount that will open the iso and check the md5sum for you. Just compare the resulting number with the number in the file you downloaded. 
and have fun.
tlcstat

---

### Post by desaivarun_104lts on 2011-03-10
> **tlcstat said:**
> Greetings, 
Zsync will let you update your install iso file without downloading the entire iso over and over again. This is helpful since they change many of the files in the iso everyday. Since you wont have to continually download the entire iso you are conserving bandwidth on the site to make it available for the developers that also use the site. It is a matter of courtesy.
The command goes like this. Assuming that the iso you are updating is natty-desktop-i386.iso you would put it in the same directory as the zsync file in this case natty-desktop-i386.iso.zsync, the directory in this case being /home/username/Downloads 
Open terminal and give the following command. using the appropriate username. 

sudo zsync -i /home/username/Downloads/natty-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync)

The zsync file has a complete updated file list and only updates the changed files in the iso file. You would then have a updated iso.

check the file for accuracy by downloading the md5sum file and checking the number against the md5sum of the iso. It should match. There is a program called gisomount that will open the iso and check the md5sum for you. Just compare the resulting number with the number in the file you downloaded. 
and have fun.
tlcstat
@tlcstat

Thank you for the clear explanation. I will check it..

---

### Post by tlcstat on 2011-03-11
Greetings,
If you need your computer on a daily basis and are somewhat dependent on it, I would suggest that you stick with 10.10 for the time being. 10.10 is a first class system that is testing without many bugs. It is actually a work of art so far as os's go (my opinion). 
Let Natty get fully released and then perhaps a month or two for the software developers to get up to speed and then do the switch. 

Mean time there are plenty of testing addicts like myself that can keep you posted on the state of affairs with the new distro. I will be putting it on a separate stand alone system next week. I think Open Office will install as long as Libre is "completely" removed. I'm not sure though that I can work it enough to uncover whatever problems might exist. But I will post what I find out. 
tlcstat

---

### Post by matt_symes on 2011-03-11
Hi

> **desaivarun_104lts said:**
> @matt
What is zsync,i just installed,by reading the document,i think it acts like toreent..Is it correct?what is the main help if i download large mb with zsync with slow internet connection,will i get any help if i use this?

It's not something i have really used, only read about. It does not work like a torrent. 

From what i can gather, the first time it downloads the entire ISO.

The second and subsequent downloads, it compares chunks of the ISO on the local drive to chunks on the server and if they are different it will download them so only those parts of ISO that have changed get downloaded saving time and bandwidth.

Here are some links.

[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

[http://www.webupd8.org/2009/10/how-to-upgrade-your-karmic-iso-with.html](http://www.webupd8.org/2009/10/how-to-upgrade-your-karmic-iso-with.html)

This ones is a video (so i'm not so sure if it's good for you)

[http://www.linuxjournal.com/video/updating-isos-zsync](http://www.linuxjournal.com/video/updating-isos-zsync)

I hope it can help you out.

EDIT: @tlcstat. I have just seen your explanation. Very well written. 

Kind regards

---

### Post by desaivarun_104lts on 2011-03-19
> **tlcstat said:**
> Greetings,
If you need your computer on a daily basis and are somewhat dependent on it, I would suggest that you stick with 10.10 for the time being. 10.10 is a first class system that is testing without many bugs. It is actually a work of art so far as os's go (my opinion). 
Let Natty get fully released and then perhaps a month or two for the software developers to get up to speed and then do the switch. 

Mean time there are plenty of testing addicts like myself that can keep you posted on the state of affairs with the new distro. I will be putting it on a separate stand alone system next week. I think Open Office will install as long as Libre is "completely" removed. I'm not sure though that I can work it enough to uncover whatever problems might exist. But I will post what I find out. 
tlcstat
@tlcstat

I am now running on 10.04,i tested the 10.10 also,the main reason,why i am interesed to go to natty is my SD Card Reader is not working on both of these,one of the testers said in his wiki page that,ENE SD Card Reader is working in the Natty,due to the new kernel,and i am very interested that Natty will solve my Main Four Problems

1) ENE SD CARD READER PROBLEM(CARD READER NOT DETECTED)

2) INTERNAL MICROPHONE NOT WORKING(THOUGH I CAN HEAR EXTERNAL SOUNDS,AUDACITY IS ABLE TO RECORD THE SOUND,BUT VERY NOISE)

3) BATTERY MANAGER PROBLEM(THOUGH CHANGED TO NEW BIOS,BATTERY MANAGER EVERYTIME SHOWS WRONG INFO ABOUT BATTERY)

4) UNABLE TO RECORD VIDEO IN THE CHEESE BOOTH WEBCAM.

IMPORTANT ONE UNABLE TO USE ANY VOIP SOFTWARES LIKE SKTYPE,GTALK...VERY VERY SAD ABOUT THIS 
My System is Acer Aspire one 532H (A0532H),1GB Ram,160 GB HDD,INTEL ATOM

---

### Post by nrundy on 2011-03-19
> **desaivarun_104lts said:**
> Hi,

That means i have to download all the applications again and again,once the new release is out..It seems very diffcuilt,i am in a place,where the internet is too slow.it takes long time to download an 700 mb image,after downloading,i have to install all the applications again :-(

Is there no way to keep all my applications?

keep a list of what applications  you have to install (e..g, ones that don't come default). Then "sudo apt-get install application-1 application-2 application-3" etc. You only have to type it once and everything gets installed for you all at once.

I just learned this by the way :)

---

### Post by user_linux08 on 2011-03-24
I also partitioned my Dual-Boot H.drive (Windows 7 & Ubuntu) into 3 partitions.
1. Windows 7
2. Ubuntu Applications and Sys files
3. /Home (formatted for ext4).

This way, it is possible to update ubuntu to new version in either way. upgrade or clean install - all w/o losing any of my personal files on Home directory. 

I can't emphasis enough how many times after system crashes and re-installation, this arrangement had saved me from arduous backing up the /Home onto DVD and back.

I highly recommend to partition the HD and separate the /home onto its own virtual drive. For all those users new to this procedure, you have to be very careful and watch the options closely during the initial installation of ubuntu.

---

