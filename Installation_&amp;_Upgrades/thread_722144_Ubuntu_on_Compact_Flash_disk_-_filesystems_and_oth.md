---
title: "Ubuntu on Compact Flash disk - filesystems and other options"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by makkan77 on 2008-03-12
**Prelude** - not required reading if you like skip directly to the Question 2 below

Last week i purchased a CF>IDE bridge (Lycom) to use as hard drive in my rather old Toshiba laptop*. 
With my first install I borrowed two CF cards (Sandisk 2 GB/256 MB)  from work and installed fluxbuntu on the laptop. Normally I install fluxbuntu on this machine formatting the HDD as ext2 (it's speedier on an old system) but with this install I choose the guided setup thus getting ext3 and swapspace by default. 

I had no problems what so ever with this install, it worked all through out the weekend with me doing system updates and basic usage. I should also state that this setup seemed faster and more responsive than the old 2,5" HDD I normally use. Needless to say also dead quiet. 

Then came monday and I had to return my borrowed cards. So I bought myself a Sandisk Ultra II 2GB card and proceeded to install a fresh fluxbuntu system. This time however I choose to do my own partitioning and made a ext2 filesystem and a small 96 MB partition for swap. The install went smoothly but then came some problems. 
For some reason my system (with every *buntu flavour I've tried) drops to console during boot and needs the following commands to start again: 

[INDENT]modprobe ide-disk
modprobe ide-generic
mount -t ext2 /dev/hda1 /root 
CTRL-D [/INDENT]

To avoid this at every boot time I read that I should make a new initrd image with yaird. So I downloaded yaird and replaced my initrd image with "yaird -o nameofinitrdimage" (I did all of this in my weekend project too). After rebooting the problems started. The first failure was related to mtab not having references to something. After rebooting again I was forced to do a fsck which failed and dropped me to console. I did a manual fsck only to get a massive amount of problems (I/O failure, inode problems an so forth) with my HDD (read CF disk).

**Question 1**

Instead of trying to work it out I decided to reinstall. But I thought I'd get some notes from the community first. What could I have done wrong?

**Question 2**

What filesystem should I be using. I have both googled and searched this forum but the answers wary quite alot. Some suggest journaling others strongly disagree. Therefore I would like to know if anyone has sucessfully used a CF card as a system disk for any longer period of time. What filesystem you have been using. And also if you have made any other tweaks to your system. 

**NOTE**: My system only has 96 MB RAM therefore I'm a bit unsure wheter I could live without swap or not.


**Toshiba Satellite 320 CDS, 233 MHz, 96 MB RAM, 4 GB HDD (to be replaced by 2 GB CF card in *bridge).

---

### Post by PmDematagoda on 2008-03-12
Perhaps Fluxbuntu may need certain parameters to boot up properly, such as "ide=generic".

An ext3 filesystem is highly recommended over ext2 since ext3 is more reliable and less likely to fail.

And in your case, I think a reinstall would be much easier.

---

### Post by makkan77 on 2008-03-12
Thanks for the quick reply... 

> **PmDematagoda said:**
> Perhaps Fluxbuntu may need certain parameters to boot up properly, such as "ide=generic".
Would this fix the problem I have with having to load ide-disk/ide-generic and mount my root filesystem. I that case I should state that I have had this problem with all with both ubuntu 7.10 and xubuntu 7.10 aswell. However I have never tried the "ide=generic" boot command.

> **PmDematagoda said:**
> 
An ext3 filesystem is highly recommended over ext2 since ext3 is more reliable and less likely to fail.

And in your case, I think a reinstall would be much easier.

From what I've read in these and other forums some people do not recommend using journaling filesystems since they cause extra writes to the CF card thus giving it shorter life.

---

### Post by PmDematagoda on 2008-03-12
> **makkan77 said:**
> Would this fix the problem I have with having to load ide-disk/ide-generic and mount my root filesystem. I that case I should state that I have had this problem with all with both ubuntu 7.10 and xubuntu 7.10 aswell. However I have never tried the "ide=generic" boot command.
No one can give a 100% guarantee, but it would be worth a try.

> From what I've read in these and other forums some people do not recommend using journaling filesystems since they cause extra writes to te CF card thus giving it shorter life.
Yes, it is true that there are extra writes, but it all comes down to your choice, you could either use ext2, ext3 or any other file system that fits your needs.

---

### Post by makkan77 on 2008-03-12
Well if ide=generic works it would be fantastic. I really have no clue why I should have to use yaird -o but it works, maybe I should read up on that ;)

Regarding the filesystems I hope someone using CF as HDD will be able to shed some light on what to use. Especially long term usage.

---

### Post by makkan77 on 2008-03-14
bump

---

### Post by markp1989 on 2008-03-14
i would recommend you add the following to you /etc/fstab file

```
tmp     /tmp            tmpfs   noexec,nosuid,rw,size=1024K     0       0
vartmp  /var/tmp        tmpfs   noexec,nosuid,rw,size=1024K     0       0
varlog  /var/log        tmpfs   noexec,nosuid,rw,size=2048K     0       0

```

this will keep all logs and temp files in ram , therefor reducing  writes to the flash drives, but any logs will be lost upon rebooting 

i do this on  my eee pc which uses a solid state drive, not a CF card but still flash storage

---

### Post by makkan77 on 2008-03-14
Even though I only have 96 MB of RAM to start with?

---

### Post by markp1989 on 2008-03-14
> **makkan77 said:**
> Even though I only have 96 MB of RAM to start with?

the size of them ram disks will only use up 4mb of your ram

---

### Post by makkan77 on 2008-03-14
Ah.. I see that now.. 

BTW whats your take on choice of filesystem? ext2, ext3 or something else? 

Also i noticed Icebuntu in your signature... would you recommend trying it out? Is it as ready as fluxbuntu?

---

### Post by markp1989 on 2008-03-14
> **makkan77 said:**
> Ah.. I see that now.. 

BTW whats your take on choice of filesystem? ext2, ext3 or something else? 

Also i noticed Icebuntu in your signature... would you recommend trying it out? Is it as ready as fluxbuntu?

i personaly use ext2,on  flash drives

i would recommend that you try Icebuntu (im the dev), how ever it is not as ready as Fluxbuntu yet.

edit: currently there is no alternative install CD , only a live cd, that can be instaleld, im not sure how well the installer will perform on 96mb of ram.

if you do decide to have a go, to install it , boot from the live cd, press "ctrl+alt+t" to open up the terminal, and type "ubiquity" this will run the ubuntu installer, which can be slow to install on some systems, but should run well once installed

I currently have installed Icebuntu on a 1gb cf card

---

### Post by makkan77 on 2008-03-15
> **markp1989 said:**
> i would recommend you add the following to you /etc/fstab file

```
tmp     /tmp            tmpfs   noexec,nosuid,rw,size=1024K     0       0
vartmp  /var/tmp        tmpfs   noexec,nosuid,rw,size=1024K     0       0
varlog  /var/log        tmpfs   noexec,nosuid,rw,size=2048K     0       0

```



I did this yesterday and havent had any problems so far. But I did get a feeling that I should check up on something when I installed a new app with aptitude. What about aptitudes own logs/database isn't that lost at every time i reboot? Or are the logs in var/log only for humans, and cause no damage if they are lost?

I should also mention that I might have solved the read/write problem, it's really to early to tell for sure but I did turn off all references to DMA (in bios and in linux) and haven't had any problems since. One possible explanation is that  my CF>IDE bridge didn't support DMA.

---

### Post by makkan77 on 2008-03-17
Seems I didn't solve my IO, Read/Seek/Write and whatnot issues at all by turning off DMA. It might have been some other issues with ext2 filesystem just dying from two many hard-reboot due to a total system hang. 

I did try to reinstall a system completely but then Dariks Boot & Nuke couldn't even finish correctly (with DMA turned off in bios). Which is wierd since there seems to be no physical problems with the card when I access it from another computer (in a card reader). Also I did start a new installation of fluxbuntu that failed in installation phase. 

I also read today that the CF>IDE adapter I have ([_Lycom_]("http://www.lycom.com.tw/ST317p4m.htm")) does [support _DMA_]("http://forum.thinkpads.com/viewtopic.php?t=41568&postdays=0&postorder=asc&start=120&sid=40b5e517f35a9b95c805523d1fc07c33"). So this shouldn't really be an issue. 

I will try to reinstall the system today using ext3 as a filesystem instead. As I did the first time I was successfull.

---

### Post by markp1989 on 2008-03-18
> **makkan77 said:**
> Seems I didn't solve my IO, Read/Seek/Write and whatnot issues at all by turning off DMA. It might have been some other issues with ext2 filesystem just dying from two many hard-reboot due to a total system hang. 

I did try to reinstall a system completely but then Dariks Boot & Nuke couldn't even finish correctly (with DMA turned off in bios). Which is wierd since there seems to be no physical problems with the card when I access it from another computer (in a card reader). Also I did start a new installation of fluxbuntu that failed in installation phase. 

I also read today that the CF>IDE adapter I have ([_Lycom_]("http://www.lycom.com.tw/ST317p4m.htm")) does [support _DMA_]("http://forum.thinkpads.com/viewtopic.php?t=41568&postdays=0&postorder=asc&start=120&sid=40b5e517f35a9b95c805523d1fc07c33"). So this shouldn't really be an issue. 

I will try to reinstall the system today using ext3 as a filesystem instead. As I did the first time I was successfull.

do you mind me asking how you turned dma off, because currently on my cf card it hangs whilst waiting for dma every boot

---

### Post by makkan77 on 2008-03-18
Well I'm not really sure I did turn off DMA since I got errors again after a while but I'll be happy to share the info I got hold of. 

First I turned it off in my bios (I have a really old laptop so my choice is Standard IDE and EIDE) I choose standard. 

Then I also tried the following boot parameters: 
**ide=nodma **
This supposedly turns off DMA for the whole IDE interface, maybe you don't want that if you want to use a DVD-player with DMA, in that case: 
**hda=nodma **
Is probably better

I also found these two commands today I haven't tried them yet though. 
ide0=0 
ide1=0 
I assume ideX is the harddrive you want and =X is either 1 or 0 i.e on or off (but I'm not sure)

---

### Post by makkan77 on 2008-03-18
This might be helpful
[http://www.promethos.org/lxr/http/source/Documentation/ide.txt]("http://www.promethos.org/lxr/http/source/Documentation/ide.txt")

---

### Post by dicecca112 on 2008-03-18
anyone know where these are available in the US?  Doesn't have to by Lycom as long as it does the same

---

### Post by makkan77 on 2008-03-18
From what I've read in other forums most americans seems to use  a similar device from addonics (which according to the pictures I have seens looks exactly the same as my lycom device).

---

