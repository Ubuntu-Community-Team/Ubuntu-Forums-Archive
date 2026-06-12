---
title: "Interesting EeePC Ubuntu Installs?"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Herman on 2008-09-10
:) I'm getting ready to install EeePC Ubuntu in my wife's new EeePC 4G 701, we love it and we already have Ubuntu running it from a USB flash memory stick and everything works great.
There's a slight performance lag when writing to disk in the USB flash memory. I made some tests with benchmarking software, bonnie++, and I strongly think that using reiserfs instead of ext2 or 3 will really speed things up a lot.
I can't decide whether to make a separate swap area or use a swap file either.

Has anyone else made any interesting, or different installs in an Asus EeePC, or have any different ideas?
(I guess I was just born to be different, I hate just doing the same as what everyone else is doing.) :)

---

### Post by fewjr on 2008-11-20
I have been looking at the tripleE Asus computers. I'm leaning towards the 901. The 1st one I saw was a 7" model that has two SD slots, one on each side. One of them was for expanding your hard drive size. When you installed it you can watch the hard drive size change to a larger size. I think thats the one your wife has?

---

### Post by snowpine on 2008-11-20
I have a 900ha, the model with the 160gb hard drive. I am currently quad-booting the following: Windows XP (it came preinstalled), Crunchbang 8.10 (openbox), Debian Lenny (gnome), and Sidux (xfce or lxde). All of them worked out-of-the-box except for Crunchbang, which required an special easy-to-install eeepc kernel from array.org to get the wireless working. 

If I only had 4gb of storage, I would probably go with Crunchbang or Debian Lenny minimal install + LXDE. I installed Lenny+LXDE on a 4gb SDD card, and it only took up something like 1.3 gb.

Good luck! Report back with your findings...

---

### Post by Herman on 2008-11-30
:) I swapped my nice Acer Aspire 3003 WLMi for the EeePC because the EeePC will fit in my lunchbox if I want to take it to work. I think it's the 7" model, but mine only has one SSD slot.
My wife likes the larger laptop better because that one suits her needs.

I'm having fun with the EeePC.

Most experts recommend installing Ubuntu in flash memory using the ext2 file system to avoid the possibilty of wearing out the flash memory due to the file system journal being written to very frequently.
I was doing some research into ReiserFS today and I found out something I didn't know before.
We can easily disable file system journaling with ReiserFS by adding the option 'nolog' to our mounting lines in /etc/fstab.
Unitl now I was running Ubuntu in ReiserFS with full journaling.

Most flash memory is fast to seek and read files from but writing files to disk is slow, especially if there are a lot of small files to write, as in an operating system.
The Reiser File System is up to fifteen times faster for small files, which seems to make up for the slowness of the flash memory in that respect.
Disabling file system journaling gives another even further speed boost.

The downside is, it will be harder to recover the file system after a crash. (No harder than if I used ext2 though probably).

I'm trying it out and I have already been keeping a record of uptime and disk writes with a script that I run before shutdown which contains the iostat command, logging the results to another file.
Now that I have turned off journaling in my Reiser file system I'm going to continue my record keeping and see how many disk writes it saves to have journaling turned off.
I don't keep valuable files in this system so probably for me the extra speed will be the main benefit.
I believe my flash memory will last a considerable time regardless, but that's only my opinion, I'm testing that too. 
For now I'm running the EeePC from a 4 GB USB flash memory stick, not in the EeePC's internal SSD drive. I use a USB hub to plug more USB flash memory sticks all together so I can add disk capacity as I like. All of my flash memory sticks are already getting old, and I haven't succeeded in wearing one out yet.

Regards, Herman :)

---

### Post by brallan on 2008-12-01
interesting thread. I've got an eee 901 and I read on the debian website that they recommended both NOT eliminating the extra small partitions (oops, already wiped them) that came with the xandros default OS:

