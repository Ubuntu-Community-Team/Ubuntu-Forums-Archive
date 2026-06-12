---
title: "Install Does Not See RAID0 SSD"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by Hipster Doofus on 2011-12-23
Started with a thread over here>
[http://ubuntuforums.org/showthread.php?t=1883773](http://ubuntuforums.org/showthread.php?t=1883773)

Bit the bullet, redownloaded ubuntu & went to install it along side windows from a usb stick.

Booted OK. Got to the screen dealing with location & partitions & it says 'This computer currently has no operating system.' (Windows 7 is loaded)

Cancelled out of that & it continued to load to the live session. 

I have raid0 SSD as the primary. (Windows loaded with an unallocated amount of 57gb at the end)

I also have raid0 HDD for storage.

When booted into the live session I can see the HDDs but not the SSDs.

Why can't the install see the SSDs? Is there something I am missing?

---

### Post by BC59 on 2011-12-23
Some help:

[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

BIOS settings for SSD
[http://www.ocztechnologyforum.com/fo...l=1#post567561](http://www.ocztechnologyforum.com/fo...l=1#post567561)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Hipster Doofus on 2011-12-23
So from those guides, thanks btw, I can do that from the usb live? Because at this stage I can't get ubuntu install to see my windows OS. It wants to install over the top.

---

### Post by darkod on 2011-12-23
Have you tried using the alternate install image which you should be using for RAID? Because the desktop image can recognize raid people have been ignoring the recommendation to use the alternate image, but it still stands.
Not sure if it has more drivers support and maybe it will be able to read the SSD raid which the desktop image can't.

You should be able to create usb with the image, either by using ubuntu's Startup Disk Creator or universal usb installer, etc.

---

### Post by Hipster Doofus on 2011-12-23
Thanks darkod.

Downloading the alternate now. Does it install with a gui like the desktop version? 

If I go with 'Install along side Windows' is there anything I need to watch for? Grub for example.

I just want to let the install take care of the partitioning. I'm not up to it as yet.

Edit - Just saw that it has gui. So here's hoping.

---

### Post by Hipster Doofus on 2011-12-24
Got a bit further. When trying to create the partitions I got 'device 126 failed'.

Screenshot shows the drives although my SSDs do not have a manufacturer name. I tried to create the partitions into the free space.

I now have this as shown in windows management.

Should I have configured 'software raid'?

---

### Post by darkod on 2011-12-24
No, linux software raid can be used only if you run only linux. Windows can't see it and can't install on it.
There is something weird. The Raptors raid0 is correctly reported but the SDD raid0 is actually reported as software raid.
It might be that the mobo raid configured the array in a weird manner, or during the windows install it wrote something on the raid that the ubuntu installer can't understand.

Are you using the bios raid for both arrays or you have a raid card, etc?

---

### Post by Hipster Doofus on 2011-12-24
Using the bios raid for both. It could very well be the SSDs as corsair had nothing but trouble with them until their latest firmware. Windows would stop seeing the drives amongst a few other issues.

Maybe it's Ubuntu turn not to see them correctly.

What would happen if I partitioned the raptors & installed Ubuntu? Would Ubuntu be able to see the SSDs OS in grub?

---

### Post by darkod on 2011-12-24
Again, the ability to recognize win7 depends on the ability to recognize the SSDs correctly. One can't go without the other. You could install on the Raptors but whether it will see win7 remains a question I guess.

On another note, I hope you are aware of the risk of running raid0 because it has no redundancy for your data. Not only that you are running raid0 on the SSDs for the OS, you are running it on the Raptors for the data.

If one disk goes dead you lose all the data in raid0 array, you are probably aware of that.

It's one thing to have raid0 to test transfer rate etc, but if you plan to run them long term in raid0...

---

### Post by Hipster Doofus on 2011-12-24
Yeah aware of the risks. Been running raid0 for years.  All important data backed up......most of the time. :D

Think I'll leave it for now & try again from time to time & see if ubuntu can pick up the SSDs. If they do I'll post back.

Thanks BC59, darkod. Helped in getting me a lot further.

---

### Post by inobe on 2011-12-24
just to test it out, see if opensuse sees them, also the array.

the dvd has all the tools.

[http://www.opensuse.org/en/](http://www.opensuse.org/en/)

---

### Post by Hipster Doofus on 2011-12-24
I was just about to download another distro. Great minds. :D

Will be back.

---

### Post by inobe on 2011-12-24
> **Hipster Doofus said:**
> I was just about to download another distro. Great minds. :D

Will be back.

yeah, it's not your average distribution, a bit on the complex side, yet it's a performer with polished De's.

the install process is pretty straight forward, i dual boot opensuse and kubuntu, i don't have raid on this box, my other box is raid5 opnensuse 12.1, it has great fault tolerance and performs just as good in comparison to raid0, a drive fails, i just replace it, all is good...

the install process, a super guide with other cool howto's

[http://opensuse-guide.org/installation.php](http://opensuse-guide.org/installation.php)

---

### Post by Hipster Doofus on 2011-12-24
OK. Seems to have done the trick. Only issue was when setting up it asked if it should install mdraid (think that's what it was) but it only showed the HHDs. However when it got to the partition page the SSDs were there.

So from the second screen shot the 'F' 'F' 'F' is the free space. If I continue from screen shot one with the suggested partitions all should go according to plan?

---

### Post by inobe on 2011-12-24
it looks like the proposed setup will dual boot opensuse and windows.

what's the pen drive?

looks like it's a go, especially if all your important stuff is backed up?

it's easy to reinstall an os, not so much when you lose valuable data..

---

### Post by Hipster Doofus on 2011-12-24
The pen drive is the TDK usb drive with Universal USB Installer on it.

Quick question. What the go with the mount points? If I leave them would not I then need to have the usb (E-pen drive) plugged in all the time?

---

### Post by inobe on 2011-12-24
i don't really know, i usually leave them disconnected, then mount them later once all is installed, updated, upgraded.

i doubt it would be trouble to leave it.

edit: i disconnect extras, eliminates confusion :lol:

---

### Post by Hipster Doofus on 2011-12-24
Time to try an install.......once the backup is complete. I'll be back.

---

### Post by inobe on 2011-12-24
goodluck, i'm out for a bit, have fun.

be back in an hour.

---

### Post by Hipster Doofus on 2011-12-24
I can't catch a break.

Now when it gets to the actual install I get this.

Any ideas?

---

### Post by inobe on 2011-12-24
looks like the 2gb swap partition.

this is a first for me.

what are the other options after aborting?

i'm not sure selecting continue will finish root and home partitions, if it does, you won't have a swap partition.

i really don't know the affects, it's all new to me.

---

### Post by Hipster Doofus on 2011-12-24
After aborting I followed the screens to rebooting. I'm going to try a dvd to see what happens to the pen drive mount & see where it want to go.

It is something to do with the swap partition.

I going to head over to the opensuse forums & have a look around. 

Big thanks for all the help. I'm getting closer. :)

---

### Post by inobe on 2011-12-24
again, that's a first, the os forums will be of good assistance.

---

### Post by Hipster Doofus on 2011-12-25
Looks like raid is going. Another install of windows coming up. Good thing I'm not activating it each time.:lolflag:

Now I have to decide which distro to go with.

Being a complete noob to linux any suggestions? Ubuntu or openSUSE?

I'll probably end up giving both a go.

---

### Post by inobe on 2011-12-25
to test the read and write speeds, open terminal/ konsole then type

```
su
```

hit enter and type root password.

now type

```
hdparm -tT /dev/md0
```

or whatever **md** is your home partition, md is raid, sd isn't.

my kubuntu 11.10 on a single drive.

```
sudo hdparm -t -T /dev/sda
[sudo] password for xxxxx: 

/dev/sda:
 Timing cached reads:   8034 MB in  2.00 seconds = 4019.49 MB/sec
 Timing buffered disk reads: 408 MB in  3.01 seconds = 135.38 MB/sec

```


not bad for a single drive.

on topic, being new to something requires time to learn and understand it, to get what you need from it.

with any distribution this is possible, but if we suggest which one, you are more than likely going to test the other anyway:P

---

### Post by darkod on 2011-12-25
Again, these is some confusion with the SSDs about linux software raid. mdadm is the package for linux softraid. On the other hand you said you are running bios raid (fakeraid).
The devices in fakeraid are assigned /dev/mapper/blahblah, and in softraid /dev/mdX.

Also I have seen that md124 might mean problems, one user on the forum had similar problem and changed the md124 manually to md0 and it worked. But he was running softraid, so that part was right.

I wonder if you have some remains of softraid on the SSDs. In case you want to start all over, you should try removing any mdraid data on them. So, if you are staring all over, try this:

Boot with ubuntu cd in live mode and install mdadm because it's not included:
sudo apt-get install mdadm

Assuming your SSDs are /dev/sda and /dev/sdb, do:
sudo mdadm --zero-superblock /dev/sda
sudo mdadm --zero-superblock /dev/sdb

That should get rid of any mdadm information that might be there.

After that try configuring the bios raid again, and just for test, start with the ubuntu alternate cd as if installing. In the partitioning step select Manual and take a look if both bios raid devices are shown and recognized.

If yes, cancel the install. In stall windows first and then ubuntu with the alternate cd.

---

