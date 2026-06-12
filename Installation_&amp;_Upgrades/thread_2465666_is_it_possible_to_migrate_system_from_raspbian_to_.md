---
title: "is it possible to migrate system from raspbian to ubuntu?"
date: 2021-08-08
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2021-08-08
I have been running a raspberry pi as a media file server but it keeps eating sd card so I am migrating everything to a miniPC. 

Since I can't just transfer the entire system (I was told that an x86 system can't run raspbian) is there any way to transfer the the programs, databases and settings from the raspbian system over to the Ubuntu 20.04 system? Or am I going to have to re-install everything manually? Please don't say manually....

---

### Post by TheFu on 2021-08-08
You can't transfer programs. Those are compiled for ARM, not x86-64 computers.

What you can do is backup the list of installed packages, data, and user stuff into a fresh install of Ubuntu.  I suspect some of the package names will be different, but I don't know.  There will be manual steps. No way around that.  Look through my backup/restore threads here.  You want to know what to backup, so the restore is as painless as possible onto a completely different system.  I've never gone from ARM --> AMD64, but I have gone from 32-bit to 64-bit Intel.  That's the same issue.

I use raspberry Pis (running OSMC) as silent playback devices and an old Celeron as a media server.

---

### Post by rebeltaz on 2021-08-08
> **TheFu said:**
> You can't transfer programs. Those are compiled for ARM, not x86-64 computers.

What you can do is backup the list of installed packages, data, and user stuff into a fresh install of Ubuntu.  I suspect some of the package names will be different, but I don't know.  There will be manual steps. No way around that.  Look through my backup/restore threads here.  You want to know what to backup, so the restore is as painless as possible onto a completely different system.  I've never gone from ARM --> AMD64, but I have gone from 32-bit to 64-bit Intel.  That's the same issue.

I use raspberry Pis (running OSMC) as silent playback devices and an old Celeron as a media server.

That's what I figured. Thanks.

BTW - Your setup is similar to mine :)

---

### Post by MAFoElffen on 2021-08-08
Sort of easier than that in some ways... Like TheFu said,,, but a bit easier. Some background first...

Raspbian is based on Debian, so then main packages will be  the same or similar to Ubuntu. The differences will be that some of them are specific to ARM, while some are just specific to the Pi itself. 

The config files for your main applications will we the same. Database files will be the same. Etc. 

You already have the data. the quickest way to get a backup is to take it to your new Ubuntu Install on your new or other system, take your MicroSD card from your Pi, put it into a USB Flash Card Reader... Insert it into a USB port of the target PC... Open up nautilus. There will be two mounts from the Card- Boot and Writable. The Writable is the mount you want to go to. Copy whatever you need to somewhere, where you can take your time to pick out what you need. For me, this is how I backup the multiple SD cards I have for my Pi. By just directly reading it.

So no. Not all manual. And there are ways to make it faster and less painless.

Eating SD cards? Meaning, is it losing power and not getting a clean shutdown of the system image? Pi uses a compressed filesystem, which on shutdown tries to re-compress any changes in two separate pivot shutdown jobs... It just needs to shutdown cleanly, so that the filesystem is clean. 

Or do you not have a case without a fan, where the cards are overheating?

---

### Post by rebeltaz on 2021-08-08
> **MAFoElffen said:**
> Sort of easier than that in some ways... Like TheFu said,,, but a bit easier. Some background first...

Raspbian is based on Debian, so then main packages will be  the same or similar to Ubuntu. The differences will be that some of them are specific to ARM, while some are just specific to the Pi itself. 

The config files for your main applications will we the same. Database files will be the same. Etc. 

You already have the data. the quickest way to get a backup is to take it to your new Ubuntu Install on your new or other system, take your MicroSD card from your Pi, put it into a USB Flash Card Reader... Insert it into a USB port of the target PC... Open up nautilus. There will be two mounts from the Card- Boot and Writable. The Writable is the mount you want to go to. Copy whatever you need to somewhere, where you can take your time to pick out what you need. For me, this is how I backup the multiple SD cards I have for my Pi. By just directly reading it.

So no. Not all manual. And there are ways to make it faster and less painless.

Eating SD cards? Meaning, is it losing power and not getting a clean shutdown of the system image? Pi uses a compressed filesystem, which on shutdown tries to re-compress any changes in two separate pivot shutdown jobs... It just needs to shutdown cleanly, so that the filesystem is clean. 

Or do you not have a case without a fan, where the cards are overheating?

I've still got the pi running right now so I'm doing scp copies for the configuration files I need. It's just that I have the memory of a guppy, so every time I rebuild this (or any) system, I have to figure out how to get everything working again from scratch. 

As for the cards, I don't think it's a shutdown issue because the system will be running and then just ... blughh.... It acts up so I reboot it. When I do (using *shutdown -h now*) it shuts down but will not come back up. Sometimes I can take the SD card and do a filesystem repair on it and it'll work, but most times, the card is completely unrecognizable.

I never thought of overheating. The pi is in a case, but it has vents. I have three other pis running the same cases and they don't seem to have an over heating issue. Two run as OSMC / Kodi media players while the third runs as a simple web server for a couple of sites I host.

---

### Post by TheFu on 2021-08-08
I have 2 R-pi systems.  They run OSMC, but I don't keep any media local and don't use the OSMC/Kodi DB at all. It is just the playback interface and connects into a DLNA server on the network.  I've had cheapo microSD cards in both for many years. So long that I don't remember when.  1 finally died about a year ago, so I splurged $9/ea for a few Samsung Endurance  32G microSDs. I only need 8G - perhaps 4G - but they don't sell them that small anymore.

My r-pis also get used as mpd servers and playback music, also from other storage, never local. I probably listen 4 hrs a day.

I don't have a v4 Pi. The v2 and v3 I have already do more than I need, but I did add a v4 to my Xmas list last year.  Guess I was naughty. Maybe this year?

I've never run Ubuntu on a Pi. I don't see the point. Any desktop would be too slow to for my use and I'm just not that interested in seeing what CAN be done anymore. I have plenty of hardware and need to replace 2 systems for a newer one when low-end GPU prices drop and Ryzen CPUs become $100 cheaper than today.

I know that heat CAN be an issue for SD storage - just never seen it myself. I don't leave devices in a hot car - actually, I don't take the vehicle out when it is too hot, so it is garaged 99.99% of the time.

---

### Post by MAFoElffen on 2021-08-09
I have a Pi4 8GB and love it! Yes, heat can kill them. Especially cheap cards. I got a case with vents, a good fan and _heat sinks_ off Amazon for less than $20. I feel it was a very good investment.

I have a few cards... Each setup differently. Right now writing this from that, on Ubuntu Desktop. Funny. Some things run "very well" if I run a Desktop. Other things just suck. Forget about video playback from the desktop. LOL. You'll just be disapojnted. But to be expected. It's just got a framebuffer.

Other's, well seem to actually run very well. My son talked me into it. Mate was originally developed for PI. It has a lot of the hacks already. And the person that supported it took a lot of the hacks from other Distro's and port them to Mate. That is why that is so lightweight.

Mine? Mostly testing KVM 6.x and nested Virtualization on Arm. That and testing 21.10 Dev ARM64.

---

