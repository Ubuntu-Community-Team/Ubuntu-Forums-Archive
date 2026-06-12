---
title: "Error: Out of Disk"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by chzuck on 2010-05-04
I am new to Ubuntu. I have heard much about it from my brother, so I thought I would give it a try. I loaded the newest version 10.04. When I rebooted here is what came up on the screen.
Grub loading
error: out of disk
Grub Rescue>
So, I thought I would format the hard drive and install an older version. I installed 9.10 and got the same results. I then tried to work through many of the fixes I found on this forum without any change. When it comes to this kind of stuff, I am not to computer literate. I am trying to install this on an old Gateway computer 350mhz. Any help would be greatly appreciated. Please make it easy to understand and assume I know almost nothing.:(

---

### Post by lechien73 on 2010-05-04
Could you give some more details about the size of your hard disk? Old computer systems have problems booting if the partition starts beyond cylinder 1024.

Maybe you could try updating your BIOS, which might help. Take a look at [http://support.gateway.com/support/drivers/dlcenter.asp?cmpid=topnav](http://support.gateway.com/support/drivers/dlcenter.asp?cmpid=topnav) and see if you can download an update.

---

### Post by kansasnoob on 2010-05-04
That sounds somewhat like this error:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

But I thought that was fixed in 10.04?

Anyway it sounds like your CPU is 350mhz, how much RAM do you have?

Were you able to run the Live CD, that is just running the Live Desktop without installing?

If so it might be helpful to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And also the output from terminal of:

```
lshw
```

---

### Post by chzuck on 2010-05-04
My hard drive is 10gb and I have 320mb RAM installed.  I am able to run Ubuntu from the live CD.  I will check for BIOS update and other requested info.  It may be a few days since I start my 4 day 12 hr work schedule tonight.

---

### Post by Carl Hamlin on 2010-05-04
> **chzuck said:**
> My hard drive is 10gb and I have 320mb RAM installed.  I am able to run Ubuntu from the live CD.  I will check for BIOS update and other requested info.  It may be a few days since I start my 4 day 12 hr work schedule tonight.

320MB is an unlikely number - perhaps you meant 32MB?

Regardless, I'd recommend bumping up to 2GB to increase performance. You're not going to like what you get with much less.

---

### Post by kansasnoob on 2010-05-04
> **Carl Hamlin said:**
> 320MB is an unlikely number - perhaps you meant 32MB?

Regardless, I'd recommend bumping up to 2GB to increase performance. You're not going to like what you get with much less.

How so?

256+64=320 :)

I think Ubuntu will barely run on it, Xubuntu or Lubuntu would probably be better.

---

### Post by chzuck on 2010-05-04
Maybe before doing all the checking that was suggested, I may try one of the OS you mentioned.  Would you recommend one over the other?
 
On the RAM, you are exactly right.  I have 2 128 sticks and 1 original 64.  All I can do is replace the 64 with another 128 and that's all this ole computer will handle.

---

### Post by sunk8 on 2010-05-04
> **chzuck said:**
> Maybe before doing all the checking that was suggested, I may try one of the OS you mentioned.  Would you recommend one over the other?

I've used 'em both.
Lubuntu is still under development. Not a full-fledged release yet. But it's lighter and faster.

Xubuntu has been here for years. Your computer will be able to give you good performance on this one too. It requires just 192Mb of RAM abd runs smoothly on 256. 2GB space is enough for an average user. Plus you will get better support. The no. of people who use Xubuntu is higher.

What I'll personally recommend:
Install Xubuntu. Install the 'lxde' package on it.
You will be able to choose between the desktops at login.
Thus, you can make the best of both desktops.
If you find lxde more comfortable, you can easily switch to Lubuntu!

---

### Post by Scari on 2010-05-04
> **Carl Hamlin said:**
> 320MB is an unlikely number - perhaps you meant 32MB?

Regardless, I'd recommend bumping up to 2GB to increase performance. You're not going to like what you get with much less.
Seeing he said his gateway was an old computer it probably won't support even 1 gig of memory let alone 2 gig...

---

### Post by chzuck on 2010-05-04
So, it seems my RAM is too small to run Ubuntu?  I will try Xubuntu and see what happens.  One thing that seems strange to me is that Ubuntu live CD will run, just very slow.  I guess I am trying to understand why it will not run from the hard drive, but will run from the CD:?:

---

### Post by sunk8 on 2010-05-04
> **chzuck said:**
> So, it seems my RAM is too small to run Ubuntu? I will try Xubuntu and see what happens.  One thing that seems strange  to me is that Ubuntu live CD will run, just very slow.  I guess I am  trying to understand why it will not run from the hard drive, but will  run from the CD:?:

You can install Ubuntu even if u have low RAM. But believe me, you won't like the experience. I got Ubuntu 9.10 running on my old comp (350MHz, 64MB RAM, 4MB video card, 6GB hard-disk). It didn't exactly run, was more like crawling. But no crashes at all as I had 512 MB of swap. Took me about 5 minutes to just pull firefox up!


Xfce desktop is similar to the GNOME desktop in many ways. Most Ubuntu programs should run fine on Xubuntu too...

I hope u enjoy using Xubuntu. On my new computer, although I have Ubuntu  10.04, I also have the Xfce desktop, just for better performance...

---

### Post by chzuck on 2010-05-04
Of course all this Linux stuff is brand new to me.  My brother has used it for some time.  What about a virus program?  I currently use Avast free version.  I assume you don't use Microsoft stuff at all?

---

### Post by sunk8 on 2010-05-04
> **chzuck said:**
> Of course all this Linux stuff is brand new to me.  My brother has used it for some time.  What about a virus program?  I currently use Avast free version.  I assume you don't use Microsoft stuff at all?

You can use emulators like WINE to run Windoze apps on Linux.
Winetricks and Playonlinux make the job even easier.

Linux does't actually need an antivirus. But you can use ClamAV from the repositories.
Chk out:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
and
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

I have been using Linux for a few years now, and not 1 virus!
Except for ones that might creep into WINE. But they couldn't harm the actual system. ;-)

---

### Post by kansasnoob on 2010-05-04
IMO listen to sunk8! Xubuntu is less resource hungry by far than Ubuntu.

Lubuntu is even less resource hungry but read the release announcement at Distrowatch:

[http://distrowatch.com/?newsid=06045](http://distrowatch.com/?newsid=06045)

Note that it says:

> This release is considered as a 'stable beta'

---

### Post by kansasnoob on 2010-05-04
> **Scari said:**
> Seeing he said his gateway was an old computer it probably won't support even 1 gig of memory let alone 2 gig...

Yeah, sort of like throwing a turbo on a '60 Chevy six-banger :lolflag:

Also "old" RAM is cost prohibitive!

---

### Post by ewanchic on 2010-05-05
I don't believe this is the real answer. I am receiving this error too when installing ubuntu 10.04. I too am running an older computer, probably with 128MB of RAM, but I'm installing Server, not Desktop.

---

### Post by ewanchic on 2010-05-06
More google searching helped me to discover the problem. the size of my Hard drive cylinders is the issue. (I think it's about 1024 or something like that).

Anyway, the solution is, you need to make the first primary partition small, and mount it as your boot directory (/boot). So you'll probably have to format and reinstall your OS again.

The site I read suggested 200MB - 1GB, I made mine 50MB which is still very big. Create your other 2 partitions, root (/) and swap, or however you want them, and continue on.

This will solve the grub rescue> problem.

As far as the Error: Out of Disk, you'll still be getting this. I believe this has something to do with your floppy drive. If you don't need it, disconnect it and you should be good.

My floppy is still connected, and connected incorrectly, although it is disabled under the bios. I still get this error, but I'll get back to see if removing the floppy drive fixes the issue.

---

### Post by sunk8 on 2010-05-06
Well, do let us know what happens...

---

### Post by chzuck on 2010-05-07
I must say I am disappointed at all the problems I am having getting Ubuntu going.  If I need to disable my floppy drive, it's back to Windows XP in a flash!  I will not disable a drive in my computer to get something to work.   After all aren't Linux systems supposed to be the greatest?
 
I have one or two things to check out in Ubuntu and if I don't have any success, I will try Xubuntu.

---

### Post by yardapeJV on 2010-05-08
I had this same problem last night, and I tried to reinstall several times with no luck, each time getting an "Out of Disk" afterwards.  (This is with an 80gig drive, which has plenty of room)   Each time I went through, I let Ubuntu set up the partitions on the whole drive.  This seems to be the problem!  Based on info from another post, it seems like specifying partitions yourself solves the problem.  

Set up a swap (2 gigs), set up "/" as the primary (ext4, ~10 gigs), and set up a "/home" (ext4) with the rest of your drive if you want.  

Here are more detailed instructions if you would like:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml")
Check out the section about doing a manual partition.
 

This completely fixed my problem and I am up and running! Let me know if it works for you..

---

### Post by RJARRRPCGP on 2010-05-08
You probably don't have enough HDD space for GRUB!

Are you using software RAID? If you are, please make a /boot partition, which must be at least around 100 MB, on the first HDD.

---

### Post by chzuck on 2010-05-08
OK, I tried yardapeJV's fix. Same end result for me. I tried to get the Xubuntu live CD to run without success. So, now I am going to try Ubuntu 8.04, which is the newest version my brother is running.
 
Would CD burn speed have anthing to do with the problems I am having.
 
If this don't work, it's back to Windows XP Home Edition. **Never had these issues with it. **I hate for a machine to beat me, but I just don't have the time to invest in something that does not work for me from the start.

---

### Post by chzuck on 2010-05-10
OK, I just tried to install Ubuntu 8.04 and came up with yet another GRUB error. It came up error 18 right after it said GRUB loading. Is there something I need to change in my BIOS? Every version of Ubuntu I tried to load came up with some kind of a GRUB issue. Before installing 8.04 I cleanded the hard drive with Acronis of all data and partitions.

---

### Post by RJARRRPCGP on 2010-05-10
It's best to wipe the HDD and reinstall everything! That usually solves strange errors.

---

### Post by chzuck on 2010-05-10
To All,
**[SIZE=3][COLOR=red]I THINK I HAVE FINALLY FOUND THE PROBLEM![/COLOR][/SIZE]** 
I found a suggestion to setup the drive in LBA. I have done that and was able to install and run 8.04 from the hard drive. I am now in the process of installing Xubuntu, which after the change to LBA, I was able to run from the CD. I will let you know how I make out with Xubuntu.
 
I have used Acronis to wipe the Hard Drive clean between installs, including partitions.

---

### Post by RJARRRPCGP on 2010-05-11
> **chzuck said:**
> To All,
**[SIZE=3][COLOR=red]I THINK I HAVE FINALLY FOUND THE PROBLEM![/COLOR][/SIZE]** 
I found a suggestion to setup the drive in LBA. I have done that and was able to install and run 8.04 from the hard drive. I am now in the process of installing Xubuntu, which after the change to LBA, I was able to run from the CD. I will let you know how I make out with Xubuntu.
 
I have used Acronis to wipe the Hard Drive clean between installs, including partitions.

What do you mean by "LBA"?  

-> LBA was already selected, because LBA is the current sector addressing standard, has been, since 1996!

With CHS, your HDD would be limited to 504 MiB! LOL!

---

### Post by chzuck on 2010-05-14
I saw a suggestion on a forum to "set the drive up in LBA mode in the BIOS.  So I went under "primary IDE master" and found LBA mode control was set to Disable, so I enabled it and now I can load and run Xubuntu from my hard drive, where I could not before and was getting grub errors.

---

### Post by sunk8 on 2010-05-14
So the issue's finally resolved?
How's Xubuntu working for you?

---

### Post by chzuck on 2010-05-14
Seems to work pretty good.  Sometimes it gets unstable.  Loads multiple windows, cursor moves all over the screen by itself, but settles down and works OK.  The problem I am having now is trying to install my Epson Stylus Color 640 printer.  I turn the printer on and it does not recognize it.  I tried numerous methods within Xubuntu and some that I found on the forum.
 
I am learning that Linux is not for computer novices!

---

### Post by shiman6 on 2010-10-17
I think the problem for the Out of Disk error is the "round to cylinders" option that partition editors does. I installed 10.04 on my computer, got the error, and when i looked in gparted, there was 1mb of unallocated space in front of the main partition. I removed it and re-installing to see if it helps.

---

### Post by chzuck on 2010-10-17
Unfortunately I gave up with linux.  It seemed as though I would get one problem solved and something else would not work.  Much easier to stay with Windows!  It has its short comings, but not near the problems of Linux software!

---