[http://wiki.debian.org/DebianEeePC/HowTo/Install#head-b80162731ee87164e03d2fb7524bb0a5a45f61fa](http://wiki.debian.org/DebianEeePC/HowTo/Install#head-b80162731ee87164e03d2fb7524bb0a5a45f61fa)

and say there is no need to worry much about the journaling of ext3 tiring out the disk much faster.

I wonder if the best option isn't just to buy a SD card and put the OS on there with the internal Solid State drive as a /home partition. If one day it gets one too many writes, then you can just change it out. Another possibility might be to just run the entire OS from memory, with somethng like the SLAX "run from RAM option". It will certainly work with a gig of RAM.

What about the difference in read/write speeds between the USB flashdrives, the internal flashdrives and the SD drives? I imagine USB must be much slower, isn't it a lot slower booting off a usb stick?

---

### Post by snowpine on 2008-12-01
> **brallan said:**
> 
I wonder if the best option isn't just to buy a SD card and put the OS on there with the internal Solid State drive as a /home partition. If one day it gets one too many writes, then you can just change it out. Another possibility might be to just run the entire OS from memory, with somethng like the SLAX "run from RAM option". It will certainly work with a gig of RAM.

What about the difference in read/write speeds between the USB flashdrives, the internal flashdrives and the SD drives? I imagine USB must be much slower, isn't it a lot slower booting off a usb stick?

I have experimented with installing to USB sticks and SD cards. Both are very slow compared to the internal drive. If performance is at all a concern, install the OS to the internal drive and don't worry about wearing it out. It is designed to be used. 

That being said, there are hacks to reduce writes to the internal disk. My two favorites are 1) don't use a swap partition; 2) mount the /tmp directory to ram instead of to disk.

---

### Post by h4mx0r on 2009-01-03
I got the eeepc 900A the 4GB flash version no webcam. I wanted to go with a very minimal desktop perhaps lxpd or jwm and some other light apps. I think using reiserfs and notail option with noatime is a good idea in general especially for such a small space. What is it like 500mb you save?

The whole reason I instantly thought the eeepc was a genious idea is that the "toram" option sounds like it would work perfectly. You could load the entire system up to memory for added performance. I'm going to try upgrading the memory to 2gb to improve upon this quality. But I don't get how saving things to disk would work right like this do I just put all important stuff in /home and leave that out of ram? That way most settings get written to disk immediately?

One more thing I was thinking of is using a high speed SDHC card in a reiserfs raid0 setup but the differences in the two storage mediums I think would yield a negative performance gain. Although it is good for a /home like mentioned.

Seeing as I don't have a webcam I was thinking of soldering on some infrared led lights to use it with my wiimote. Saw some youtube posts of someone playing tremulous on their laptop and I was like omg I am totally going to finally do that. [http://www.youtube.com/watch?v=oK9AGpI38tw](http://www.youtube.com/watch?v=oK9AGpI38tw) Because the eeepc size and cooling you can plug it up to any sort of monitor/projector quite easily... :)

---

### Post by bluester on 2009-05-16
_**My system:**_
Asus 1000HE (Excellent NetBook) 
64G Patriot Warp SSD (most my applications are here) 
2G G.Skill RAM (You will need it for this system)
PNY 32GB-sdhc class-4 (My data and movies reside here)  
Ubuntu 9.04 (The OS of choice)
_**Using:**_
[SSD Optimization on Ubuntu]("http://starcubetech.blogspot.com/search/label/SSD")
[Eeeasy Scripts (Juanty)]("http://forum.eeeuser.com/viewtopic.php?id=65606/")
[Multimedia Guide (Jaunty)]("http://ubuntuforums.org/showthread.php?t=766683")

I posted a review on newegg.com (it has not posted as of yet).
[U][B]
User noticeable performace enhancements:[/B][/U] 
Boot time : approximately 35 seconds
Cooler - I can keep the notebook in my lap.
Quieter - Fan speed remains low.
Faster - time from double click to launch is noticeably faster.

