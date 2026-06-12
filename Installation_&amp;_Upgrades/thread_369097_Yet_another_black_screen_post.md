---
title: "Yet another black screen post"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by OrangeOrb on 2007-02-24
ive had ubuntu 6.06 installed on my system a while ago and i everything was just dandy up until i tried to update my video card drivers with that Envy program that is out now. After i installed the drivers the pc rebooted to an odd looking screen then switched to the login screen with an ungodly high resolution. and it couldnt login due to an error. I dont know a lot about linux (im still a newb) so i booted up my xp cd and told it in the recovery console to fix the master boot record. I went back into windows and formatted my ubuntu partitions clean, and went on to try another distro. I tried out Xandros for a while, didnt want to pay any money for it so i decided i wanted to try ubuntu again. I fixed the mbr and reformated my linux partitons again. I popped in the live cd and selected the option install/run. It went to the screen with the loading bar, loaded. Then all i got was a black screen, no cursor, no nothing. I thought maybe something was wrong with the cd so i tried it 2 other computers i have and it worked just fine. So i dl'd version 6.10 and it couldnt run it either. Then i got pissed and downloaded the PcLinuxOS live cd. Guess what? BLACK SCREEN! and also guess what? It works on my other f'n systems! By that point i was really angry so i dl'd the full complete dvd ubuntu 6.10 install. I selected the option to install in text mode. It installed the os just fine. i was like hells yeah! but when i selected ubuntu in the grub menu it went to the loading bar screen, it loaded up and then the screen goes BLACk AGAIN! ARGHHHHHHHH!!! Why the hell is my computer doing this? here is my specs:

Abit An7 nforce 2 motherboard
Atlon xp 2500+ mobile (OC'd to 2.3ghz)
ATI Radeon X850 XT PE
1 GB ddr3200 Kingston HyperX ram
1 Western Digital Cavier ATA 100 120gb hard drive
1 Seagate Barracuda 7200.8 Sata 300gb hard drive
1 NEC CDRW-DVDRW combo burner
NEC 19" 90GX2 lcd monitor
dual-boot system with Windows XP
Both OS's are installed on the Western Digital drive

Ubuntu will let me boot into recovery mode from the Grub menu just fine, but i have no clue on what to do from there. Right now im typing on my wife's pc and im letting mine just sit there and try to load up ubuntu. My hard drive light has been blinking for the past 20 min. the screen is still black and nothing so far is happening. if there is anybody out there who can help me, please do. Or if any of you have had the same problem, let me know. thanks.

---

### Post by Herman on 2007-02-24
Well I'm not 100% sure form your description if this is your problem exactly or not, but take a look at this link and see if it helps you at all,             [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")

Regards, Herman :)

---

