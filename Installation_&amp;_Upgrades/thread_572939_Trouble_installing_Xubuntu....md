---
title: "Trouble installing Xubuntu..."
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by ~Maxx on 2007-10-11
Hi all.  I'm a noob trying to install Xubuntu on an older PC (Compaq w/ Pentium II, 398MHz, 256MB RAM).  The install hangs up at 15% during *detecting file systems...* and pops up the following error message...

> [I]The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted

/media/New\040Volume

Please close any applications using these mount points

Would you like the installer to try to unmount these partitions again?[/I]

Numerous attempts to install have produced exactly the same result.  Should I try a different hard disk?  I also noticed that when I boot Xubuntu from disk on this machine the top and bottom tool bars do not appear.  It's probably nothing, as they do appear correctly when I boot the disk on my main pc - but I wondered if this was a sign of possible compatibility issues.  

Thanx for any advice.  All the best!

~Maxx

---

### Post by ~Maxx on 2007-10-11
Sorry to bump my thread, but I'm having no luck with this issue on my own.  I tried using the manual partition option, but after setting the options and clicking "forward" the process stalled and seemed to do nothing from the start (I let it go for a good half hour).  Anyone have any ideas?

Thanx again...

~Maxx

---

### Post by louieb on 2007-10-12
Saw your link to this thread. 256 MB ram is marginal for the xUbuntu live CD. To install use the alternated install CD.  I't should run ok once installed on the hard drive. I've got xUbuntu on a P2 400mhz, w384mb ram. and it does ok.

---

### Post by PmDematagoda on 2007-10-12
Try installing Xubuntu using the safe graphical mode in the Live CD menu, but it will work on 256Mb RAM louieb, I myself installed Xubuntu on a 3.0Ghz Celeron, 256Mb, integrated VGA computer, ofcourse the specs are far more powerful than ~Maxx's but the Live CD still ran very slowly due to the 256Mb RAM, so I started the Live CD up using safe graphical mode and it ran faster. 

By the way, even I faced the problem of no top and bottom bar on the same computer while it was running on the normal Live CD mode, but this cleared up when I started using safe graphical mode of the Live CD and after installation, so you should not have any issues concerning the top and bottom bars after Xubuntu installation.

---

### Post by ~Maxx on 2007-10-14
> **louieb said:**
> Saw your link to this thread. 256 MB ram is marginal for the xUbuntu live CD. To install use the alternated install CD.  I't should run ok once installed on the hard drive. I've got xUbuntu on a P2 400mhz, w384mb ram. and it does ok.

> **PmDematagoda said:**
> Try installing Xubuntu using the safe graphical mode in the Live CD menu, but it will work on 256Mb RAM louieb, I myself installed Xubuntu on a 3.0Ghz Celeron, 256Mb, integrated VGA computer, ofcourse the specs are far more powerful than ~Maxx's but the Live CD still ran very slowly due to the 256Mb RAM, so I started the Live CD up using safe graphical mode and it ran faster. 

By the way, even I faced the problem of no top and bottom bar on the same computer while it was running on the normal Live CD mode, but this cleared up when I started using safe graphical mode of the Live CD and after installation, so you should not have any issues concerning the top and bottom bars after Xubuntu installation.

Thanx for the replies folks!  I was afraid I'd have to give up on Xubuntu.  I'll give these suggestions a shot and post my results.  BTW - I should have the RAM updated to it's full potential (384Mb) within a few days.  Just waiting for it to show up in the mail.  Hopefully that will count toward some improvement.

Thanx again!

~Maxx

---

### Post by ~Maxx on 2007-10-15
Well...  Utter failure again it seems.  Booting and installing from "safe" mode produced the same results as previous attempts.  So I downloaded the alternate install file, checked the md5sum, and made the disk with InfraRecorder.  While attempting this install I received the following errors...

