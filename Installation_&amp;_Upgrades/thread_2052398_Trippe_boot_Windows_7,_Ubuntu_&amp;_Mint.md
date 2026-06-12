---
title: "Trippe boot: Windows 7, Ubuntu &amp; Mint"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by Xanthius on 2012-09-03
I guess a lot of people ask this same question, and no I'm not too lazy to search but the results I get don't really match my situation.

So yeah, as expected I've been using Windows a long time, ever sinse Windows 3.1 came to be however with Windows 8 Microsoft is really pushing forward to their "new interface" and to me it feels like they decided to take a huge dump at my doorstep. 
This does not mean I'm unfamiliar with Linux, but I still prefer a friendly user interface which Ubuntu & Linux Mint seems to offer.
So yeah, its time to start switching over and learn now so I don't have to know Metro for when Windows 7 ends up like XP.

So here is what I want to know: formatting, partitioning & sizes.

My hardware of Interest:
[LIST]
[*]Dell XPS L702X (17)
[*]120GB SSD
[*]320GB HDD (NTFS)
[*]4GB RAM
[/LIST]

I am currently running a single boot of Win7, which I can re-install but I prefer not to. I want to use at least 50 GB of space for Windows.
Now I've once read that the EXT (3/4) file format works faster on Linux than NTFS, so I prefer a clean file system rather than a Wubi install.
I also want to use the SSD for all my O.S's, as I store my large files games, photo's, music & video's on my HDD.
I've read that Ubuntu & Mint share the same apps, meaning I want to install apps 1 time for both installations (if really possible)
I've also read that the swap partition needs to be the same size of your memory for hibernation mode, and can the swap partition be shared of both Linux installations?


So what is the recommended partitioning (incl. sizes & file systems) of my SSD? 
And is it wise to change the SSD partitioning, or shall I do a complete re-install?

I don't require a lot of space for Linux, since I design websites and program applications, do some photo and perhaps some video editing. Maybe even play some games, such as Minecraft or Open TTD, not too excessive usage of SSD space but I want more then enough space not to worry about it.
I realize the size is limited, and since I'm unfamiliar with the sizes of Linux installations and how big they can get (such as Windows builds up easily to 60GB without games installed on it) I'm requesting help.

---

### Post by mastablasta on 2012-09-03
i have it installed in 8GB virtual disk. it used about 6GB or so. you can install it in virtual box first if you like to give it a go: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
i use it to test a few things, learn and also i have webserver installed to test some websites and tools i plan to use later on hosting mashcine.
 
also make sure you test it by running it live before installing it. just to see if your hardware is actually suppoted.
 
i guess you still intend to use windows drives for data and such which is OK as linux can read them just fine. Windows can't access the linux part without special tools. 
 
otherwise for dual boot linux size: for work and such and to leave some space for any downloads and saves i would say carve a 20-25Gb chunk out of hard disk and leave it to installer to set the partitions. 4Gb or more will be taken by /swap (kind of like page file and used for hibernation and such), with kernel updates and additional programmes you will easilly come to about 10GB, the rest you can use for some data or temporary saves. programmes in linux don't take much space, but then again depends which ones you plan to use. 
if you have gnome (Ubuntu) and install a KDE programme to it (KDE is used in Kubuntu), it will download plenty KDE libraries. but only once. next time you install KDe libraries will already be there so the next install will be much smlaler
 
more complicated games also sometimes take plenty fo space. bu tlike i said if you have about 10GB for data &programmes it should be more than enough. since as i udnerstand you plan to have main data on windows disk.
 
oh and BTW windows 8 does have classic desktop option. additionally via third party windows7, XP and i htink even windows 95 kind of menues are already available.
 
EDI: one last thing. if you just want Mint interface you do not have to triple boot, just for that. you install ubuntu and then isntall Cinamon or Mate (+mint menu) desktop whichever you prefer. then to change the interface you logout and on log in select a new interface.
 
if you are looking for windows look&feel then i suggest to try Kubuntu. if oyu dont' liek the K menu, right click on K and select classic menu style. it looks preety much like windows classic then...
 
EDIT2: Does Dell XPS L702X have Nvidia Optimus? if so you will need to look into compatibility and the bumblebee project. Nvidia doesn't suppor tthis technology in linux, which is why Linus told them to go ....

---

### Post by Xanthius on 2012-09-03
The Dell XPS 15/17 use optimus but I've ran the Ubuntu live CD to fix my windows driver issue, it worked and since my internal GPU is more then enough to fit my needs for designing in Linux bumblebee does support it, hopefully GPGPU as well.

I'll make a bootable USB drive, install Ubuntu and take the advice of carving 40GB of beginning space for the entire Linux installation. 

Thanks for mentioning switching between workspaces because Unity is mostly for my "personal" use and Cinamon for my configuration / programming & designing needs that saves quite a lot of size.

For the Windows part, I do not really see any need to continue with it. I can go in depth of what I mostly dislike about it, not saying it is bad (Windows 7 is actually really good) but Microsoft is heading in the wrong direction, as I've tried using Windows 8 and I really didn't like it. Sure 3th person software can be used to adjust the issue buts that's just prolonging the inevitable.

Eventually I'm just gonna use it as a gaming platform until that is obsolete thanks to Valve.
I feel Linux distro's are getting more and more mature and that its time to step over to free software. Learn it while Windows 7 can be there to back me up before its too late.

So thanks for the time taking response, it's much appreciated.

---

### Post by oldfred on 2012-09-03
My SSD is 60GB and I have two / (root) partitions of almost 30GB. I use about 9GB including my /home, but am aggressive about moving data to shared data  folders including some of the hidden one's like the Firefox & Thunderbird profiles.

You can share swap if you do not encrypt /home nor hibernate.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
But with 4GB of RAM you will rarely if ever use swap and with an SSD, using  hibernation will not really save you any time booting. 

I have two data partitions. One is NTFS which I started with XP and wanted to share my Firefox & Thunderbird profiles, so I did not have to reboot to have the same email & bookmarks. Now with my SSD I had to change to AHCI and my XP does not work with AHCI so all new data goes into a Linux formatted data partition. I then decided I really do like separate smaller system partitions and separate data partitions.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

