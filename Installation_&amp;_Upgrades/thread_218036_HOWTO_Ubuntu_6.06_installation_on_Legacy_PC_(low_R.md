---
title: "HOWTO: Ubuntu 6.06 installation on Legacy PC (low RAM)"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by swamytk on 2006-07-18
> Oh, God! Thanks a lot for making me learn more on Linux!
Oh, Ubuntu! Thanks a lot for giving me a stable complete system!
oh, My Wife! Thanks for caring me to work over night!
Oh, My child! Thanks for motivating me with your flash smile!


It is a lot of pain and patience to install Ubuntu 6.06 Dapper Drake LTS on my legacy (to some extent) machine. My machine is of PIII/192MB/20GB/Intel-D815-Chipset. The real problem of installing Dapper on this machine is due to low RAM. I was able to run Live CD of SimplyMepis 3.4.1.rc1 in excellent speed and able to install during live cd session without any issues. But Ubuntu's installation was not so easy. I had discussed with Ubuntu forums on compatibility of this machine with Ubuntu. Many Ubuntians had warned me and wished best of luck. Yes, it is true. I had a lot of patience to install Ubuntu. But after installation, it is -breezy- -breezy- -breezy- that is what I can say. Everything (yes, ***every hardware***) worked out of box with nice configuration. To my surprise, all applications are flying like jet. I don't find any difference between working on PIV/512MB system and this legacy system. You might have read so many reviews about Ubuntu desktop system, so I need not to tell you more on that. But I want to summarize some of the important precautions/steps/consideration while installing Ubuntu 6.06 on any legacy system with lower RAM.

Upto Ubuntu 5.10, we did not have such installation problem on legacy machine. But since Ubuntu 6.06 (Dapper Drake) has become Live CD (**complete** live cd), it is not able to cope up with the lower RAM. Here are tips to install Ubuntu 6.06 Desktop  successfully on a low end RAM system. What I am suggesting here are more safer to install and increase the chance of successful installation.

1. Boot your machine with Live CD either with option-1 (Start or Install Ubuntu) or option-2 (generice video driver mode). Ensure that you are getting desktop after a few minutes.

2. Don't click Install icon on desktop. This installation tool is a great one, but not yet stable. This tool in turn call GParted for disk partitioning while installtion, which is also not stable. Don't run GParted which is available on System->Administration menu also. In my three installation of Ubuntu 6.06, I have faced problem of crashing of GParted consistently. Let us utilize fdisk for partitioning work.

3. Press Ctrl+Alt+1 to go to console. You will have already live cd user logged in shell prompt.

4. Try to allocate a full hard disk for Ubuntu installation. This technic is to avoid calling GParted in installation wizard. (Console work: You no need to do anything on console)

5. If you want to partition the hard disk for other OS also: Make sure that you have a large free space (not partitioned) available for Ubuntu installation (min 2GB). For example if you want to allocate 10GB for Ubuntu, create a 10GB free space by deleting the existing partition. No other free space size on this hard disk should be more than this 10GB of free space. This technic is to avoid calling GParted in installation wizard. (Console work example: $ sudo fdisk /dev/hda)

6. This is very important. Since live CD creates a root file system on RAM, the installation wizard has no enough RAM to run. This is the most common reason for installation hang. To avoid this we can create a temporary swap partition of atleast 256MB (512MB is fine). (Console work example:
	(a) Create swap partition: $ sudo fdisk /dev/hda
	(b) Make swap file system (hda5 is swap file system in this example): $ sudo mkswap /dev/hda5
	(c) Add swap to the running system: $ sudo swapon /dev/hda5
	(d) Make sure that swap is live: $ sudo swapon -s

7. Press Ctrl+Alt+7 to go to desktop. Don't run any other program in desktop (please cool, wait! don't listen music while running installation). Double-click install icon on desktop to run Installation wizard. Now it should not take more than 20 to 30 minutes for entire installation. 

8. Ubuntu will create / and swap partition automatically. If you want seperate /home partition, you can add it any time after installation.

[COLOR="Black"]Bottomline:[/COLOR] 1. Avoid running GParted (use fdisk). 2. Make swap file system available for running live system.

[COLOR="Red"]Top moral:[/COLOR] **Linux makes you to customize your installation according to your hardware configuration. It does not warrant any strict configuration. It is all about choices and freedom.**

---

### Post by SkyNet2029 on 2006-07-18
Excellent info . I too run many (6) legacy machines at home of the AMD K63Dnow 350-500Mhz variants. Yes, they are a blast (and dirt cheap to boot!) These machines vary in memory from the least capable - 32MB.. That's where my 20GB fat32 storage resides, all the way up to a whopping 512MBRam/350Mhz/80GB setup. 
It has also been my experience as to the failing of an installation simply due to qtparted gobling up my resources. I just wanted to add that one of the things I have found realy useful is to fire up an ALT+F1 window, run top, and smite down that which I don't need by way of a #killall eye_candy_bloat_app_name_here.  The largest waste of resources I have noticed is the bluetooth daemons and Cupsd, if anyone is interested.. I mean, the main point of an installation is to umm, Install. I hadn't actually thought of avoiding qtparted altogether though(using the Kubuntu liveCD's), silly me. 
Yes, I know that KDE is pretty much thrashing on some of these machines, but there are ways to get it up and running without watching all of your hard partitioning work get tossed simply due to a lack of system resources. Anyway, I am glad to see that I am not the only one here trying to slap some sense into the installation routine.

---

### Post by swamytk on 2006-07-18
> **SkyNet2029 said:**
> The largest waste of resources I have noticed is the bluetooth daemons and Cupsd, if anyone is interested..
Yes, you are perfect. Not only during installation, after that also I restrict unnecessary services. Actually I don't run most of the Ubuntu default services @ home pc. My home pc is not connected to network, internet, printer, scanner, bluetooth , no raid, no ntp service, no nfs, no samba... no.. no.. goes on.. Once I disable all these services ($ cd /etc/init.d && sudo mkdir backup; sudo mv --unnecessary-services-- ... backup), now my PII/192MB starts in 30 seconds.

---

### Post by anil_robo on 2006-09-18
I installed Ubuntu Dapper LTS on a [legacy machine]("http://stooge.myftp.org") via install CD, and it took about 18 hours for the 350MB install. But it runs faster in server mode than I ever expected! :)

---

### Post by DikenliTel on 2007-02-15
I have exactly same situation. I have started a new topic [here]("http://ubuntuforums.org/showthread.php?t=361436") but nobody can understands me like you :) My disk structure is:

Primary master ide (maxtor 40 gb) and partition table is:
 [IMG]http://img128.imageshack.us/img128/8046/ads305zrx8.jpg[/IMG]

(the picture is taken from partition magic under windows xp)

Now, could you please tell me how to install xubuntu 6.10 in that system? Thanks a lot...

Note: ext3 partition and swap partitions are empty.

---

### Post by DikenliTel on 2007-02-16
===Problem Solved===
I installed with an alternate installation cd and now, i'm doing great :guitar: 
Thanks everyone who was considered about my situation...

---

