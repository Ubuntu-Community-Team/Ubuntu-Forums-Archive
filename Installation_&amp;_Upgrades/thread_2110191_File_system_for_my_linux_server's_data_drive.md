---
title: "File system for my linux server's data drive"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by Litzner on 2013-01-29
I am considering putting a Linux distro (haven't decided on which yet) on my server instead of Win 2008 RC2.

The server will have a SSD for the boot drive, and a 6TB RAID 10 Array for the data drive. 

The data drive has to be accessible (both read and write) from a Windows box as it will be a network drive assigned to Windows computers. Linux also has to be able to read and write to it, as I will use the server to download large files to it.

This server will be used to stream media to a PS3, and/or directly to the TV, and maybe a XBMC box some day.

What filesystem should the data drive be in to best accomplish this?

---

### Post by darkod on 2013-01-29
It will be shared on the network with Windows through a Samba share, so from windows point of view the linux filesystem is not important.

The general filesystem to use on the server these days is ext4. If you have specific data, like majority of big files, or small files, there might be other that are more efficient. For mixed data it seems ext4 is still the way to go.

---

### Post by tgalati4 on 2013-01-29
If these are "green" drives I would use ext2, keep the drives separate--Just a Bunch of Disks (JBOD), use rsync to periodically mirror the drives (once a night or once every few days).  Most important, get a metal-cased UPS.  Plastic ones melt and catch fire.

Ubuntu server with nfs, samba, mediatomb, ushare would get you 90% of what you need.

---

### Post by Litzner on 2013-01-29
Is there any reason not to move from Windows 2008 RC2 to a Linux Distro on it?

It will also sometimes perform "Internet Connection Sharing" I often did this in Windows to push a wireless signal through my net work if my internet was down.

---

### Post by tgalati4 on 2013-01-29
It's hard to recommend a home server setup without a lot of details:

How many users?  How many simultaneous users?
Music streaming?  Video Streaming?  Photo Streaming?
Nightly backups from laptops to the server?  Nightly backups from desktops to the server?  Nightly backups within the server?  One offsite backup solution?  Running a website?  Running a content management system?  Monitoring your home's security?

I'm not sure how you share a wireless connection if your internet is down.

If Windows2008RC2 does everything you need then keep it.  I haven't used Windows since Win98, yet I constantly get virus-riddled/crippled machines with WinXP, Vista and Win7 so I'm forced to relive the nightmare that I awoke from a decade ago.

The only reason to keep Win2008 is if Microsoft pays you to say:  "Litzner recommends Microsoft Windows 2008 for homeserver use."  In fact, that should be your signature line.  (But only if they pay you.)

---

### Post by Litzner on 2013-01-30
Not many users will be logging into or doing anything directly on the server, just me, but I would like to have two different accounts/user running at the same time. One for running a XBMC client on the TV it is connected to, and one for me to get in and manage large downloads I queue up on it, rather then using my gaming rig to manage those.

It will be used for video and music streaming.

There will be no computers backing up to the server, at-least not directly. The server will have a RAID-10 array for it own data protection.

I have a 3 ft parabolic WiFidish mounted off my back deck that I use as a backup internet solution.

---

### Post by darkod on 2013-01-30
In general I think linux servers work more reliably than windows servers. If ubuntu can do what you need, go with it.

On the other hand, if you need some specific software/tools that run much better on windows, you can stick to it especially if you already have a licensed copy.

---

