---
title: "Cant make start-up disk with some OS's"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2011-02-27
Hi all,

I have made several start-up disk, just made 2 today, but certain ISO's won't even go into the "start up disk creator" window. 

I've made them with Ubuntu, Kubuntu, Linux Mint, Xubuntu, Lubuntu, Ultimate-Edition, Peppermint One & Peppermint Ice, but I can't make one with Puppy, PCLinuxOS, and a couple others. 

I'm trying to make one with "system rescue cd" so I can use it to totally wipe my 500GiB hdd, before I start to partition & install OS's on it. I downloaded system rescue & saved it to my desktop, but start up disk creator won't let me make a start up usb with it.

My questions are...

1. Why does it refuse to make some & not others?

2. I know it's not totally necessary but, is there really any reason to completely wipe it before writing over it? Such as longevity or speed?

according to post #2 on this link, there is...[*[COLOR="Red"]Click Here[/COLOR]*]("http://www.bleepingcomputer.com/forums/topic378509.html/page__p__2127416__fromsearch__1#entry2127416")

I want the best start I can get with this hdd cause I plan to install several distro's on it.

---

### Post by moore.bryan on 2011-02-27
I don't know if this is exactly what you're asking about, but some distros need to be installed to the USB via dd.

---

### Post by Dutch70 on 2011-02-27
> **moore.bryan said:**
> I don't know if this is exactly what you're asking about, but some distros need to be installed to the USB via dd.

Thanks for a quick reply Bryan
 via dd??? Not sure what that is, I really would like to get that problem figured out, and I would think distro's like PCLinuxOS would be able to to be created from start up disk creator.


but I guess my main quesion is...
 How important is it that I wipe that hdd of all traces of windows before I start to format it for several linux distro's?

---

### Post by moore.bryan on 2011-02-27
> **Dutch70 said:**
> Thanks for a quick reply Bryan
 via dd??? Not sure what that is, I really would like to get that problem figured out, and I would think distro's like PCLinuxOS would be able to to be created from start up disk creator.
No worries. I know some distros work nicely with Ubuntu's Disk Creator, but others require a minorly different structure for the bootable USB. A *really* good supplement is UNetBootin (in the repos, AFAIK).  "dd" refers to the command-line command. For example
```
sudo dd if=/home/username/Desktop/Linux.iso of=/dev/sdb
```
burns the Linux.iso you have saved to your Desktop onto the USB drive at /dev/sdb.

> but I guess my main quesion is...
 How important is it that I wipe that hdd of all traces of windows before I start to format it for several linux distro's?
This is a loaded question. What do you mean by "important?" Putting Linux onto a hard drive will clear it out, leaving no Windows behind. Are you concerned "leftover" Windows files could interfere with your Linux install?

---

### Post by ajgreeny on 2011-02-27
The USB startup disk creator only works with the Ubuntu family .iso files, not with any others.  The two Pepermint distros and Mint are both ubuntu based, so work OK, but others do not.  For those try unetbootin, as suggested by moore.brian, and available in the repositories.

---

### Post by C.S.Cameron on 2011-02-27
Another alternative to usb-creator and UNetbootin is MultiBootUSB.
You can boot multiple iso's on a single flash drive:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by Dutch70 on 2011-02-28
Thanks a lot for all the good info everyone. I'm trying Unetbootin right now & it seems to be working so far. I thought it was only for windows users that didn't have start up disk creator.

I also checked out the MultilbootUSB, but didn't go that way b/c I've only installed a few tarballs & not yet comfortable. Think I'm gonna go back & check it out more though. 

I'll mark this thread solved when I make sure this works.

Thanks again

---

### Post by Dutch70 on 2011-02-28
Thanks everyone!!! :D

 I used Unetbootin to install both Fedora & PCLinuxOS. I thought  Unetbootin was mainly for people with windows. 

Thanks again for your help!!!

---

### Post by deshotel on 2011-05-08
> **C.S.Cameron said:**
> Another alternative to usb-creator and UNetbootin is MultiBootUSB.
You can boot multiple iso's on a single flash drive:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

When I use any of these (mentioned) usb creator programs, my brandnew ASUS N43S intel core 5-2410M 2.3Ghz, running Ubuntu 11.04 (w/Kubuntu desktop)tells me that I cannot open .exe files (whereas my older Toshiba also with Ubuntu 10.10 said the same thing but then opened the various usb creators anyway--yet did not actually create anything!). Would really like to try many more USB versions (like puppy 5.2)besides the one that the very nice Ubuntu startup disk creator uses...any suggestion on how to fix my problem?? Thanx4UrHelp:D!

---

