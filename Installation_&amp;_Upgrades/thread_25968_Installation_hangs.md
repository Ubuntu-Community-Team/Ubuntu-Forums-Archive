---
title: "Installation hangs"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by Unfug on 2005-04-11
Hello,

i read a lot of Ubuntu and its look great, so i decided to install it on my Pc.
I download Ubuntu 5.04 amd64, because Pc is AMD64 (Winchester).

So now in the Installation , after choose HDD Partition and copying files there is a "CHECK".
CD-ROM Check , and so . 
And then there is Network Directory Check. 
The Progress bar is 50% and nothing will happen.
I choosed Language German (because iam ). So can you help me? 
So here is my Specs:

Amd 64 3000+ (winchester)
Asus A8V 
Radeon 9550 Gecube (speedy edition).
1GB Infineon Ram
CyberDrive CD-Writer
Samsung DVD-Rom (no WriteR)

No other cards in the pci slots. Thanks to you

I hope my english is not to bad :roll:

---

### Post by iom on 2005-04-11
hm. interesting. the very same thing happened to me, so i went through the installation procedure again and the second time it succeeded. however, i didn't figure out what the problem was.

---

### Post by iom on 2005-04-11
the very same thing happened to me, same screen, same 50%. well, i didn't figure out what the problem was (it could be that repository server didn't respond in time or sth like bad connection...) so i went through the whole procedure again. this time, it succeeded.

---

### Post by arctic on 2005-04-15
this guy seems to have the same problem [http://www.ubuntuforums.org/showthread.php?t=27145](http://www.ubuntuforums.org/showthread.php?t=27145)
and me, too... after replacing an old 40 gb hdd with a new 160 gb hdd, i tried to reinstall the system with the cds that i already used on my old box. and now, it always hangs at those bloody 50%. several reinstalls didn't help yet. and the console is not giving any useful information. i will try to install it once again with disabled network-stuff (dhcp can be configured later), maybe that helps to get rid of the problem.
oh.. and i do not think that it is server-related. i tested them from another box and they worked okay.

---

### Post by arctic on 2005-04-17
okay, i got the install complete this time. i simply hit "F1" at the boot screen, then typed "expert" in order to start the install in expert mode. 

most critical stuff is already "preselected" for you, so if you are not familiar with debian systems, you won't be lost that much and will head straight to your dekstop-installation. while installing the system, you go step by step (auto advancing is turned off). thus, you can skip the repository testing with apt and log into your system. 

after that, once you are logged into your new system, you can start the dhclient from a terminal as root/superuser, assign dns-servers and activate your apt-get mirrors. it took me only five minutes extra to get the machine running. :)

good luck to you, guys.

---

### Post by raamdev on 2005-04-28
Is it really hanging, or just taking awhile?

I was having the same exact issue; the system seemed to hang at "Testing network repository". The first time this happen, I suspected that it might be trying to connect to the net, but was unable to because my laptop wasn’t connected. So I hooked up my Ethernet cable, restarted the installation process and manually configured the network settings when the installation process prompted me. But again, it seemed to hang at the same spot. 

I noticed some activity on my NIC light, so I decided to just let the laptop sit there for awhile and see if anything happens. To my surprise, after about 3 or 4 minutes it actually passed the Testing network repository and after taking a little while on the next step, it continued with the installation. 

Bottom line: Hook it up to the internet during the install process, and be patient when it seems to take forever!

---

### Post by arctic on 2005-05-01
be patient when it hangs forever... lol... my box was frozen like hell. no reaction after four hours. :D

---

### Post by kxb on 2005-05-16
Also had this problem while installing from behind a proxy server (not sure if that is related or not), and in somewhere between 5-30 minutes, it moved on to 75% complete with message "Testing security update repository..."  Hope it finishes so I don't have to start all over.

---

### Post by matthiar on 2005-05-16
Hi all -

I had the same problem and I finally gave up on Ubuntu because it was soo frustrating when it was supposed to be so easy !!

Anyway, due to BIOS limitations I have found that using a /boot partition within 1024 cylinders, then throwing everything esle onto / and using LILO to boot from the MBR will work fine on this box. 
How can I tell Ubuntu to go this route?
Seems even the expert options "help" you a little too much ...
This does not seem like an extremely odd thing to do or does it?
Pointers appreciated and I will try this distro again!

Regards
Matthias

---

