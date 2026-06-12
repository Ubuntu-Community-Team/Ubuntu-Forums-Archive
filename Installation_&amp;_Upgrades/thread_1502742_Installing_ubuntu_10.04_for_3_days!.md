---
title: "Installing ubuntu 10.04 for 3 days!"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by PtPub on 2010-06-05
I have started the install of Ubuntu 10.04 Alternate ISO three days ago! 
My computer is a Dell Dinension 4600 3.2 intel HT processor, 2 GB ram 250GB maxtor hard drive ATI radeon graphic card...

First I have tried installing 9.1 version of ubuntu, however it kept stopping at the APT manager setup... 

Then I tried installing LIVE CD Ubuntu 10.04 Regular ISO, same problem. The alternate CD seems to be working well, but it is taking FOREVER to install. I have tried it twice, thinking my PC froze the first time. And then decided to just leave it on over night. That was Thursday June 3, 2010. Today is June 5, 10:30PM CST, and the installation is installing GRUB to MBR. It is at 50%, and taking forever...

I had ubuntu installed on the exact same machine before (version 9.04 later upgraded to 9.10). It took about 45 minutes!!!:guitar:

It is the only system installed on the HD. Clean format, encrypted HD option... Don't know what other info might be needed. I have burned the Alternate ISO from the Ubuntu.org page on a TDK CD-R.

Does anyone have the same problem??? Or is it my hardware? I don't think it's my PC since it had Ubuntu install on it before without any problems...

Please HELP!!!:popcorn:

---

### Post by minhajmsm on 2010-06-06
Ive had a similar problem in installing UBUNTU... I tried 8.10 then 9.04 ,and 9.10... even I tried Fedora... couldn't install..but when i got the 10.04LTS it just got installed without any problem..... and someone suggested formatting with some sort of an software making it to zeros or something .. and now my previous posts missing... get back to you when I find that thread.... sorry...

---

### Post by wilee-nilee on 2010-06-06
How does any live cd run when you try it?

---

### Post by jerenept on 2010-06-06
I thought only gentoo took that long to install...

Maybe it is your CD. try checking the disc for errors and if any are found, burn the CD at a lower speed (4x has worked fine for me)

---

### Post by wilee-nilee on 2010-06-06
A md5sum always helps.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by PtPub on 2010-06-06
The regular CD seems to lock up at configuring APT... First it takes forever to go through the black screen, it just blinks a line in the top left corner for about 45 minutes, then it goes into formatting partitions, etc... and stops at configuring APT... or at least i think it froze at that point, because i just got pissed and turned off the PC after 3 hours on the same screen...

The system has finally finished installing, however it is very laggy... i made the required updates, but I think I will revert to 9.10 some time later...

I will try to tweek it, but the "wobbly windows" are choppy, when I try to move a window it takes about 5 seconds for it to move after I clicked and dragged it (no matter weather I have compiz enabled or not!). When i click on the top menu it takes about 3-6 seconds for the drop menu to show...

I will update this thread after I play with some settings, so in a few hours...

Oh and by the way THANKS for a "middle of the night" lightning fast response...:guitar:

as to the SPEED of burning the CD, I used 2x, which is the slowest my Vaio VGN-nr110e burner can handle... LOL

---

### Post by wojox on 2010-06-06
Nevermind.

---

### Post by PtPub on 2010-06-06
Problems:

1. HD cannot be mounted: Unable to mount 251 GB LVM2 Physical Volume. Not a mountable system.

2. The only way the windows move with the mouse is when I choose NONE under Visual Effects...

3. Cannot play DVD's and the required codec cannot be fount in Repositories...

I am attaching a Hardware two reports from the Ubuntu Testing Utility and from HardInfo program. Maybe that will help someone solve the issues...

---

### Post by PtPub on 2010-06-06
It seems like out of my 251GB I have 210GB left...
5.8GB for swap
That means the installation takes 34GB???
Now it looks like during the 3 days (or more like 2.5), it downloaded w hole bunch of files, and it probably took awhile for Ubuntu to do so, even though my download speed is around 19MBPS (comcast)...

So the 695MB CD "expanded" to 34GB... That explains some of the installation time delay, (formatting 250GB - couple of hours, downloading files from Ubuntu, another couple of hours, then setup one day or so...)

---

### Post by efflandt on 2010-06-06
Something is not right if a fresh system shows 34 GB used, unless you had an existing /home with loads of files. I have installed Ubuntu on a 4 GB USB stick before, and following is a fairly fresh install on a laptop with possibly some other files downloaded:

```
efflandt@dell8200-laptop:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda3                40620      3083     35474   8% /
none                       497         1       497   1% /dev
none                       502         1       501   1% /dev/shm
none                       502         1       502   1% /var/run
none                       502         0       502   0% /var/lock
none                       502         0       502   0% /lib/init/rw
/dev/sdb1                  250       150       101  60% /media/JUMP256
```  If you wonder why Used and Available don't add up, some may be reserved for "root only" if the disk becomes full.

