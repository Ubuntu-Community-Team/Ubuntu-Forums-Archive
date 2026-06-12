---
title: "Installing ubuntu 11.10 on Fakeraid, any tips or advice?"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by xcal8bur on 2011-11-07
I was all excited about 72 hours ago because I was planning on getting into Linux and learning what it was all about, in addition to having a rock stable (or so I've heard) nfs server to serve 1080p dts to the TVs in the house. Unfortunately it's now three days later and I now have more gray hairs yet Ubuntu 11.10 still does not want to boot off my bios configured RAID5 setup. Having searched through many threads and tutorials, this one here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) seemed the most helpful and I followed it and it ALMOST booted, but ended up giving an error.The error says lots of things but two parts that stand out are "/sbin/dmraid-activate sda [317] terminated by signal 9 (Killed)" (WOW Linux actually uses the word"Killed") and"ALERT! /dev/disk/by-uuid/bunchofrandomnumberslettersandhyphens does not exist. Dropping to a shell" and then it goes to the initramfs prompt.
So this has definitely not been the best introduction to Linux a person could have recieved. Any advice on what should be done or experiences that are related would be much appreciated.

---

### Post by bluexrider on 2011-11-07
Server Guide [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Raid [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by xcal8bur on 2011-11-07
Thanks for your reply bluexrider, those articles are definitely interesting and useful and I may need them both, but the first one doesn't have a heading on raid at all
and the second one talks about softwareRAID wheras I'm dealing with a FAKEraid situation. Linux seems like it could be so awesome too bad it's giving me a hard time getting it going. I'll be glad to look at any other articles you could point me to.

---

### Post by darkod on 2011-11-08
I don't have any links now, just few personal points.
1. Fakeraid is called fake because it really uses your CPU and resources, because it is not a dedicated raid card/controller. In this case, linux/ubuntu software raid works much better, it has been tested and proven.
2. Recovering from software raid failure is much easier than from fakeraid, if you ever get into that situation. But for a server, even if it's for home, I would think about recovery too.
3. Again, even for a home server, I would always use a LTS version, not necessarily the last one. In other words, the latest LTS (Long Term Supported) is 10.04, the next is 12.04 due April 2012. I would use 10.04.

I am actually testing 10.04 to make my own NAS soon (but the current shortage of hdds on the markets is ruining my plan so far), and I'm satisfied with it. I also don't have much experience with raid.

Bottom line, I would definitely consider software raid and 10.04 LTS server.

---

### Post by xcal8bur on 2011-11-08
1. Thank you for responding darkod, but the reason why I intend to run Fakeraid is beacause I would like to dual or even triple boot my system (with W7, ubunbtu, and OSXLion). in addition, although I have read that Linux software raid is good I have trouble believing even more resources are not being used with pure software raid.
I also have a marvell 9128 controller on my motherboard that I would like to raid 0 
2 SSD's and put all three OS's on.
 
2. That's funny I've read the exact opposite, that recovering from a fakeraid is easier. It makes sense to me since when one of your disks in your array are damaged in a software raid the OS could have problems booting. I'll try to find the article.
 
3. darkod, Can you please explain why 10.04 or other LTS versions are better for home servers. I'd like to know.
 
BTW what do you mean there is a current shortage of HDD's? and also have you considered getting a dedicated NAS device (they suck alot less power), I've done alot of research and it seems like the synology ds411 is the best option for home use right now, it's best competitor is probably Qnap but I've read a few reviews where similarly priced QNAP Nas' perform far below Synology Nas'.

---

### Post by darkod on 2011-11-09
LTS server versions are supported with updates etc for 5yrs after the release. So even though 10.04 LTS is soon to be replaced with 12.04 LTS as the latest version, it will still be supported until April 2015. So as long as your server is running how you like it, you don't have to upgrade to 12.04 until you investigate whether that will mess up something or not.
On top of that, I can't explain how or why, but it seems more effort is being put in LTS releases, like major releases, and they are more stable compared to the "ordinary" ones.

Yes, if dual booting with windows fakeraid is the only option but since we are talking about a server I didn't think you will dual boot. Not much usefulness of dual booted server. If it's for practice, just use Virtual Box or similar.

I prefer assembling my own NAS because I think it will work better. I have WD My Book World Edition and not really happy with it. If you use a mini-ITX board with Intel Atom or AMD E-350 it doesn't use much power. As far as the HDDs go, there were very big floods in Thailand in the major factories and the prices have jump to sky. You could buy 1TB disk for 40-45€ and now they are selling for like 160€. The shortage is not expected to normalize until the end of first quarter 2012 as far as I have read.

Lastly, you mentioned RAID0. Regardless if it's fakeraid or softraid, if you plan to use raid0 you are aware that it doesn't protect your data, right? If a disk fails, you can replace it and have a new array, but the data is gone. In raid0 the data is written half on one disk and half on the other so you can't restore it with one disk failed. You can't expect raid0 to protect you for any serious server use. If this is just for playing, fine. I guess you want to see how fast raid0 SSDs will go.

---

### Post by xcal8bur on 2011-11-09
1. Thank you for the informative post darkod, I will probably use the 10.04 LTS server edition now, can you tell me if that versions installation allows you to choose whether GRUB gets installed to the master boot record or not? is dmraid included in the package? (ie. does it recognize Fakeraid?) I want to use GRUB legacy to triple boot my computer according to this link [https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot) . (BTW I don't see why Windows and Mac OSX can't serve on the same machine as linux as long as you reboot).
 
2. Do you have any links that you can provide that show how one can setup there own NAS? do you know roughly how much power the mini-ITX NAS' use? are home made mini-ITX NAS' faster than commercial NAS'? can you build them with Link aggregation (802.3ad 2Gbps ethernet ) for faster data delivery to multiple clients?
 
3. Regarding the RAID 0 SSD's, I only plan on running the OSes on them, my data will be on a RAID 5 (some redundancy, good read speed) on a seperate array of normal yet fast seagate HDD's. in addition I intend to backup the DATA with a Blu-Ray burner. 
 
P.S. So does anyone know how to setup GRUB legacy on Fakeraid arrays? I now believe that is the only reason why UBUNTU will not boot properly because the Error that it gives me seems to be related to GRUB stage 2 according to this link [http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)
 
Thank you for your time, in advance.

---

### Post by darkod on 2011-11-09
1. I don't have an exact number about the power use, but my logic is this: The disks will use more or less the same regardless in what kind of box they are installed. As far as the cpu goes, the two cpus I am considering are the Intel Atom D525 of 13W and AMD E-350 of 18W. A lot less than 65-95W that cpus have these days. I was first planning to use and old Athlon Clawhammer because I already have it, but after seeing that the TDP is 90W, I figured a low power cpu will pay for itself over the long run.

2. Yes, 10.04 LTS lets you choose where to install grub2 but I have never tried installing it on a partition, not on the MBR. It would probably work.

My idea with saying multi boot is strange for a server, was not that it wouldn't work. It was more from a point of view that if you don't use some kind of virtualization, you can only have one OS booted at the same time, not all three. A server would have its role and usually you don't turn it off to reboot the other OS.

Have you already tried the install of both grub1 and grub2 and the chainloading and it didn't work?

---

### Post by xcal8bur on 2011-11-09
2. So does 10.04 let you choose where GRUB installs even with the normal CD .iso or do you have to use the alternate CD .iso or the server CD .iso perhaps?. Can you also please explain what virtualization is a little further?, it sounds interesting.
 
What I did was follow the thread in my first post. There was a series of commands for the ubuntu terminal that I went through (all of which I am not sure what they do) but I believe I removed the grub2 and installed grub 1 and then setup grub to point at what ubuntu sees as my RAID MBR or boot sector. That's one of the problems I am not familiar with all these linux commands so I am not sure exactly what I'm doing. I have not attempted chainloading yet I was trying to get ubuntu to work first by itself with grub. do yo think chainloading will have a better chance of working even if ubuntu is the only OS on the RAID.

---

### Post by darkod on 2011-11-09
Ubuntu should let you choose where to install grub2 with all types of CDs. But for installing a server I guess you will use the server cd.

I am not an expert in chainloading with grub1, especially on fakeraid, so I can't give you exact instructions.

If you install only ubuntu there is no need to chainload, just let it use grub2 and install it on the MBR. When you get to the point of adding other OSs, you will have to tackle the grub1 and chainload problem.

Wikipedia link on hardware virtualization:
[http://en.wikipedia.org/wiki/Platform_virtualization](http://en.wikipedia.org/wiki/Platform_virtualization)

With the latest ubuntu releases the server cd actually has an option for virtualization that makes it easier to install. And there are lots of manuals on the internet to read more about configuring it.

Yeah, I know what you mean about running commands without understanding them. But it's better if you get more into it sooner rather than later because it really helps to do things right and not make mistakes. I'm far from an expert myself. :)

---

### Post by Hedgehog1 on 2011-11-10
> **xcal8bur said:**
> 
BTW what do you mean there is a current shortage of HDD's? and also have you considered getting a dedicated NAS device (they suck alot less power), I've done alot of research and it seems like the synology ds411 is the best option for home use right now, it's best competitor is probably Qnap but I've read a few reviews where similarly priced QNAP Nas' perform far below Synology Nas'.

I have a Synology DS411 that serves as my NAS for 3 Ubuntu PCs, 2 Windows 7 PCs, and also feeds DNLA to two blu-ray players and one DNLA aware HDTV. Inside it has a little Linux OS that does all these things.

Their implementation on the software is outstanding - but if you are willing (or just wanting) to fool around and make your own, you can.

I love my DS411 - they will have to pry it from my dead hands to take it from me.

As to the hard disk shortage: The Floods in Thailand (where 50% of hard drives are made and nearly all hard drive manufacturers use parts made in Thailand) have caused a shortage hard drives (well, for reasonable money, anyway).  The are going fast and selling for far more than they were 4 weeks ago.

***The Hedge***

:KS

---

### Post by xcal8bur on 2011-11-12
I believe I got this one solved, even though I'm not sure exactly what was wrong.
after trying some other tutorials on getting fakeraid to work namely this one here
[http://samueltaylor.me.uk/2011/01/31/setting-up-nvidia-nforce-fakeraid-on-ubuntu-10-10/](http://samueltaylor.me.uk/2011/01/31/setting-up-nvidia-nforce-fakeraid-on-ubuntu-10-10/) . Even though the tutorial was counterproductive as linux saw a corrupted RAID array after the first boot, the tutorial above got me thinking about the metadata and partition tables. So I went into Gparted saw that my partition tables for the RAID array and the disks individually were GUID or GPT, so I went to Device->create partion table..., for all three disks and set it to msdos partition table. then I rebuilt my array in bios and booted the live cd normally, went into GParted and created an msdos partition table for the array, then formatted 2 partitons. One as ext4 and the other as linux swap. I then started the ubuntu installer and chose "something else" when asked where to install. I did not format anything with the installer but created a moint point / for the Ext4 partion that gparted created. the other reason I chose "something else" was because the ubuntu installer by default wants to install GRUB to /dev/sda which would I believe corrupt something since it would be trying to access the RAID member disk directly. So I chose my RAID array for the location to install GRUB (the bootloader). Even though it failed installing GRUB and gave an error at least it did not try and install it on /dev/sda. When it failed I chose to continue without installing a bootloader. Then before rebooting I followed this tutorial [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html). After rebooting ubuntu started no problems,I'm guessing the GUID partiton tables were the worst part of my problem that along with GRUB not installing correctly. I've rebooted several times now and it seems to have worked, peculiarly GParted has disappeared. So I hope this info helps someone else. This is all on RAID 5 on an ICH10R on a GA-X58-UD5 gigabyte motherboard. when my second SSD arrives I'll probably put ubuntu on that in RAID 0 and use the RAID 5 as DATA. I benchmarked the RAID 5 array in Ubuntu's disk utility app and it gives me 196.0 MB/s avg, 259.4 MB/s max for READ and 145.6 MB/s avg, 279.2 MB/s max for WRITE with 19.1 ms access times, any opinions on these figures are welcome.
 
BTW does anyone know why GParted has disappeared? it says installed but its not in the apps.
 
To: Hedgehog, How many terabytes do you have on that? does it serve NFS shares? the only thing I think that particular NAS is lacking is LINK aggregation (802.3ad), but if it can serve 3 1080p DTS .mkv streams then it's good enough for me, perhaps you can answer that question.

---

