---
title: "Ubuntu 6.10 LiveCD hangs during installation"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by th0r0n on 2007-01-10
Hi,

I am installing Ubuntu 6.10 onto my Toshiba 2410-504 using the LiveCD.

It boots up into the Desktop fine (From the CD), the Disk Check works and comes up as fine.

I select my language and keyboard layout, and put my name and password into the installer, and then it asks me how I want to partition... I selected 'use free space' and afterwards tried 'manual' but they both crash.

On use free space it crashes just after reviewing the summary and pressing ok... There's no HD activity light, no mouse, nothing, and the CD stops spinning.

On the manual partition, the whole thing bombs out in the same way whilst the application is loading.

Anyone got any ideas? Here's my spec:

Toshiba 2410
250MB DDR RAM
20 GB HDD
1.7Ghz P4
32MB Geforce 420 Go! 
Teach DW224E CDRW/DVD

Thanks!

Toby

---

### Post by scrooge_74 on 2007-01-10
ARe you trying to dual boot? For some reason I had that problem with my toshiba so I just wiped clean the disk and went solo with linux

Maybe here you can find some info.  [http://www.psychocats.net/](http://www.psychocats.net/)

---

### Post by MikeBuffer on 2007-01-10
I think it is safest to partition first before doing the install, if you need to maintain other partitions such as a Windows one. After booting the LiveCD, select System - Administration - Gnome Partition Editor. That way, you'll be able to see whether there are errors during the partitioning. Also, you will be able to reboot into Windows to verify that you have left it undisturbed before proceeding with the install.

Before partitioning would work successfully for me, I had to boot into Windows and run the disk defragmenter followed by chkdsk -f.

Mike.

---

### Post by finer recliner on 2007-01-10
check the disk for errors. its on the live cd boot menu

---

### Post by th0r0n on 2007-01-10
> **finer recliner said:**
> check the disk for errors. its on the live cd boot menu

If you mean the CD... I have and it's come up fine.

I've manually created a block of free space, I will see how it copes with that, wish me luck.

T

---

### Post by th0r0n on 2007-01-10
Resolved!

I needed to run the windows disk checker

(Right click your hard drive in 'My Computer' and click Check Volume for Errors and then reboot)

Then I installed off of the LiveCD as normal but I also used PartitionMagic in windows to create 5GB of free space.

Thanks for the help guys.

(BTW: My netgear wpn511 PCMCIA card worked straight out of the box after entering my SSID)

T

---

### Post by GrimJa on 2007-01-12
Guys, is it just me.. or does the whole "live/install" concept just suck!?
I mean, this new live version has been nothing but trouble for me.. and the previous CMI based versions never game me any of this;

Aside from the fact that the thing is SLUGGY and takes forever to load (nothing at all like knoppix)  - (and I think its due to the fact that its both running an os from CD.. AND installing one... not good!)     

There's the fact that this thing, despite seeing and acknowledging the swap partition, wont appoint it for swap.. and gives no option to, hence when I'm about to install, it whines about not having a swap partition, even though its there. 

And Its hangs a 81% all the time. So it still dont have ubunto on my machine! :[

I'm off to do a disk check now, but I doubt thats the prob - CD isnt scratched.

So upset with this install Cd setup. I much prefer the CMI based ones before it.

---

### Post by Seti on 2007-01-12
Totally know what you're talking about. I was getting the same thing with Edgy livecd, where one I had designated mount points for all my partitions, it would tell me that there was no root partition even though it was there! I've quickly changed to the Alternative Installer, even tho I've been having some trouble even with that lately trying to reinstall ubuntu. Could it be a pooched drive? I dunno yet.

---

### Post by scrooge_74 on 2007-01-13
> **GrimJa said:**
> Guys, is it just me.. or does the whole "live/install" concept just suck!?
I mean, this new live version has been nothing but trouble for me.. and the previous CMI based versions never game me any of this;

Aside from the fact that the thing is SLUGGY and takes forever to load (nothing at all like knoppix)  - (and I think its due to the fact that its both running an os from CD.. AND installing one... not good!)     

There's the fact that this thing, despite seeing and acknowledging the swap partition, wont appoint it for swap.. and gives no option to, hence when I'm about to install, it whines about not having a swap partition, even though its there. 

And Its hangs a 81% all the time. So it still dont have ubunto on my machine! :[

I'm off to do a disk check now, but I doubt thats the prob - CD isnt scratched.

So upset with this install Cd setup. I much prefer the CMI based ones before it.

The other day I was trying to help a friend and we were trying to install from the live CD, it was taking for ever to do the simple of task. Latter I try booting that same PC but using the safe mode boot, what ever did not load was the answer I manage to install the systems in a few minutes instead of the few hours doing nothing I had already spent.

---

### Post by GrimJa on 2007-01-15
> **scrooge_74 said:**
> The other day I was trying to help a friend and we were trying to install from the live CD, it was taking for ever to do the simple of task. Latter I try booting that same PC but using the safe mode boot, what ever did not load was the answer I manage to install the systems in a few minutes instead of the few hours doing nothing I had already spent.

AHA!

SO I shall try that then! :D 

You are reffering to the live CD's Safe-mode option right?
(I do think I recall seeing one... was it my imagination!? ](*,) )

---

### Post by Pobega on 2007-01-15
> **GrimJa said:**
> Guys, is it just me.. or does the whole "live/install" concept just suck!?
I mean, this new live version has been nothing but trouble for me.. and the previous CMI based versions never game me any of this;

Aside from the fact that the thing is SLUGGY and takes forever to load (nothing at all like knoppix)  - (and I think its due to the fact that its both running an os from CD.. AND installing one... not good!)     

There's the fact that this thing, despite seeing and acknowledging the swap partition, wont appoint it for swap.. and gives no option to, hence when I'm about to install, it whines about not having a swap partition, even though its there. 

And Its hangs a 81% all the time. So it still dont have ubunto on my machine! :[

I'm off to do a disk check now, but I doubt thats the prob - CD isnt scratched.

So upset with this install Cd setup. I much prefer the CMI based ones before it.

It hangs at 81% probably because of a bad burn. 

The reason the LiveCD is in a fully functional desktop environment is because you can surf/chat while installing, and I do think it's a good idea in concept; You rarely notice it on Ubuntu, but on installs like Gentoo (Which takes 3-4 days to get running, mind you) being able to chat/surf while installing is a godsend. **Especially** if you're doing it on your main/only computer.

---

### Post by GrimJa on 2007-01-15
> **Pobega said:**
> It hangs at 81% probably because of a bad burn. 

The reason the LiveCD is in a fully functional desktop environment is because you can surf/chat while installing, and I do think it's a good idea in concept; You rarely notice it on Ubuntu, but on installs like Gentoo (Which takes 3-4 days to get running, mind you) being able to chat/surf while installing is a godsend. **Especially** if you're doing it on your main/only computer.

HA! 

Dude, think about it, you're running an OS from a CD... OS's take long to load from HDD's muchless CDs!  AND ... you're going to ;
Run an Os
Install an OS
Run applications like messenger!! 

Thats going to rape out your CD drive man.. naturally it'll take forever due to the low access times and data rates of a CDROm drive.

knoppix is one of the best live CD's I've seen, and even it is relatively slow AND its not installing :|

Anywho.. off to try the safemode now.

As you said, Good Idea.. IN CONCEPT dude ](*,)

---

