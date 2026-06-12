---
title: "Switching from WIN2K3 to Ubuntu 7.1 Server"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by AlexP121 on 2007-11-18
I want to start by saying that I have very little experience with any Linux distro, so please be gentle. :-) Anyway, I just decided to install Ubuntu Server on a drive so I can replace my Win2K3 server as it's about to die anyway. I would really appreciate some guidance with this. I am a very low-level admin, just took MCSE classes and had a close friend help me set-up my home/biz network. I have the Win2K3 server, and 3 PC's all running WinXP, I want to remove the server and use Ubuntu as my server to provide internet connection, do the DNS and be a file server, and web server.... bascially I installed ALL of the possible software and now have no idea how to configure it properly, so I don't want to introduce it to my network without tweaking it some. I am considering buying a new box just for this new server. IT will be at least Pentium 4 if not Core 2 Duo and minimum of 1GB RAM, and 256 or 512 MB vid card, the drive the install is on now is a 40GB, but I can add another drive if needed. I run a small computer services company out of my home and I am just starting to hire contractors to do the office work and do the traveling Tech work, which I was doing EVERYTHING prior, but I now have a full time job, but I still want to build my business on the side. If you need anymore information I am more than happy to provide it. Oh, by the way, I have cable internet and a business class router (wireless, but have that disabled) with built in VPN capabilities that supply all the PC's with internet access. 

I am eager to switch over to Linux, but I was not very good with the old DOS command-line thing and it seems like that is just what I am running into again. I can follow instructions excellent, but to try and just explain things, it's hard for me to grasp. I have done a significant amount of research online, but I am very cautious, because this is my company and I cannot afford to let my confidential data be hacked. I have been in business since Sept-Oct 2006 and have struggled to get to where I am now and would be very grateful for any help that you can give. My full time job in working in a law firm in mid-town Manhattan doing hardware support, lol. I am always looking to improve my skills and learn new things, so I figure this is a great opportunity. Again, thanks to all for your help and support.

---

### Post by dhtseany on 2007-11-19
Wow that was a lot of info to process :)

Anyways lets start simple; are you running active directory?

Sean

---

### Post by AlexP121 on 2007-11-19
Yes. I am running Active Directory, DHCP, DNS, WINS and I attempted to set up my Win2K3 server as a file server and for Remote Access/ VPN, but didn't configure the VPN at all. 

Thank you for the help by the way.:)

---

### Post by dhtseany on 2007-11-19
Ok well first to help you get your feet wet with the CLI (Command Line Interface or as my girlfriend calls it "That DOS looking thing" haha) by trying out this tutorial. When finished your server will be a DHCP server. Go through it all the way and let me know your results. If you can't get it to work, just ask and I'll help you through the process.

Things to note:

1. eth0 refers to your first network card that you have. Remember that most everything with computers starts with 0 rather than 1. If you have multiple NICs (or Network Interface Cards) then you'll have eth0, eth1, eth2, etc. until you run out of installed NICs :)

2. Instead of using grep to install the DHCP packages, I'd search around Synaptic. Again, if any of this is confusing just ask.

So yeah, let's get started :)

Sean

---

### Post by dhtseany on 2007-11-19
Also, note the following:

Although it may not be exactly what you're trying to do, check out [this page]("http://blog.saturnlaboratories.co.za/2007/01/01/howto-ubuntu-home-lan-server.html")

Additionally, note the following CLI command that will help you install the DHCP server if you can't find it in Synaptic:
```
sudo apt-get install dhcp3-server
```

Good luck!

Sean

---

