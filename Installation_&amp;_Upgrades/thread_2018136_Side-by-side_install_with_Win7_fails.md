---
title: "Side-by-side install with Win7 fails"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by muffled tone on 2012-07-06
I have an Acer Aspire 4741 with 2Gb RAM laptop with Windows 7 installed by manufacturer. I've never had any experience with Linux, but been interested for a while.
 
I decided to try Lubuntu but don't want to dump Win7 just yet, so:
1. I downloaded Lubuntu 12.04 x86 32-bit ISO and burned a Live CD
2. I tried a Live session, all's fine except for WiFi issue
3. Tried "Install Lubuntu within Windows 7, choose OS on boot" from within Live session, clicked "Next" and the screen turned black saying "Process terminated code [15]" or something, then telling me to eject CD and press [Enter] to restart and install. I think it should be asking me for which partition to use, not sure.
4. I press Enter, it restarted and... I boot into Win7 :confused:
 
So I figured, maybe I need to install from outside Live session, so I tried again, but same thing happenned.
I tried browsing my hard drive in case it's already installed but not available during boot menu, but no trace of Lubuntu whatsoever.
 
Checked the MD5SUM but it's OK, CHKDSK was also OK.
Tried searching the forum for something like this but couldn't find it, or maybe I was searching the wrong place? #-o
Anyway, can anyone help? Don't know what else to do.

---

### Post by wilee-nilee on 2012-07-06
> **muffled tone said:**
> I have an Acer Aspire 4741 with 2Gb RAM laptop with Windows 7 installed by manufacturer. I've never had any experience with Linux, but been interested for a while.
 
I decided to try Lubuntu but don't want to dump Win7 just yet, so:
1. I downloaded Lubuntu 12.04 x86 32-bit ISO and burned a Live CD
2. I tried a Live session, all's fine except for WiFi issue
3. Tried "**Install Lubuntu within Windows 7**, choose OS on boot" from within Live session, clicked "Next" and the screen turned black saying "Process terminated code [15]" or something, then telling me to eject CD and press [Enter] to restart and install. I think it should be asking me for which partition to use, not sure.
4. I press Enter, it restarted and... I boot into Win7 :confused:
 
So I figured, maybe I need to install from outside Live session, so I tried again, but same thing happenned.
I tried browsing my hard drive in case it's already installed but not available during boot menu, but no trace of Lubuntu whatsoever.
 
Checked the MD5SUM but it's OK, CHKDSK was also OK.
Tried searching the forum for something like this but couldn't find it, or maybe I was searching the wrong place? #-o
Anyway, can anyone help? Don't know what else to do.

A Install inside windows is done from windows and is called a wubi install, is this what you want? It is then a file in windows, not generally considered for long term use. If you want a wubi install you use its download tool from windows to install, getting it to download lubuntu is probably possible. The wubi installer is not on the live cd's any more.

If you want a actual dual boot alongside windows, give us a screen shot of gparted from the live lubuntu boot.

---

### Post by muffled tone on 2012-07-06
I tried installing from Live session, not from inside Windows. There was an icon on the desktop & I just double-clicked it.
The install options were:
1. Install within Windows 7 (and choose at boot time)
2. Replace Windows 7
3. Other installation

I picked the #1 option, but nothing happenned except for my laptop rebooting.

About your question:
1. No, I don't want it to run from inside Win7
2. Yes, dual-boot is exactly what I want
And I thought dual-boot is what I'll get with that #1 option, forgive me for my total lack of knowledge on this.
I'll try to get that "gparted" output you said & attach it, as soon as I figure out how to do that (I'll search for it first).

Thanks a bunch for the info, gonna do that right away.

---

### Post by wilee-nilee on 2012-07-06
> **muffled tone said:**
> I tried installing from Live session, not from inside Windows. There was an icon on the desktop & I just double-clicked it.
The install options were:
1. Install within Windows 7 (and choose at boot time)
2. Replace Windows 7
3. Other installation

I picked the #1 option, but nothing happenned except for my laptop rebooting.

About your question:
1. No, I don't want it to run from inside Win7
2. Yes, dual-boot is exactly what I want
And I thought dual-boot is what I'll get with that #1 option, forgive me for my total lack of knowledge on this.
I'll try to get that "gparted" output you said & attach it, **as soon as I figure out how to do that **(I'll search for it first).

Thanks a bunch for the info, gonna do that right away.

My mistake it helps to offer this info.

In the reply window panel is a paper clip that is how you attach an image to a reply. ;)

---

### Post by Mark Phelps on 2012-07-06
Go into Win7, open the Disk Management app and look at the set of partitions there.  IF you already have four, you can't install Ubuntu to a partition without removing a partition, first.  The installer does not know to do that and will not install.

---

### Post by msammels on 2012-07-06
Mark, couldn't he still do it, if one of his four partitions was an extended partition?

---

### Post by wilee-nilee on 2012-07-06
> **msammels said:**
> Mark, couldn't he still do it, if one of his four partitions was an extended partition?

One has to be removed to make a extended, but yes you are correct.

---

### Post by msammels on 2012-07-06
Well, I was thinking, 3 normal, 1 extended, that way... or maybe I'm being silly :P

---

### Post by wilee-nilee on 2012-07-06
> **msammels said:**
> Well, I was thinking, 3 normal, 1 extended, that way... or maybe I'm being silly :P

The key here for best help is really what I suggested, basically show us what is actually there, before actually advising, is really best practice in protecting the users OS's.

It does not have to be gparted it can be a fdisk -l as well.

