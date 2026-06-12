---
title: "Bad install of Ubuntu 20.04.1  ??"
date: 2021-03-13
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2021-03-13
Hello all

I've had gobs of problems switching to 20.04.1. I seem to have a multitude of issues, simple or complex, that I don't know how to fix.

I installed it about 2 months ago and has never run right - as I thought it should.  I thought I wiped my hard before I installed Ver. 20.04.1  But I didn't realize there were some legacy programs I missed. I just now found a /properties folder in my 650 GB HDD. It's showing  17.8 GB being used  and 578.6 GB free. that I did not know was used. I  guess that most of the space was from the 20.04 install and Firefox. It  does seem to be alot of GB taking up space. 
At the time I installed it, I saw that these files did not seem to be enough to worry about. Could this be a part of the problems I am having?

My previous upgrades, Ver. 10.04 through Ver. 16.04, seemed to install and set up easily. But 20.04.1 seems to be missing some packages. I had to add VLC to watch video, but it still won't play files using Flash or HTML 5 files. I know Flash is discontinued, but shouldn't it still play legacy files?

It did not integrate with my HP wireless printer - which had worked perfectly under 16.04. 

But with 20.04.1, It will sometimes print wirelessly, but other times it will only work when it's connected to a hard line and sometimes not then. I tried the printing program that comes with Ubuntu (which is supposed to be identical to the HPLip,) The error message says it needs to be connected to a computer even when it is. I have tried to uninstall and re-install, I've tried simple scan to setup. It will then do a basic scan, but without features.

The worst problem I have to overcome is that every program I download, or try to install, will only open showing the code, but no GUI. This happens every thing I try to do. I'm OK using the terminal for uncomplicated things, but when there are dozens of lines I have look through just to do even simple things, I give up because of the time it takes. There is probably something simple that will fix the problem, but I can't find it 

Just now I have something happening that I really do not understand. I somehow hit an "Insert Section" with a message saying a file connection will delete the contents of the current section. "Connect Anyway?" has a choice of Yes or No. But it will not "Cancel or Reset." There's also a button to "Insert" which I have not a clue to what it can do.

Any help is appreciated. Thanks

My most frustration is with The new version of Firefox. I know this is out of context here so I will not go into to my issues. My big question is whether I should do an uninstall / reinstall. Or should I try to run an update. Chrome seems to work better, but I have data and settings that would take a lot of time to reconfigure or find. I did not setup many logins and passwords with a password manager. This results in hundreds of chits of paper. It would be amusing - it it wasn't true.

---

### Post by grahammechanical on 2021-03-13
Please explain the method that you used to "wipe" the hard drive. When you installed 20.04.1 did you choose the Erase Disc and install Ubuntu option or the Something Else option? If we choose the Something Else option we need to tell the installer which partitions are to be used as /root and /home. We also have an opportunity to have those partitions formatted. If we do not format the partitions already existing folders and files will not be removed.

In the past when you upgraded from 10.04 through to 16.04 did you use the online upgrade process provided by Ubuntu? When you "upgraded" to 20.04.1 did you do a fresh install? The online upgrade process will leave existing programs and related folders and files in place and may even upgrade the installed programs even if they are not part of the Ubuntu default set of programs. A fresh install will only install the default set of programs and VLC is not included in them. Neither would it include certain proprietary audio and video drivers. Neither would it include a flash video driver. These are things to be installed afterwards.

One reason for not formatting the home partition when we are reinstalling over an existing installation is to keep the configuration files and data folders associated with existing programs.

> Just now I have something happening that I really do not understand. I  somehow hit an "Insert Section" with a message saying a file connection  will delete the contents of the current section. "Connect Anyway?" has a  choice of Yes or No. But it will not "Cancel or Reset." There's also a  button to "Insert" which I have not a clue to what it can do.


Is this to do with the Ubuntu operating system or an application such as Libreoffice Writer?

Regards

---

### Post by Gnusboy on 2021-03-15
[URL="https://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]grahammechanical
[/COLOR][/B][COLOR=#000000]
I did something that acciden[/COLOR][/URL][COLOR=#000000]tly erased the response I was writing to Grahammechanical just now.
I tried to get it back with the restore auto saved content, that did not work. Is there another way I can get that data back?I did not know that an unintentional key stroke could do that.

This is a grand display of how my day is going.

[/COLOR]
Thank you for you help. I appreciate it.
Thinking back, I believe I used the overwrite

---

### Post by Gnusboy on 2021-03-16
My question: Should I erase the HDD drive again and do a complete re9installation?
                     Would re-installing Firefox and VLC be a viable choice.
                     Or, should I turn this entire system into a fishing weight or doorstop?

So, I'm still trying to figure out what I should do about the install of 20.04 on my desktop. It's an older system I built in 2010. I've kept it because it still runs well and handles my needs/
[SIZE=2]AMD Phenom X4 9850
4 GB Ram
650 GB HDD
2 Partitions ==
1 TB external HD
400+ GB partiton running 14.04 
500+ GB partition with 16.04
Ubuntu 10.04 continually updated to Ubuntu 16.04

I am still trying what is causing my problems. When I upgraded to 20.04 I had previously transferred all my important stuff to an external drive. I thought that by making a clean install, 
anything still on the internal drive would be erased. As I started installing 20.04 I noticed some data/programs left on the drive were being erased. I had planned for this and wasn't worried.
The install seemed to fine, but I did not see the various stages and programs I recall seeing in earlier distros. I can't recall exactly what the programs were and forgive me if I am misremembering the 
installation process. Nonetheless, I thought I read something about  20.04 designed differently that earlier versions. So, when I did not see what I was used to, I assumed it was related to 
changes made to the the new distro.
I later realized there were other programs that were not included and need separate installs. I believe this is when my problems began. I installed Firefox.I put in VLC, but something must have been wrong because it
was not working as expected. It did not play flash or HTML 5, YouTube and embedded video. I installed 4 add-ons:

HTML 5 Everywhere
Open in VLC media player
UBlock Origin
Privacy Badger
The Add-ons got it so I could watch some embedded video, but it does not work on all sites.

I have no doubt that my problems are self-inflicted. But is there a simple solution?
Thanks for helping.







[/SIZE][SIZE=2][SIZE=2]







[/SIZE]
[/SIZE]

---

