---
title: "Portable Linux - Installation to a USB HDD for use on different computers"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by n4pgw on 2013-02-24
I am interested in setting up a Ubuntu, (probably Lubuntu,) on a USB HDD (not flash drive) that I can carry with me to plug into any available computer and use. 

I am hoping that this portable system can contain all the same software as installed on my primary desktop including all my most often accessed data.

Edits follow: 

I have decided that I do not prefer Unity and would like to downgrade to something like Lubuntu, or maybe even Mint.  However, I just spent the last two weeks getting 12.04 up and running with all my software, so rather than start with nothing again, I'll shift to this other project of having a portable version. When I get it stabilized, I'll have something to use while I rebuild this main system.

Once I have the portable working, I can use it until I get my primary desktop rebuilt with the newer Linux.

I am also assuming that I will have to install all the software twice, once on the portable, and once on my primary.

Data can be copied, but can it be synchronized so I only transfer the latest changes?  

And not have to copy all the data just to know it is all updated?

---

### Post by n4pgw on 2013-02-24
Additional details: 

The USB drive is a WD My Passport 360GB HDD.  It uses only one USB cord to provide both power and data, so I suppose that it is slow. 

This is my primary computer: 
Compaq Presario with 64-Bit dual core processor, 3GB RAM (4 max), dual monitors, 500 GB internal drive, DVD Writer, 1.5TB External USB HDD (not portable).

The other computers will vary randomly, but here are a few I have available, assuming they will boot from USB: 

(These are all single core)
64 bit laptop with 3GB RAM
32 bit laptop with 1GB RAM
32 bit desktop with 2GB RAM
64 bit desktop with 4GB RAM

---

### Post by sudodus on 2013-02-24
I have done it and it works well. It is like installing to an internal drive. There is one thing you need to think about: Don't install any proprietary drivers (typically for graphics and wifi)!

It it not necessary, but helps to avoid mistakes, if you disconnect your internal drive, when you do the installation.

If you plan to use an HDD, but have not bought it yet, consider buying an SSD and a separate box instead. Get a box with USB 3 and eSATA! Then your system will run with full speed, when either of those connections is available :-)

---

### Post by n4pgw on 2013-02-24
Thank you Sudosus,

It is great to know about USB-3, but I'll be starting with what I have as described above. However, if this works, I will consider it a worth-while investment to buy a faster drive.

How do I know whether I would need proprietary drivers?  I originally installed some for this computer in 10.04, and then in my first install of 12.04, but after my crash in 12.04, I just skipped upgrading the driver.  

Keep in mind, that I will NOT be installing 12.04 with Unity on my Portable Linux drive.

---

### Post by sudodus on 2013-02-24
> **n4pgw said:**
> 
How do I know whether I would need proprietary drivers?  I originally installed some for this computer in 10.04, and then in my first install of 12.04, but after my crash in 12.04, I just skipped upgrading the driver.  

By trial and error. If it works with the built-in drivers, fine :-) I have also noticed, that 12.04 LTS has better recognition of hardware than 10.04 LTS.
> 
Keep in mind, that I will NOT be installing 12.04 with Unity on my Portable Linux drive.
Yes, I suggest Lubuntu or Lubuntu plus Xubuntu-desktop
```
sudo apt-get install xubuntu-desktop
``` This gives you some extra tools, for example to tweak your audio settings, as well as the Xubuntu desktop environment. You select desktop environment at the log in screen.

Use a 32 bit system, that will run on all the computers. Maybe you should check if the 32-bit laptop has a CPU with pae or not. Anyway, 12.04 is the last version of Lubuntu and Xubuntu, that supports non-pae CPUs (typically Pentium M).

---

### Post by n4pgw on 2013-02-24
Thanks again Sudodus, 

The 32 bit laptop is pretty old and probably is non-pae.  It isn't important, though, just an option since I have it.  I could just as easily sell it and use the money to buy a better hdd. ;) 

Lubuntu isn't LTS, so I would have to upgrade more often.  I guess if it doesn't try to stay too cutting edge or keep adding new bloat, it would not make much difference. I just don't want to spend my life debugging crap.  I just want my computer to do what I need it to do.  

Really, until the release of version 11 with Unity, I don't recall any problems keeping up with the short term releases of Ubuntu.  I think that either 10.10 or 11.x was the reason I switched to LTS in the first place.

BTW, how do I know if a processor is non-pae?

---

### Post by sudodus on 2013-02-24
> **n4pgw said:**
> Thanks again Sudodus, 

The 32 bit laptop is pretty old and probably is non-pae.  It isn't important, though, just an option since I have it.  I could just as easily sell it and use the money to buy a better hdd. ;) 

Why not :-)
> 
Lubuntu isn't LTS, so I would have to upgrade more often.  I guess if it doesn't try to stay too cutting edge or keep adding new bloat, it would not make much difference. I just don't want to spend my life debugging crap.  I just want my computer to do what I need it to do.  

