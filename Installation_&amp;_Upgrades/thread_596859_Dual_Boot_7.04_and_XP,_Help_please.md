---
title: "Dual Boot 7.04 and XP, Help please"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-10-30
I just got Hi-Speed. I am in the process of dealing with: do I get a router to keep the hackers out? (The hi-speed is connected to my XP machine. My Feisty machine is in the other room. The XP PC has more RAM and twice the CPU. The Video Card has 256mgs DDR ram. My Linux Box has 1 Gig DDR Ram, 1Gig CPU, and an old 8mg (yes video card. It's attached to the net via an external serial modem.

I am working up the nerve to put Feisty on the bigger machine, probably a dual boot w/XP. I am all set to do it. I ran the Live CD of Feisty and it worked fine. No sound, video, net connecting, no problems at all that I noticed during a 3 hr run thru.

I have a book I used to learn Dapper, called "Linux for Non-Geeks" by Richard Grant. W/o that I would likely never have stayed w/Ubuntu long enough to get to the point where I feel comfortable. He says the way to do a dual boot is to have XP on the HDD, and to do a defrag. Then install Ubuntu. During the install when asked how do you want the partition, there are 3 choices. He says to pick the 1st one, and to use the slider to divide the HDD and then go ahead and install. He says it is easy and seamless. I have to say that I intend to believe him because after going thru most of the book twice already, once w/6.06 and once w/7.04, I have had NO hassles.

Before I wake up tomorrow and take the plunge and go ahead with this attempt at dual boot, does anyone have any advice? My XP is NTFS, what is Feisty? 32FAT? That seems like a potential problem.

I only need XP for a couple games and because I can't get Ubuntu to play certain streaming audio. I have trouble with .ra and .rm files, as well as .asx files. Anything that comes thru in MP3 is fine. If I can get the audio and video happy, so I am not missing that part of the net (I am a news hound), then I likely would go w/o MSoft altogether.

Thnx guys, sorry for being so wordie, I am like that.

---

### Post by cherry316316 on 2007-10-30
> **Chappy7777 said:**
> I just got Hi-Speed. I am in the process of dealing with: do I get a router to keep the hackers out? (The hi-speed is connected to my XP machine. My Feisty machine is in the other room. The XP PC has more RAM and twice the CPU. The Video Card has 256mgs DDR ram. My Linux Box has 1 Gig DDR Ram, 1Gig CPU, and an old 8mg (yes video card. It's attached to the net via an external serial modem.

I am working up the nerve to put Feisty on the bigger machine, probably a dual boot w/XP. I am all set to do it. I ran the Live CD of Feisty and it worked fine. No sound, video, net connecting, no problems at all that I noticed during a 3 hr run thru.

I have a book I used to learn Dapper, called "Linux for Non-Geeks" by Richard Grant. W/o that I would likely never have stayed w/Ubuntu long enough to get to the point where I feel comfortable. He says the way to do a dual boot is to have XP on the HDD, and to do a defrag. Then install Ubuntu. During the install when asked how do you want the partition, there are 3 choices. He says to pick the 1st one, and to use the slider to divide the HDD and then go ahead and install. He says it is easy and seamless. I have to say that I intend to believe him because after going thru most of the book twice already, once w/6.06 and once w/7.04, I have had NO hassles.

Before I wake up tomorrow and take the plunge and go ahead with this attempt at dual boot, does anyone have any advice? My XP is NTFS, what is Feisty? 32FAT? That seems like a potential problem.

I only need XP for a couple games and because I can't get Ubuntu to play certain streaming audio. I have trouble with .ra and .rm files, as well as .asx files. Anything that comes thru in MP3 is fine. If I can get the audio and video happy, so I am not missing that part of the net (I am a news hound), then I likely would go w/o MSoft altogether.

Thnx guys, sorry for being so wordie, I am like that.



use ubuntu gusty 7.10

---

### Post by logos34 on 2007-10-30
yeah, why not install 7.10? You have broadband now, shouldn't take that long to download.

A router is the best firewall...great first line of defense to protect your windows system.  And linux with the default iptables firewall settings should be virtually impregnable.  Test your vulnerability with these lnks:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
[http://weblogin.bu.edu/troubleshooting?cmd=ssl](http://weblogin.bu.edu/troubleshooting?cmd=ssl) 
[http://security.symantec.com/sscv6/default.asp?langid=ie&venid=sym](http://security.symantec.com/sscv6/default.asp?langid=ie&venid=sym)

Dual boot installation:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.easy-ubuntu-linux.com/](http://www.easy-ubuntu-linux.com/)

.ra and .ram are Real media.  Use RealPlayer and/or MPlayer (+mozilla plugins). 

multimediacodecs:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mikeize on 2007-10-30
As to the formatting of your partition.  It's really up to you.  I think most people have linux on an ext3 partition, followed by reiserfs... and you could do FAT32, but I can't remember if there is a file-size limit or something with that format.  The advantage of a FAT partition would be that XP would automatically be able to recognize and read it, though I found a little program that lets my XP read my ext3 partition, so don't let that decide for you.
I don't really know the merits of any of these over the others, but I suspect they're minimal.  In any case, it doesn't matter what format you use, since it is on a different partition than XP, there won't be any conflict.

-mike

---

### Post by logos34 on 2007-10-30
> **mikeize said:**
> I think most people have linux on an ext3 partition, followed by reiserfs... and you could do FAT32, but I can't remember if there is a file-size limit or something with that format. The advantage of a FAT partition would be that XP would automatically be able to recognize and read it, though I found a little program that lets my XP read my ext3 partition, so don't let that decide for you.

fat32 has a 4gb file size limit, so no large movie files or backup images...besides, it fragments much more easily and is not as secure as ntfs, so avoid if possible.  Luckily it's no longer really necessary since there's fs-driver for windows (what mikeize is referring to I believe) and ntfs-3g for linux (preinstalled in Gutsy).
Use ext3 for linux partitions (or reiserfs,xfs,jfs).

---

### Post by Chappy7777 on 2007-10-30
I can't really tell if you guys are saying "yes, that will work" or not. As to why not use 7.10 rather than 7.04, I have 7.04 on a Ubuntu CD that was mailed to me, so I know it's not corrupted. Is there that much difference between what I can do with 7.10 and 7.04? Like what? If the upgrade is worth it, I'd do it. Tho since I am new to hi-speed, I am new to making ISO disks and using mdr , etc. It's all intense geek to me.

I have 7.04 on my other PC as well as 6.06LTS, and I see little difference other than in 7.04 all the programs are newer versions. I imagine that's true of 7.10  Newer versions. Duh, isn't that what an upgrade is? LOL, my brilliance amazes me. NOT!  BTW, I don't use Dapper anymore, I just haven't needed that 20G HDD so it's sitting in my desk drawer (the HDD). 

I am going to defrag XP (i do have NTFS) and get the HDD ready to install 7.04 as a dual boot. Unless I read a reply in here saying, no don't do it!!!, I will likely go ahead and try it later. Worse case scanario, I have a mess and end up reinstalling 7.04 on the whole drive. With a few exceptions, I can live w/o Windows.

If you guys think I am making a big mistake (to the point where it won't work) please reply to this asap.

---

### Post by Chappy7777 on 2007-10-30
[QUOTE=logos34;3667466]yeah, why not install 7.10? You have broadband now, shouldn't take that long to download.

A router is the best firewall...great first line of defense to protect your windows system.  And linux with the default iptables firewall settings should be virtually impregnable.  Test your vulnerability with these lnks:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
=========================

Just a quick note to say I am a long time fan of Steve Gibson's and the 1st thing I did after the cable modem was installed and I set it up, was go to his site and run "Shield's Up".  My software Firewall, Comodo, passed. No open ports found. Most were in stealth. Tho when I was using dialup, everything was stealth w/just Comodo.

---

### Post by Chappy7777 on 2007-10-30
doink

---

### Post by Chappy7777 on 2007-10-30
I'm starting to assume that you all think going ahead w/my plan is ok. In which case, thanx alot.

I am off to watch "Lab w/Leo".  I am praying he will talk Linux this eve.

---

### Post by logos34 on 2007-10-30
> **Chappy7777 said:**
> I can't really tell if you guys are saying "yes, that will work" or not. As to why not use 7.10 rather than 7.04, I have 7.04 on a Ubuntu CD that was mailed to me, so I know it's not corrupted. Is there that much difference between what I can do with 7.10 and 7.04? Like what? If the upgrade is worth it, I'd do it. Tho since I am new to hi-speed, I am new to making ISO disks and using mdr , etc. It's all intense geek to me.

...

I am going to defrag XP (i do have NTFS) and get the HDD ready to install 7.04 as a dual boot. Unless I read a reply in here saying, no don't do it!!!, I will likely go ahead and try it later. Worse case scanario, I have a mess and end up reinstalling 7.04 on the whole drive. With a few exceptions, I can live w/o Windows.

All systems look go to me.

I agree, no big diff between feisty and gutsy, that's my opinion at least.  And as you say you can always upgrade. (If you do, it might be better to upgrade from the alternate cd rather than online...plus, it will introduce you to  [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") check, [burning an image]("https://help.ubuntu.com/community/BurningIsoHowto"), etc--all very easy).

Backup your files in windows just to play it safe.

---

### Post by Chappy7777 on 2007-10-30
> **logos34 said:**
> All systems look go to me.

I agree, no big diff between feisty and gutsy, that's my opinion at least.  And as you say you can always upgrade. (If you do, it might be better to upgrade from the alternate cd rather than online...plus, it will introduce you to  [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") check, [burning an image]("https://help.ubuntu.com/community/BurningIsoHowto"), etc--all very easy).

Backup your files in windows just to play it safe.
=============================================
Thnx Logos. That cements it. I will do as planned. I'll let ya'all know what happened after I'm done. 

Oh, I went to watch Lab w/Leo and he did do a Linux section. Praise God.

---

### Post by logos34 on 2007-10-31
Just came across this and thought I'd pass it on:

[URL="http://www.pcmag.com/article2/0,2704,2178277,00.asp"]'Add Linux to Your Windows'
[/URL]
Haven't had a chance to look at it but hopefully it will further demystify the dual-boot installation.

---

