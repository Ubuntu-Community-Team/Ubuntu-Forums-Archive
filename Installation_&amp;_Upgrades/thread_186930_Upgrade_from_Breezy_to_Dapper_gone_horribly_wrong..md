---
title: "Upgrade from Breezy to Dapper gone horribly wrong."
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Ted_Smith on 2006-06-02
Hi

Fooloishly I took the plunge yesterday and upgraded Breezy to Dapper because when I read the Wiki HowTo it looked so straight forward I thought 'Hey, what can go wrong!'.

I ran 
```

gedit /etc/apt/sources.list

``` 
replacing 'breezy' with 'dapper' then ran

```

sudo apt-get update && sudo apt-get dist-upgrade

``` 

I got a few errors saying it couldn't download this and that so I ran 'apt-get update' (I think) and it downloaded about 300Mb of stuff and said certain things were to be removed and other things to be installed. I took about half an hour. 'Jolly good' I thought. Certain icons changed and I was warned to reboot due to major changes so I assumed all had gone OK. Robooted. Never been able to access it since!

When booting up normally it gets to the 'mounting root filesystem' and it just hangs for ages until eventually it drops to a shell warning me that it can't find HDE devices (I think - it's all becoming a blur!). 

I've tried using the recovery module and tried to follow the guide written by 'ubuntu_demon' [here]("http://www.ubuntuforums.org/showthread.php?t=186672") but I can't use gedit because I'm not in the desktop. I tried to use vim (from memory) but couldn't work out how to edit it. 

I've tried rebooting using the older Linux kernal in the hope that Breezy may be retianed in some way - it boots but doesn't display the desktop - I get all sorts of Xorg warnings. So I can't use that either now it seems. I'm writing this using one of my other PC's which luckily has an Internet connection. 

Can anyone help an idiot get his nice Linux system back up and running or will I have to do a fresh install (a bit Windowsey that though isn't it)? A shame because I'd got Breezy set up real nice and working well. I knew I should have waited a while before upgrading...

Ted

---

### Post by az on 2006-06-02
[QUOTE=Ted_Smith]Hi

Fooloishly I took the plunge yesterday and upgraded Breezy to Dapper because when I read the Wiki HowTo it looked so straight forward I thought 'Hey, what can go wrong!'.

I ran 
```

gedit /etc/apt/sources.list

``` 
replacing 'breezy' with 'dapper' then ran

```

sudo apt-get update && sudo apt-get dist-upgrade

``` 

I got a few errors saying it couldn't download this and that so I ran 'apt-get update' (I think) and it downloaded about 300Mb of stuff and said certain things were to be removed and other things to be installed. I took about half an hour. 'Jolly good' I thought. Certain icons changed and I was warned to reboot due to major changes so I assumed all had gone OK. Robooted. Never been able to access it since!

When booting up normally it gets to the 'mounting root filesystem' and it just hangs for ages until eventually it drops to a shell warning me that it can't find HDE devices (I think - it's all becoming a blur!). 

I've tried using the recovery module and tried to follow the guide written by 'ubuntu_demon' [here]("http://www.ubuntuforums.org/showthread.php?t=186672") but I can't use gedit because I'm not in the desktop. I tried to use vim (from memory) but couldn't work out how to edit it. 

I've tried rebooting using the older Linux kernal in the hope that Breezy may be retianed in some way - it boots but doesn't display the desktop - I get all sorts of Xorg warnings. So I can't use that either now it seems. I'm writing this using one of my other PC's which luckily has an Internet connection. 