OK, go for Xubuntu, supported until April 2015
> 
Really, until the release of version 11 with Unity, I don't recall aReply With Quoteny problems keeping up with the short term releases of Ubuntu.  I think that either 10.10 or 11.x was the reason I switched to LTS in the first place.

BTW, how do I know if a processor is non-pae?
```
hwinfo|grep --color ",pae,"
```

---

### Post by n4pgw on 2013-02-24
Thanks again, Sudosus, 

But, I screwed something up and crashed the system.  I installed the kubuntu desktop and think it installed ubuntu studio.  Now I get an empty desktop and nothing I can do.

[http://ubuntuforums.org/showthread.php?t=2119578](http://ubuntuforums.org/showthread.php?t=2119578)

It looks like it will have to wait until after church.

Oh well, I guess I'll have to try again.

I have a boot partition, a / partition, a swap partition and a /home partition.  Do you know of any problems using Xubuntu replacing the first three partitions but only accessing the /home partitioin?

---

### Post by sudodus on 2013-02-24
> **n4pgw said:**
> Thanks again, Sudosus, 

But, I screwed something up and crashed the system.  I installed the kubuntu desktop and think it installed ubuntu studio.  Now I get an empty desktop and nothing I can do.

[http://ubuntuforums.org/showthread.php?t=2119578](http://ubuntuforums.org/showthread.php?t=2119578)

It looks like it will have to wait until after church.

Oh well, I guess I'll have to try again.

I have a boot partition, a / partition, a swap partition and a /home partition.  Do you know of any problems using Xubuntu replacing the first three partitions but only accessing the /home partitioin?

The /home partition contains not only your personal files, but also a lot of hidden directories and and files with settings and data for installed programs (including desktop settings, browser bookmarks and mailboxes (if you use for example Thunderbird). It might be confusing to keep those data if you install another flavour of Ubuntu, but many people keep /home and make a fresh install of the rest instead of upgrading to a new version of Ubuntu.

So back up your /home and try :-)

---

### Post by n4pgw on 2013-02-24
Thanks,

I am reinstalling now.  I hope the desktop in home isn't damaged.  It probably isn't since I haven't gotten to a login screen.

I edited my partitions to the following: 

22GB / bootable ext4 primary
3GB swap extended
remainder of drive is /home ext4 not formatted or resized

Last time I did this, all my data was there even after reinstalling software.

hope for the same this time

---

### Post by n4pgw on 2013-02-25
I tried testing Ubuntu 12.04 on my portable drive.  Of course, not thinking, I didn't set up Gnome, so when I plugged it into my other desktop, it came up with a dead brown screen.  So, I deleted it and started installing 10.04, but something went wrong, so I am going to start over.  

I think I'll try it with Linux Mint Cinnamon   I have been playing with it a little on my VM.  It seems to be intuitive enough to work with.

---

### Post by sudodus on 2013-02-25
Well, with a USB 2 connection it will be slow, but if there is RAM enough, you should be able to run any system, that runs on the computer booted from RAM.

You need portability and reasonable speed on less powerful computers, so I suggest that you avoid Unity and KDE. Lubuntu would be the fastest among the Ubuntu flavours. Second fastest would be Xubuntu. Linux Mint is nice, but I think the default flavour is slower than Lubuntu and Xubuntu. There are light desktop versions of Linux Mint too.

Finally there is the question, if it runs at all on some computers, that 'need' proprietary graphics drivers. But I have good experience with the built-in drivers of [LX]ubuntu 12.04.

It is worth testing with the boot option **nomodeset** at 'quiet splash' in the file

[FONT="Courier New"]**/etc/default/grub**[/FONT]

```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

``` 
and run ```
sudo update-grub
``` to make it active at the next boot.

---

### Post by monkeybrain2012 on 2013-02-26
> **sudodus said:**
> I have done it and it works well. It is like installing to an internal drive. There is one thing you need to think about: Don't install any proprietary drivers (typically for graphics and wifi)!

It it not necessary, but helps to avoid mistakes, if you disconnect your internal drive, when you do the installation.

If you plan to use an HDD, but have not bought it yet, consider buying an SSD and a separate box instead. Get a box with USB 3 and eSATA! Then your system will run with full speed, when either of those connections is available :-)

Actually wifi drivers are fine. Proprietary graphic card is a problem if you use your portable on a machine with a different graphic card or different graphic driver.

The important thing is to install the boot loader in the external drive.

P.S. I don't think usb2 will be slow, installing on an external hard drive is like installing in a second hard drive. I never notice a slow down.I have installed 10.10, 11.04, 12.04 and 12.10 on external hard drives and they all worked well (apart from using it as a portable, this is how I test a new release before I install it internally)

---

### Post by n4pgw on 2013-03-04
Thanks.

And Thank you to all who responded.

---

