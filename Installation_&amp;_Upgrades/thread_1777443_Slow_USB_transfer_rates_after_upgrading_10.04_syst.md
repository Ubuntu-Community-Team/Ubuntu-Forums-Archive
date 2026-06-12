---
title: "Slow USB transfer rates after upgrading 10.04 system"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by duuso on 2011-06-07
Inspired by [Slow USB transfer rate after upgrading to Karmic thread]("http://ubuntuforums.org/showthread.php?t=1306333"):
> **simonedge said:**
> Time for a bump, I think. (it's... disconcerting that such an issue should be unresolved for so long)

Ubuntu Netbook Edition 10.10, kernel 2.6.35-27-gener

initial speeds of about 13mb/s for about fifty percent of the file  (650mb video), dropping to about 3mb/s thereafter. Not to mention that  wait when the transfer is reported as complete.

The above was with a bog-standard FAT pendrive.
Formatting the drive to EXT4 and transferring the same file again  yielded an initial speed boost (closer to 20mb/s) until, again, about  50% of the file had been transferred. Te speed then tailed off slowly to  about 7mb/s, but I wasn't left waiting when the transfer had  finished.
I downloaded updates to Ubuntu 10.04  just  few days ago, those may have something to do with this. On my setup  read speed from various usb 2.0 devices is around 850 kb/s (while hdd to hdd/hdd to hdd over lan speeds are constant 85 mb/s). 

Kernel 2.6.32.32.28 generic, x64.

---

### Post by syoung27 on 2011-06-07
Very happy i just saw somebody else with this problem.  So far in ALL my Linux distro experiences on my new laptop have all consisted with poor VERY poor USB speeds:(  12minutes for 1gb. 
Zorin, Fedora15, Ubuntu 11.04 i believe is what i have now also. 
Hopefully there is a fix for this, i was slightly confused googling answers. every site i saw had very different solutions so i wasn't eager to jump on any of them. hopefully some trusty ubuntu mind has a good one!

---

### Post by duuso on 2011-06-08
This should be fixed with updates, not by googling etc. Once again major problems with everyday usage which leads very many users to different OS's or at least makes long lasting bad impression.

I'm having same USB memory on iMac and average read speed is 20 mb/s.

---

### Post by mörgæs on 2011-06-08
Do you get these slow rates when transferring one huge file or also for a number of small files?

---

### Post by syoung27 on 2011-06-08
comes with both. i have two large externals and 3 thumbdrives always in use, various file sizes. all slow. they start at like 19mbs and slowly decreases, then circles that pattern every like 30 seconds

---

### Post by 23dornot23d on 2011-06-08
I found problems if I had USB thumb drives in ..... without them - what is it like .....

I just have a 300 Gig western digital  a 500Gig seagate and 1Terra seagate

But the worst USB drive is the Iomega 1 Terra for speed its ever so slow ...... to find things
and to boot up ...... ( I use this one the least now )

---

### Post by mörgæs on 2011-06-08
> **syoung27 said:**
> comes with both. i have two large externals and 3 thumbdrives always in use, various file sizes. all slow. they start at like 19mbs and slowly decreases, then circles that pattern every like 30 seconds

It sounds like the classical USB problem. 

There are a number of bug reports, for example this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/392089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/392089)

There are some workarounds in this report (and in 197762)

---

### Post by duuso on 2011-06-12
On my system it doesn't slow down, it just starts with very slow speed (max 950 kbps), no matter if it's one big or smaller ones. 

Tested periapphels (which also have worked before):
Kingston 8 gb usb stick, 16 gb sdxc memory card (on Dell display), Zoom H2 recorder equipped with usb 2.0, fuj:tech's external usb 2.0 sata dock & Canon dslr. All suffers the same symptom. All of those are also in daily use, so this should work.

edit: My problem was solved by reconfiguring bios. There was a hidden "Enable USB 2.0 support" selection which was shown only when I had an USB device (in this case Dell display with cardreader, but Huawei E169 3g modem didn't work same) plugged in.

---

### Post by riiidaa on 2011-07-26
Affects me too, on a clean install of 10.04

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624510](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624510)

> 
on my 10.04 LTS server, with a seagate 1TB usb2 drive I just purchased. (The disk was formatted with EXT4 whilst at home connected to an Ubuntu virtual machine on a Windows host that I then happily copied a bunch of large files to from a Samba share with write speeds approximately 14MB / sec)

Connected the same disk to my server yesterday and immediately hit this bug when trying to move files from the SCSI disk to the Seagate USB. The server is a DL360 G3.

My colleague pointed me at this bug report. I ran the following commands last night after remotely rebooting:

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.04.3 LTS
Release: 10.04
Codename: lucid

sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads: 4 MB in 3.93 seconds = 1.02 MB/sec

A woeful 1MB per sec...

This morning I did it again:

 sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads: 2 MB in 7.44 seconds = 275.24 kB/sec

which is pretty much useless.


---