Can anyone help an idiot get his nice Linux system back up and running or will I have to do a fresh install (a bit Windowsey that though isn't it)? A shame because I'd got Breezy set up real nice and working well. I knew I should have waited a while before upgrading...

Ted[/QUOTE]


Boot into recovery mode and run

sudo apt-get dist-upgrade

and then

sudo apt-get install ubuntu-desktop

You just have a few packages that did not install.  Maybe because the server was busy.

---

### Post by ubuntu_demon on 2006-06-02
You can use pico in the terminal instead of using gedit.

---

### Post by Ted_Smith on 2006-06-02
Thanks for you easy to follow response. I did as you said, it downloaded some more stuff and installed it, I rebooted, but the problem persists. What it says, exactly, is : 
```

Loading Essential Drivers : OK
Mounting Root File System : blank
Waiting for root filesystem : blank

```

And it just hangs for ages (about 3 or 4 minutes) until it drops out into the shell saying : 

ALERT : dev/hda2 does not exist

BusyBox Built In Shell
#

Sorry to be a pain

Ted

---

### Post by ubuntu_demon on 2006-06-02
First try booting into recovery mode.

If that doesn't work boot from a live cd. Mount your Ubuntu Dapper partition, chroot and work from there.

$sudo mkdir /mnt/dapper
use the correct device here .. for example /dev/hda6 :
$sudo mount */dev/hda6* /mnt/dapper
$sudo chroot /mnt/dapper

Now you can work again from dapper.

If you can't solve it and you don't want to try anymore you could always reinstall ofcourse .. but that's not very exciting is it ?:)

---

### Post by az on 2006-06-02
[QUOTE=Ted_Smith]
ALERT : dev/hda2 does not exist

BusyBox Built In Shell
#[/QUOTE]


Boot into recovery mode using an older kernel in your grub list.
[QUOTE=Ted_Smith]
Sorry to be a pain

Ted[/QUOTE]

Your not a pain.  Dude, c'mon.  Your the one up shit creek!

---

### Post by Ted_Smith on 2006-06-03
This is driving me mad now!! 

I tried to follow ubuntu_demons suggestion, but when I booted into recovery mode there was n mnt directory, so I wasn't able to execute the command. So, I booted using the live CD and firstly copies all my stuff to an external HDD. After faffing about for a bit (unsuccessfully) I gave up and downloaded the Dapper ISO. Rebooted with the CD. 

It boots up, and I click on the install. Looks great...lovelly GUI. Asked it to delete the former partition and create a fresh one and install to that. After about 15 minutes and at 34% it just froze...everything. The mouse, keyboard, the lot. Feeling like I was back with windows for a moment I had to hard reset and I tried again. Same problem. 

So, utterly furiated, I re-installed breezy. All went OK with that. I updated Breezy (without adding any unoffical repo's into the list) and rebooted. I then ran the Update Manager again and clicked the 'Upgrade' button next to where it informs you about the Dapper release. It goes like a charm. Took about 2 hours, but all went OK it seemed. Rebooted at the end like it asked, and guess what. Same god dam friggin problem!!!!!!!   

Loading Essential Drivers : OK
Mounting Root File System : blank (never goes to OK)
Waiting for root filesystem : blank (never goes to OK)

followed with : 
```

ALERT : dev/hda2 does not exist

BusyBox Built In Shell
#_

```

I'm totally in disbeleif. All I have is a normal desktop unit, AMD processor, 1Gb of RAM, 4 160Gb HDD's (not RAIDED) on a PCI IDE Adaptor, 1 X 120Gb HDD connected to IDE1 with Windows XP installed and Ubuntu. 

The only thing I can think of (and that I noticed) is that in Breezy the HDD is seen as 'IDE1' and the partition that Ubuntu install to is hda2 (hda1 being Windows). In Dapper, the same HDD is seen as IDE6 (noticed during install). When I boot with the Live CD, it reports the Ubuntu partition on IDE6, Partition 2, as DEV/HDE2. So, if it's looking for hd**a**2 on IDE6 when it's actually hd**e**2 I suspect that might be what's causing the problem. But how to fix it? I'm seriously thinking of just sticking with Breezy. Just noticed a bug report about this (it looks like) here : [https://launchpad.net/distros/ubuntu/+bug/5913/+index](https://launchpad.net/distros/ubuntu/+bug/5913/+index). I then went on to find this bug report : [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367) which seems to suggest that the problem lies with the fact that my Silicon Image PCI IDE Adaptor is seen first with Dapper, whereas with Breezy it's seen second to the IDE device on motherboard which is why it was OK with that. A solution is posted here : [https://wiki.ubuntu.com/ProbeForRootFilesystem](https://wiki.ubuntu.com/ProbeForRootFilesystem) but it doesn't seem to be very helpful and seems to be marginally sarcastic. Other comments seem to suggest that it has not been fixed for Dapper much to the displeasing of enterprise users.  

No disrespect to the people who develop Ubuntu of course. It's just that I am so amazed that I'm having such major problems installing a home desktop PC. If it was a corporate server or something I might have expected problems, but not at home and not with a straight forward install.

Ted

---

### Post by Irony on 2006-06-03
It says in the Wiki;

> EXTREMELY IMPORTANT! Make sure you type  dist-upgrade  rather than  upgrade . The process will totally hose your machine and render it *completely unbootable* otherwise.

---

### Post by RudolfMDLT on 2006-06-03
This is out of my depth so please correct me if i'm wrong! Couldn't you try booting with a live cd and editing the fstab file? In there you could piont Dapper to the correct drive?

Dapper ran fine on most other peoples pc's... Are you running any special hardware? Are you maybe running a Serial ATA drive with an IDE one - That sometimes couses trouble in XP?

---

### Post by rcarring on 2006-06-03
First, I have seen this error reported elsewhere in the forums. The precise problem of mounting root system and then it waits forever is described here:

[https://launchpad.net/distros/ubuntu/+bug/36508](https://launchpad.net/distros/ubuntu/+bug/36508)

The reason it fails is that you have an external usb mounted drive. Dapper gets confused with the order of devices, hence the situation you have where a drive is "moved" from hde2 to hde6.

The solution appears to be boot without the usb drive attached.

---

### Post by Ted_Smith on 2006-06-03
Rudo : Thanks for that one, but I'd already tried that. Logically you'd think that would work, but it doesn't appear to. it still hangs. I have no SATA devices attached. 

Rcarring : Thanks for your response. However, I don't have a USB drive attached and so cannot unplug it. The 'attached' drives in this case are effectively the 4 HDD drives connected to the PCI IDE Adaptor that cannot easily be removed, and besides, they have all my data on them. The links I gave earlier really do suggest it has not been fixed and will not be fixed until the version after Dapper.

---

### Post by rcarring on 2006-06-03
You say you have 4 hdd connected to an ide connector? I imagine you also have a cdrom as well?

My understanding is that you cannot have more than 4 primary partitions.  The 4HDDs and cdrom equal five primary partitions. 

OK, with scsi you can have a lot more than that, but that has been my understanding for several years. I admit, this is a limitation of DOS, so maybe it doesn't apply to Linux.

---

### Post by RudolfMDLT on 2006-06-03
You have "4 HDD drives connected to the PCI IDE Adaptor" and where is the CD-ROM connected or is this an expander card? Is it possible you could give us a complete PC spec and more importantly how these devices are connected? The 4HDD + a CD- ROM does sound a little suspicious? But we are all punching around in the dark until we know what exactly you are running? 

Sorry, just scrolled up and re-read your first post:

4x160Gb HDD's (not RAIDED) on a PCI IDE Adaptor, 1 X 120Gb HDD connected to IDE1 with Windows XP installed and Ubuntu.

OKAY! So you have 4 HDD filling up you PCI to IDE expander board. Then you have 1 HDD on  and a CD-ROM connected to the on board IDE controller. Your rally packing a decent machine! What you could try is the following:

Put you primary Operating System's drive at IDE 1 as the master. Remove the non-critical 160GB drives. Try installing Dapper now. Later, you can remount your other drives exactly as they where before you had to do the re-organization of you machine! The beauty of using Ubuntu above Windows is that you can chop and change drives, remount them later in there original folders and never see the difference. 

Just a bit of advice I never listen to :) : If it's not broken don't fix it! If you can't get Dapper to run, file a bug report, re-install Breezy and wait for the new distro in 6 Months time. This is a bad option and only a last resort. But surely the path of least resistance!

Next time, before you upgrade, backup you system files on 1 of the 640GB of space you have! :)

[http://www.ubuntuforums.org/showthread.php?t=81311&highlight=Backup](http://www.ubuntuforums.org/showthread.php?t=81311&highlight=Backup)

---

### Post by Ted_Smith on 2006-06-06
Rudolf

Firslty, thanks so much for an in-depth reply (although you have double posted it seems). I forgot to subsribe to the thread and so did not notice your reply until now. 

Your idea about disconnecting the drives and then upgrading to Dapper is an excellent one, and a trick I've used in the past when installing Windows to prevent silly drive letter assignments. I did not think of that IRO Linux. I think that will work. 

Annonyingly for me, I've spent all weekend and the last couple of evening re-installing Breezy and getting everything to work as I like, and am still having a few troubles with my Nvidia card. Had I read your post at the time I'd probably be up and runnin with Dapper as we speak, but hey ho. I think I'll leave it for now, and like you say, if aint broke, don't fix it. I may try again in a month or so if the mood takes me. 

And yes, she is quite a monster. When I built her about 3 years ago she was blinding - fairly standard by todays benchmarks, but she has lots of storage for sure!

Cheers

Ted

---

### Post by RudolfMDLT on 2006-06-06
[QUOTE=Ted_Smith]
Annonyingly for me, I've spent all weekend and the last couple of evening re-installing Breezy and getting everything to work as I like, and am still having a few troubles with my Nvidia card. Had I read your post at the time I'd probably be up and runnin with Dapper as we speak, but hey ho. I think I'll leave it for now, and like you say, if aint broke, don't fix it. I may try again in a month or so if the mood takes me. 

Ted[/QUOTE]
Hi,

Okay, that was stupid!:roll:  Sorry for the double post! Mostly before I post I copy the text into OO-Writer to check the spelling as English is my second language. I must have just pasted and posted without checking.

Nvidia is supposed to be widely supported in Linux. I don't know if you know about Easy Ubuntu? It's a handy little app that does most of the initial irritating things like download all the Win32 codecs, Installs Xine, puts numlock on at startup and has a option for installing 3D drivers for Nvidia and ATI, anyway, it helps get the system functional to a good point. But I take no responsibility for a muck up concerning the install of the drivers. They work on my system(ATI 9600 Pro) but install it at your own experimental risk! :) It has a remove script but as far as I know it is still in beta phase.

Checkout the link:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Cheers!

---

### Post by mlwmohawk on 2006-06-08
If you have a second IDE controller in your system, that's the problem. The Ubuntu guys mucked up and on systems with additional drive controllers the enumeration order may be reversed between Breezy and Dapper. 

I am really pissed off about this and this is the sort of bug that should have been a show stopper, but they knew about it and didn't think it was an important bug.

---

### Post by wpshooter on 2006-06-08
I have found over the years that trying to upgrade from one O/S to another is problematic, at best.  This applied to Microsoft windows and it appears that this applies to Ubuntu/linux also.

IMO, always save/backup any data, etc. that you need from the old O/S (with a method, of course, that will allow you to get it back on the new system), wipe everything out and then reinstall the new O/S from scratch.

---

### Post by RudolfMDLT on 2006-06-08
I'm upgrading to Dapper tonight and I agree with wpshooter, an upgrade is just a delay of a clean install.

---

### Post by Ted_Smith on 2006-06-09
I am replying with joyous news in the hope that my reply will help other poor sods like me who fall victim to this 'rather major development oversight'. 

I am happy to report that I am now using Dapper! How did I do it I hear you ask? Well, firstly, I disconnected the drives that I didn't need as suggested by Rudolf earlier. I then removed (temporaily) all the mount references in etc/fstab and copied them to a text file in my home folder for use later. Then I downloaded and burnt the iso of Dapper Drake to CD for use later. 

I then used the Synaptic upgrade to upgrade the OS. Rebooted to find out the problem was still there ('ALERT! /dev/hda2 does not exist' was the error), as I kind of expected. So I rebooted using the Dapper Live CD to see how Dapper itself decided to assign my drives. The Partition with Dapper installed on it was seen by the live CD as /dev/hde2 (not dev/hda2 as it thinks by looking at the boot loader). 

So I discovered that I needed to edit /boot/grub/menu.lst. So, from the live CD dropped to a terminal : 

```
 
sudo gedit boot/grub/menu.lst 

```
and where it said : 

```

kernel /boot/vmlinuz-2.6.15-1-686 root=/dev/hda5 ro 

```
I changed it to 
```

kernel /boot/vmlinuz-2.6.15-1-686 root=/dev/hde5 ro 

```
Rebooted, and it worked! When I get chance I will also edit the other instances (such as the Recovery Modes etc) to make they boot correctly when I need them, but at the time of writing this I've just changed the top entry. I had the expected problems with Xorg and have had to re-install the Nvidia drivers, but I expected that due to the Kernal revision. Of course I then had to copy and paste my mount points back into fstab after having reconnected the drives. 

I'm now using Dapper. 

I get the impression that the problem is not purely related to Ubuntu, but rather the 2.6.15 Linux Kernal generally. Google reports many instances where this has happened to other people and they're not all using Ubunutu. It's a major issue though, and a total show stopper for anyone who's newly trying to get into Linux. I hope by documenting this someone else may find it and get their own systems fixed, even if they don't use Ubuntu.

---

### Post by RudolfMDLT on 2006-06-10
I'm running Dapper aswell! took about 45min to backup, reformat and do a clean install. I really believe in doing a clean install over a backup!

TED! I'm really glad for you, but hell, the solution was complicated!](*,) 

It would be great if you could make this particular solution avaliable to the developers, or in a HOW TO, because i'm sure there are a lot of people with major complex drive arrangements!

Anyway! Good for you!

Cheers!:D

PS: ignore the spelling errors if any as OO's dictionary on Dapper doesn't work (yet)! :(

---

### Post by Ted_Smith on 2006-06-11
> TED! I'm really glad for you, but hell, the solution was complicated 

Thanks - I feel proud as punch myself for getting what seems to be quite a mjaor problem fixed :D 

> if you could make this particular solution avaliable to the developers, or in a HOW TO - it would be an honour! How do I go about doing that? Do you know?

---

### Post by RudolfMDLT on 2006-06-12
I don't really know, you could probably just create a post on it, or file a bug report. But check out this link on the ubuntu.com page, specifically the  "Quality Assurance and Bugs" heading.
[http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

---

### Post by Ted_Smith on 2006-06-17
HowTo written. I hope it's useful for someone : [http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)

---

### Post by cAuL on 2006-06-25
This actually helped me alot :-D
I shot almost 4 days by trying to get this *#-_\ dapper run

---

