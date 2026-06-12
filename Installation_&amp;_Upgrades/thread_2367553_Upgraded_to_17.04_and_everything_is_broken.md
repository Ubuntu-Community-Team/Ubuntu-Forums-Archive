---
title: "Upgraded to 17.04 and everything is broken???"
date: 2017-07-31
forum: Installation &amp; Upgrades
---

### Post by JohnBG on 2017-07-31
Had 16.04.2 32 bit installed and working fine.  Dual boot with Windows 7 32 bit.  Decided to upgrade to 17.04. At this point looks like a big mistake?  Network connection keeps dropping in and out.  Firefox cannot load any websites.  Cannot install the Grub Customizer. Cannot install Telegram Desktop.  System is pretty much useless. So I used the "Boot Repair Disk - Ubuntu 14.04 - to remove 17.04.  Then repaired the boot for Windows 7 32 bit.  Booted right into Windows working fine - no network in and out - everything fine with Firefox and 4 other web browsers in Windows 7.  Decided to reinstall 16.04.2 and got the same results = network in and out - Firefox no websites loading - Cannot install the Grub Customizer - Cannot install Telegram Desktop - did not go any further - discouraged???  Any Ideas, or suggestions, or postings, or references???  Really enjoy the tremendous power of Unix i.e. Linux.  Makes Windows a wimp.  It is more complex and challenging like solving this installation cycle deviant behavior!  When I first installed 16.04.2 it went very smooth and everything worked fine - it spoiled me! Now???

---

### Post by Autodave on 2017-08-01
When you got to the screen that asked you whether you wanted to reinstall or wipe Ubuntu1? and install, which did you choose?

Keep in mind that 16.04 is a long term service release (LTS) and will be supported for 5 years with updates. The next LTS will be 18.04 (the first 2 numbers tell you the year and the second two the month. Any release between those two will be 6 month releases (only supported for 6 months). That means that if you install a short term release, in 6 months you will have to install or upgrade to the next short term release.

Personally, I use only the long term releases. That prevents me from having to go through what you are going through right now. You will find many people on here that will tell you that they have never had a problem upgrading from one release to another. I, however, am one who will tell you that I have never had any luck doing that. The last time I tried, I had only one of thirteen machines work. And, I have a very simple install: no other PPAs than what Xubuntu came with.

---

### Post by JohnBG on 2017-08-01
I upgraded 16.04.2 to 17.04 and network became intermittent and Firefox could not load any sites with the network working. Did a straight update. Then did a wipe Ubuntu and install. Went back to 16.04.2 did the same?  Messed with the network settings "By the book" and did not fix anything.  Windows 7 works fine.  Very disappointing! Do not know where to turn?

---

### Post by BenginM on 2017-08-01
Hiya , welcome to the forums ..

it's unfortunate that you had to experience this, and your frustration is understandable ... what do you mean by Messed with the network settings "By the book" !

maybe you want to open a new thread in Networking & wireless section , or maybe a staff member might move this one there .. and state the Network issue ... you'd have a better chance having assistance if you share more information about the issue you're dealing with.

---

### Post by JohnBG on 2017-08-01
By the book = followed the instructions given in the users manual .pdf file.  This makes no sense the first time I installed 16.04.2 I had no problem whatsoever and used it for some time up until I tried to upgrade to 17.04?  Windows 7 works fine no network problems whatsoever so I do not think it is the Network Card?  Perhaps wiping the Linux partition clean with a partition management utility would make a difference?

---

### Post by BenginM on 2017-08-01
do you care to share this user manual , also 16.04.2 is an LTS release unlike 17.04 .. do you really need to be rolling with 17.04! I don't see how formatting the partition would help with a network problem , but it's an option and a good practice for a fresh install .

---

### Post by wildmanne39 on 2017-08-01
There are a couple of bugs in networking in 17.04, create a thread in networking for the internet issue only tell us if wifi and ethernet are both not working, if you have access to wifi and ethernet if they were. If you can click on the wireless script in my signature and post the results from it if you have a wifi connection also it would be very helpful.

Thanks

---

### Post by JohnBG on 2017-08-01
I only have Wired Ethernet no wireless. Firefox will fetch sites during search but no sites will load - very strange indeed?  After using Boot Recovery Disk to remove ubuntu and repair the boot sector I Used Mini Tool Partition Manager to remove partitions and merge them and installed 16.04.02 fresh after this - same problem???

---

### Post by BenginM on 2017-08-02
with the wired connection , are you able to ping google.com ! and in firefox enter the ip address 72.14.207.99 , and hit enter.. does it load !

are you able to $ sudo apt update ..!

and $ wget [http://mirrors.mit.edu/ubuntu/ubuntu/ls-lR.gz](http://mirrors.mit.edu/ubuntu/ubuntu/ls-lR.gz)

---