---

### Post by PtPub on 2010-06-06
Here's my output for the df -m 

Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/mapper/PtUbuntuDesk-root
                        229529      4043    213828   2% /
none                      1000         1      1000   1% /dev
none                      1007         1      1007   1% /dev/shm
none                      1007         1      1007   1% /var/run
none                      1007         0      1007   0% /var/lock
none                      1007         0      1007   0% /lib/init/rw
none                    229529      4043    213828   2% /var/lib/ureadahead/debugfs
/dev/sda1                  228        41       176  19% /boot
/dev/sr0                  2368      2368         0 100% /media/Crunch Super SlimDown
/dev/sdb1                 5111      1543      3569  31% /media/9E7A-FAC2
/dev/sdb2                10100        23      9564   1% /media/757673e7-a9c3-45fc-bc97-fd3bd4b28d5e


it shows as 230GB drive even though when I click on places  drive shows up as 251GB LVM2 Physical Volume...

If it formatted it to 230 then efllandt is correct, it only uses 2% of the drive space on a fresh install... And NO i had a completely CLEAN formatted drive install. No old Home folders or anything. I wiped it clean with Drive Nuker, or whatever it's called DDD Nuke... So nothing was left on the drive... all ZEROES...

Now you said something about ROOT reserved space, how can I check how much if any space there is reserved for ROOT? or you could tell me based on the above printout... 

At this moment I am installing Cairo DOck, and other Ubuntu tweeks, with the Ubuntu 10.04 Start Script v. 0.4.9.7. The easiest way I found to customize the whole Ubuntu box all at once. It has restricted extras, codecs, software, and is available here:

[http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html](http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html)

---

### Post by Onesimus on 2010-06-06
I wonder if your poor performance may be due to a failing hard disk.  You could try System->Administration->Disk Utility.

It may reveal something that would shed light on your predicament.

---

### Post by PtPub on 2010-06-06
As to the Disk Utility Here are the Results:

Drive is ATA Maxtor 6L250R0
Firmware: BAJ41G02
Minimum Read Rate: 22.5 MB/s
Maximum Read Rate: 60.8 MB/s
Average Read Rate: 48.5 MB/s
Average Access Time: 16.3 MS

After a one minute test :
It tells me Disk is Healthy
It runs at 88*F
All Assessments are at : GOOD or N/A

---

### Post by bildr on 2010-06-06
explanation of the following:

Filesystem           1M-blocks      Used Available Use% Mounted on

/dev/mapper/PtUbuntuDesk-root 229529      4043    213828   2% /

this is the 230GB you are referring to, that is correct and the os is not taking up 30 GB
that is how the drive is configured

none                      1000         1      1000   1% /dev
none                      1007         1      1007   1% /dev/shm
none                      1007         1      1007   1% /var/run
none                      1007         0      1007   0% /var/lock
none                      1007         0      1007   0% /lib/init/rw
none                    229529      4043    213828   2%  /var/lib/ureadahead/debugfs

logical filesystems, not taking up space, don't worry about these

/dev/sr0                  2368      2368         0 100% /media/Crunch  Super SlimDown
 
your cdrom/dvd

/dev/sda1                  228        41       176  19% /boot

your boot partition

/dev/sdb1                 5111      1543      3569  31% /media/9E7A-FAC2
/dev/sdb2                10100        23      9564   1%  /media/757673e7-a9c3-45fc-bc97-fd3bd4b28d5e

other partitions

I am guessing here that the logical volume is on sdb??
doing the math
5000 1M blocks + 10100 1M blocks + 229000 1M blocks (rounding for simplicity)
=244000 1M blocks

now the somewhat deceptive naming convention that HD manufacturers use:
1GB is actually 1024 M, 1MB is actually 1024 K, 1KB is actually 1024 B

as a marketing ploy the manufacturer say:
250000000000 B = 250 GB, not really in practice

example:
(250GB/1024 to get us to MB)*1000

to account for the manufacturer not converting properly

=244 1M blocks

translation: everything is working properly
the difference is the two partitions here

/dev/sdb1                 5111      1543      3569  31% /media/9E7A-FAC2
/dev/sdb2                10100        23      9564   1%  /media/757673e7-a9c3-45fc-bc97-fd3bd4b28d5e

and conversion based on 1000 not 1024.

there is no problem here, calm down

---

### Post by bildr on 2010-06-06
ok hard drive problem was solved.
on to codecs.
sudo apt-get -y install ubuntu-restricted-extras
then go to synaptic and find this package, right click on it and install all the suggests/recommends etc.

additionally you can search for gstreamer-* to get good bad and ugly from restricted repos

that should solve your multimedia stuff, if it doesn't install vlc or mplayer.

---

### Post by bildr on 2010-06-06
the mouse problem, check your video driver.  i am not walking troubleshooting a hosed video driver install so do the following at your own risk.  install proprietary drivers or open drivers, whichever you aren't currently using.  it is probably a driver issue.

---