---

### Post by muffled tone on 2012-07-06
Hey all, thanks for the replies.

So I found GParted, ran it in Live session, and it says I have 4 partitions.
While Windows' File Manager says I have 3?

According to GParted I have:
1 NTFS 100 Mb (apparently locked by Windows)
2 NTFS 100 Gb (1 for Win7 & 1 for my data)
1 NTFS 270 Gb (I install my apps here, separate from Win7)
I can also access all 4 in Lubuntu's File Manager.

So, since I have 4, I must delete 1?
Does delete here mean erase the partition OR just make it empty/available?

---

### Post by wilee-nilee on 2012-07-06
> **muffled tone said:**
> Hey all, thanks for the replies.

So I found GParted, ran it in Live session, and it says I have 4 partitions.
While Windows' File Manager says I have 3?

According to GParted I have:
1 NTFS 100 Mb (apparently locked by Windows)
2 NTFS 100 Gb (1 for Win7 & 1 for my data)
1 NTFS 270 Gb (I install my apps here, separate from Win7)
I can also access all 4 in Lubuntu's File Manager.

So, since I have 4, I must delete 1?
Does delete here mean erase the partition OR just make it empty/available?

Ubuntu needs other then a NTFS type partition to run, if you want a swap partition and a main OS partition you would put a extended where the one removed from is and put the logicals for the swap and ubuntu there. Some like to have a seperate home partition a s well, personally I don't bother with a separate.

If you feel you would like exact instructions post a screen shot of gparted.

Be sure to have the windows cloned before doing anything, the OEM installs have a single clone option, any installs pro versions and above have unlimited clone options.

Having a full backup in a clone is always a good thing. ;)

---

### Post by muffled tone on 2012-07-06
Thanks, wilee.
I'll try making a snapshot of it, and backing up data & make image of Windows too.

Sorry to ask but, what does it mean to make extended partition? And then logical? I have no idea what that is, nor what the difference is with "normal" NTFS or FAT (sorry, I'm a total noob).

And if I make 1 partition for Lubuntu and 1 for swap, PLUS the 3 old ones, there'll be 5 of them. Didn't you say the max is 4? Will I have to delete more than 1 partition? (bummer if that's the case).

---

### Post by oldfred on 2012-07-06
It means delete one and all the data in it. You will have to combine your Windows apps & data into one partition.

Then you can create a new extended partition with several Linux formated logical partitions inside it.


[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by zwygart on 2012-07-07
For the partition question I suggest you to read the wikipedia page : [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning) . Especially the section for primary and extended partition. 

For the filesystems (NTFS, FAT, EXT, SWAP, etc.) : [http://en.wikipedia.org/wiki/Filesystem#Microsoft_Windows](http://en.wikipedia.org/wiki/Filesystem#Microsoft_Windows)

---

### Post by muffled tone on 2012-07-07
Okay, I got the snapshot of my partitions. But it's from Windows Disk Management tool as Mark pointed earlier, not from GParted. Hope that's fine, cause I'm not familiar yet to Lubuntu and doing it from Windows are easier for me.
 
I intend to erase the "D:" partition, leaving it as unused space if I understand correctly, then let Lubuntu do "Automatic Side-by-side Install" with Win7. Is this correct?
 
I'll try it, hope it works! ;)

---

### Post by muffled tone on 2012-07-07
Thanks zwygart, I'll check them out.
Really need to learn a lot more of these stuff.

---

### Post by zwygart on 2012-07-07
> **muffled tone said:**
>  
I intend to erase the "D:" partition, leaving it as unused space if I understand correctly, then let Lubuntu do "Automatic Side-by-side Install" with Win7. Is this correct?

Yes, this will be the right way. Just pay attention to every step you do.

---

### Post by muffled tone on 2012-07-07
[zwygart: Yes, this will be the right way. Just pay attention to every step you do.]

It worked! Thanks for everyone's help.
With only 3 used partition and enough free unpartitioned space, the "Install Lubuntu along with Windows 7" worked automatically.
Now I can choose which one I want to boot at startup.

Everything in Lubuntu seems to work fine so far, except for my Broadcomm WiFi. A thread suggested to download from Synaptic Manager (if I'm not mistaken), but I couldn't find the package when I searched.

Plus, I don't have internet connection without my WiFi (I access this forum from Win7, where my WiFi works).
Is it possible to download the package(s?) from Windows & install them in Lubuntu offline? If so, can anyone inform me what package(s) do need & where to find them?

---

### Post by oldfred on 2012-07-07
synaptic is the older package manager, which I prefer, but they are promoting Ubuntu software center.

Best to use hard wired Ethernet connection as then you can directly download all the updates and it may just suggest what driver you need for wireless. 

If you know what .deb you need you can probably download any way you can and then install it.

---

### Post by muffled tone on 2012-07-07
Thanks "oldfred".
I don't know what packages I need to find, and since my WiFi is my only connection, guess I'll have to find some other way to do this.

Since I don't think it's appropriate to prolong this matter here, I'll mark it as solved & try to find more info on other threads. Thanks everyone for their kind help!

Some suggestions:
1. Another thread stated that Broadcom WLan drivers are included in Ubuntu & Xubuntu Live CD, but not in Lubuntu. It would be really helpful to have this kind of basic thing working out of the box in Lubuntu.
2. It's would've saved time & effort if the Lubuntu installer could detect & inform the user something like: "you have too many partitions already, please delete one", instead of just restarting without any explanation.

Well, just my 2 cents.

---