Uptime system-on-battery time increased - though only about 45 minutes.
I was getting 6hours and 15 minutes average with wireless on!
Now I am getting 7 hours average with wireless on (7h 25m tops)

In addition I installed the [2.6.29.1-3e]("http://www.informatik.uni-bremen.de/%7Eelmurato/EeePC/") kernel which improved wireless performance.
The eeeasy-scripts developed by [elmaruto]("http://forum.eeeuser.com/viewtopic.php?id=65606") are just what the doctor ordered!
The [SSD write enhancements]("http://starcubetech.blogspot.com/search/label/SSD") were well needed - my HDD light barely come on now.
The [multimedia upgrades]("http://ubuntuforums.org/showthread.php?t=766683") were also nice - Flash and Java are better - not perfect by any means.

_**Some other sites that may be of interest:**_
[URL="http://www.blogsdna.com/372/21-aboutconfig-hackstweaks-for-firefox-3.htm"]
21 About:Config Hacks(Tweaks) For Firefox 3[/URL]
[Howto; Firefox profile in RAM for increased speed and stability]("http://ubuntuforums.org/showthread.php?p=7057921#/")
[Sound Solutions for Ubuntu 9.04 (Jaunty) Users]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")
[Quickzi: How To Remove Older Kernels from Ubuntu]("http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/")
[General Troubleshooting in Linux]("http://www.nixtutor.com/linux/general-troubleshooting-in-linux/")
[All the Best Linux Cheat Sheets]("http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/")



Thanks for reading my post!

---

### Post by robytrevi on 2009-05-16
I'm trying an asus eeepc 900a with Ubuntu Jaunty. I read this guide: [http://forum.eeepc.it/viewtopic.php?id=7297&p=1](http://forum.eeepc.it/viewtopic.php?id=7297&p=1) But i've got a problem with wireless card. Wireless conection works for the first about 10 seconds, then it doesn't work. If I try to ping the router it doesn't answer (Destination Host Unreachable).
What can i do?

---

### Post by pauna on 2009-05-16
I have Eee PC 901 with 4+16GB SSD's. 1GB memory, although I am thinking of adding another 1GB. The interesting feature for this machine is that the 4GB SSD is much faster and the bigger SSD is slower.

Installed OS is Jaunty Netbook remix, although I reverted to the classic GUI soon after installation. Jaunty is the first Ubuntu version which pretty much works out of the box without special kernels, modules or major tweaks. Some scripts need to be installed and some parameters need adjusting, but that's small peanuts.

I'm running / on the 4GB (ext4) and /home on the 16GB (ext3). I don't have swap and it hasn't bitten me yet, this machine is for lightweight use only.

Since this is my secondary machine, I have taken the approach that if/when the SSD write cycle count is maxed out, it's time to buy another cheap netbook. So that's why I'm using a journaling FS on a SSD. Moreover, I know ext4 is not yet recommended for general use, but if ext4 decides to go postal on me, I can always reinstall the / partition. All my important files are on /home, which uses the more stable ext3 and besides it gets backups. Your mileage may vary.

Anyway, I think this machine is great for on-the-road communications needs. I highly recommend the 9" version, the 7" versions are pretty cramped in their display.

---

### Post by pauna on 2009-05-16
> **robytrevi said:**
>  But i've got a problem with wireless card. Wireless conection works for the first about 10 seconds, then it doesn't work.

I don't have a 900a, but here are a couple of suggestions you could try: [http://blog.threesheets.org/2009/05/problems-solutions-with-ubuntu-jaunty.html](http://blog.threesheets.org/2009/05/problems-solutions-with-ubuntu-jaunty.html)

---

### Post by robytrevi on 2009-05-17
I have tried to connect to another network and the connection seems works.
Maybe I have some problem with my network. I'll investigate.
Thank's a lot for the attention.
Bye

EDIT: I think that there's an incompatibility between eeepc900a and router netgear

---

