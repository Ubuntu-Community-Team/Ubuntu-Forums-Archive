---
title: "New 64 bit want to go mirror of 32 bit"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by free10 on 2008-04-15
OK bought new quad 6600 intel processor, new board, video card, 4 gigs of memory and tried booting my old slow 80 gig WD drive with Ubuntu 7.10 on it and to my pleasent surprize Ubuntu figured it all out and the system was stable and fast beyond belief on everything.

Now I also had bought a samsung terbyte drive to use with all the new stuff, but when I formated and intalled Ubuntu off the 7.10 disk on to it using the automatic it never gave me the chance to choose anything including 64 bit or 32, and installed 64 bit fine. After playing and looking around at 64 bits and the more limited software I am seeing in the repositories for 64 and I don't want it. And since my slower drive at 32 bit works great is there anyway to just mirror over to the new drive the old one or Disk /dev/sdb - 80 GB / 74 GiB (RO) to Disk /dev/sda - 1000 GB / 931 GiB (RO) and have all settings transferred and info and turn the 64 bit into a 32 bit systems in the process. Only about 37 Gigs are actually the Ubuntu partion on the 80 gig drive.

Ubuntu I find works fast and great with my new hardware with my old 32 bit system and is stable and in fact more stable than the old system hardware and I don't think I would gain enough of a speed boost on graphics/photo work ect to justify the headaches with 64 and the hassel of doing all the install and changes all over again I made already to my 32 bit system to get it the way I wanted it over the last few years and a lot of them I probably forgot or forgot how to do them.

Any suggestions on this? Thanks for any help--Dwight .

---

### Post by Partyboi2 on 2008-04-15
To clone the disk you could use something like
[partimage]("http://www.partimage.org/Main_Page") or maybe
[URL="http://www.brunolinux.com/02-The_Terminal/The_dd_command.html"]dd
[/URL]

---

### Post by free10 on 2008-04-16
> **Partyboi2 said:**
> To clone the disk you could use something like
[partimage]("http://www.partimage.org/Main_Page") or maybe
[URL="http://www.brunolinux.com/02-The_Terminal/The_dd_command.html"]dd
[/URL]

Well I was wondering, if I went in and changed all the "permissions" on the main files on the old and new drive for anyone to read and write to them, and then running off the old drive if I couldn't just copy all the main files on the old drive and then just paste them on the same new file section of the new drive and let is substitute not just the home folder, but all the files/folders and see if that worked. I am just wondering by doing that if it could figure out that it was sitting on a drive with different formatted parameters and a lot more space. Of course if that did work then I would need to go back and change the main folders permissions back to what they were afterwards. Thanks for the info and ideas--Dwight

---