> Warning:
file:///cdrom/pool/main/v/vim/vim-common_7.0-164+1ubuntu7_i386.deb was corrupt
> warning:
couldn't download package "vim-common"
> warning:  Failure while configuring base packages.  This will be attampted 5 times.
> An error was returned while trying to install the initramfs-tools package onto the target system.

Check /var/log/syslog or see virtual console 4 for the details.

And after selecting the "check CD-Rom integrity" option from the menu it gave me this error message (keeping in mind that the md5sum had initially checked out before I made the disk)...
> The ./pool/main/v/vim/vim-runtime_7.0-164+1ubuntu7_all.deb file failed the md5 checksum verification. Your CD-ROM or this file may have been corrupted.

I've pretty much decided that this old PC just doesn't like Xubuntu, and that's just the way it is.  But if anyone has any ideas please let me know.  I hate giving up on something that seems like such a great OS!

Thanx!

~Maxx

---

### Post by louieb on 2007-10-15
Probably burned it to fast. I burn iso files at 2x or 4x. Rarely see that problem. Only takes 10-20 minutes.

---

### Post by stiiixy on 2007-10-15
> **louieb said:**
> Probably burned it to fast. I burn iso files at 2x or 4x. Rarely see that problem. Only takes 10-20 minutes.

What he said. Especially true on older machines (they can't sustain the data throughput sometimes, and mess up the burn) depending on your burner.

Sounds like you're just having a long string of bad luck. Keep it up, mate.:guitar:

---

### Post by ~Maxx on 2007-10-15
> **louieb said:**
> Probably burned it to fast. I burn iso files at 2x or 4x. Rarely see that problem. Only takes 10-20 minutes.

> **stiiixy said:**
> What he said. Especially true on older machines (they can't sustain the data throughput sometimes, and mess up the burn) depending on your burner.

Sounds like you're just having a long string of bad luck. Keep it up, mate.:guitar:
Actually I had read a good bit about procedure before I did my very first download & install (attempt).  I've been religious about selecting "1x" in InfraRecorder (even though it always seems go at about 2x no matter what).

Also...  Just an FYI (maybe I should have mentioned it before) - the machine I'm using to download and burn has much better specs than the one I want to install the system on.  A Pent 4 with 1500MHz, 1.5gigs RAM.  So if there's a mistake being made it would have to be on that pc, not the slower one.

I'll give the torrent thing a try in a bit and post my results.

On a good note - I'm really enjoying Ubuntu, despite its relative lack of speed on this machine.  :)

Thanx again!

~Maxx

---

### Post by ~Maxx on 2007-10-17
Got it!  It's been a long hard struggle, but Xubuntu is finally up and running on my second PC.  Rather than attempting a bit torrent download I came across a note on the Xubuntu homepage about installing Xubuntu on top of Ubuntu (which I had already successfully installed).  

While still just a tad sluggish on this machine it is noticeably faster than Ubuntu (and not too much slower than the PCFluxboxOS distros that I sampled).  And I must admit that while the differences are minor, I prefer the Xubuntu desktop interface over Ubuntu.

So now that I have things running it seems that there will be an update any day now, huh?  Can't wait!

Thanx again for everyones help!  I'm sure I'll have a question or two again in the near future (and who knows - maybe I'll be able to answer other peoples questions as well!), but hopefully things will go fairly smoothly from here on out.

All the best!

~Maxx

---

### Post by Mwelsh on 2008-01-09
I'm trying to install the Xubuntu GUI on top of Ubuntu Server 7.10 I believe or 7.04. I have no internet access on the computer which I am trying to install it on. I have gotten toe Xubuntu install menu, but I cannot choose to install. The only option it will let me select is to boot from first hard disk.

How can I install this GUI on top of the existing Ubuntu which is currently just a command line?

---

### Post by PmDematagoda on 2008-01-09
Forgive me for asking this, but, why are you trying to install the Xubuntu server version on a computer that is not connected to the internet at all? The server version is meant for servers which are connected to the internet:).

---

### Post by Mwelsh on 2008-01-09
It's a test server for a local isolated network

---

