---
title: "Ubuntu 11.04 added Linux Mint partition?"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by jjb2011 on 2011-06-15
When I installed Ubuntu 11.04 (64-bit) alongside Windows 7, there was a choice to add either Ubuntu or Linux Mint. Alas, it wouldn't let me click either one so I hit "enter" and it installed both! 

I've got Ubuntu 11.04 running and am now converted to the whole Linux experience (except I turned it back to Ubuntu Classic interface). 

QUESTION: How do I get rid of the 70GB Linux Mint Partition without borking my computer??? When I start up my PC it lists Ubuntu, then Windows 7, then Linux Mint. 

Help! 

(I'm NOT doing a clean install or reinstall after all the tweaking I did. I'd rather "eat" the 70GB loss to Linux Mint). 

THanks in advance.

---

### Post by nzjethro on 2011-06-15
Hi jjb. Welcome to Ubuntu. By the sounds of it, if you've got Mint on a separate partition, you should be fine to wipe that partition with GParted, and then hunt around for a programme that will add that 70GB to your Ubu partition (they're out there, but I can't remember a name off the top of my head).
Maybe just to play it safe take a screenshot of Gparted and post it here in a reply, and run [this scrpit and post the results here.]("http://ubuntuforums.org/showthread.php?t=1291280")

It sounds as though Grub is installed on your Ubu partition (as it comes up in the Grub list first), but if you provide us with a screenshot and the bootinfo script we'll be able to see what you can and can't do without cooking the system. :D

---

### Post by jjb2011 on 2011-06-15
I tried the terminal command with the .sh program. As a newbie, I'll concede that I know how to do tarballs, .deb and more but .sh stump me. The terminal commands never seem to work. 

I only had time to take screenshots with "Shutter" (nice program). See attached. Does that help? 

70GB is no big deal. I just don't know what the same thing to happen on my next install to a PC. Does the Ubuntu 11.04 automatically give you that choice? And, if so, was there a bug in the early software install program? 

Thanks.

---

### Post by nzjethro on 2011-06-15
Ok, from what I can tell form that, you should be fine to wipe your Linux Mint partition. And what's more, if something comes up and we break the system, then as long as you don't touch the Ubuntu partition, it'll be easy enough to fix it.

To get rid of Mint, open a Terminal (ctrl + alt + t), and type:
```
sudo gparted
```

If it's not installed, install it (it'll give you the code). Then, you want to find your Linux Mint partition in the GParted GUI (it'll most likely be sda1, sda2 or something). You want to absolutely make sure it is your Mint install, not your Ubuntu install, so if in doubt, take a screenshot with GParted open, post it here, and we'll double check it.

When you know which partition your Linux Mint is, right click that partition and select "Delete", then go Edit > Apply all Operations. Before you can delete it, you may have to Unmount th Mint partition. This will give you a good indication of if you have the right partition, because GParted won't let you unmount your Ubuntu partition while you are in Ubuntu, but it will let you unmount your Mint partition.

When you have applied the operation, close Gparted, and run
```
update-grub
```
This will rewrite your grub.cfg, so that Mint won't appear in your Grub list when you start-up.

Done! Post back if you have any issues, and I'm sure someone will be able to help out.

EDIT: Oops, didn't answer your second question. I've only updated from 10.10 to 11.04 (and then back again 'cos I didn't like it), never done a clean install. It's possible that there was a bug, in it's early stages Natty was quite buggy. But they may have developed it like that, seeing as how Linux Mint is essentially Ubuntu with a green colour scheme and the multimedia codecs pre-installed. They may give people the choice so that if you want Ubuntu you can have Ubuntu, and if you want Ubuntu + the rest, you can have Mint. But tha fart that it installed both is likely a bug. [Report it]("https://help.ubuntu.com/community/ReportingBugs") if you like.

---

### Post by jjb2011 on 2011-06-16
Here is the screenshot using Gparted. I'm guessing it is sdb5

Note that when I boot up there are two Ubuntu options (the regular one and a recovery option). Ditto with Linux mint so the other smaller partition might also be a Linux Mint partition? 

They could make the partition info. a little more transparent. I know I'm a newbie but . . . 

So do I delete sdb5?

---

### Post by jjb2011 on 2011-06-16
My bad. Here it is.

---

### Post by nzjethro on 2011-06-16
> **jjb2011 said:**
> Here is the screenshot using Gparted. I'm guessing it is sdb5

Note that when I boot up there are two Ubuntu options (the regular one and a recovery option). Ditto with Linux mint so the other smaller partition might also be a Linux Mint partition? 

They could make the partition info. a little more transparent. I know I'm a newbie but . . . 

So do I delete sdb5?

By the looks of it, Win is sdb1, sdb2 is empty (data space?), sdb7 is Ubuntu (as we can see the mount point is"/", and sdb5 is Linux Mint (I checked and about 4GB sound right for a clean, untouched Mint install). So I'd say it is indeed 5. Go ahead and delete sdb5. Also, you could probably delete whichever swap partition (sdb8 or sdb6) is aligned to Mint (not sure how you tell which is which but I'd guess sdb7). Down the track, you could look into moving your Ubuntu partition across to be right next to Windows, so that you could expand your sdb2 into the freed up space to get more storage space. Let me know if you have any issues with or after deleting sdb5.

---

### Post by jjb2011 on 2011-06-17
Hey, guys! I got everything working as you suggested. Thanks!

I was so "high" on Ubuntu (as I configured it) until I got home and installed it on my desktop there and then . . . I remembered why I always dropped Linux in the end: wireless doesn't work and the computer is in a bad place for the ethernet card. Seems my work PC worked because it has a ethernet connection. 

I'll post this elsewhere but it's real sad that this one deal breaker kaboshes a beautiful OS (yes, I've read and read and read about how to work around the wireless issue but Ubuntu is reliant on third parties who couldn't care less).

Thanks again. I got Ubuntu working on one desktop. Sweet.

---

### Post by Mr.Dee on 2011-06-17
Ya hardware will sometimes not cooperate with Ubuntu.  I have a laptop and a netbook, both which did not work with wireless.  I did quickly find other Linux distros that worked like a charm. Backtrack 5 & Joli OS.

---

### Post by jjb2011 on 2011-06-17
That's too bad because I was hoping (as the resident geek at my institution) to get some people to switch. But who uses desktops tethered to an ether line (except some people at work but that number is down too or takes advantage of the VPN wi-fi network. 

Looks like as Linux gets better, it's potential diminishes. How ironic. Oh, well, it's a hobby.

---

### Post by jjb2011 on 2011-06-17
Latest screenshots (sigh). I tried to delete SDB5 as directed but then it said to delete SDB2 so I did. Now it says delete partitions HIGHER. Grrrrr. I tried to but it said "only root" can do that" and I went to Pysym Storage Device Manager to unmount and it was greyed out. 

Things just "work" with Windows or Mac. Never had so much trouble with partitions and rules and regulations. Makes the system safe and unusable. 

Help!

---

### Post by oldfred on 2011-06-17
It is not saying delete partitions, I hope you did not. It is saying unmount.

Any partition mounted in the extended partition mounts the extended partition. You have to use liveCD to edit partitions and even then the liveCD mounts swap to speed things up. So you have to click on swap(s) and right click swap off.

---

### Post by jjb2011 on 2011-06-17
Well, I was following the advice of the fellow above who advised:

"When you know which partition your Linux Mint is, right click that partition and select "Delete", then go Edit > Apply all Operations. Before you can delete it, you may have to Unmount th Mint partition."

So I did that and then it asked me to delete another but I couldn't unmount it. My head hurts. I'm just going to waste the space with all those extra partitions. I still have 800GB.

As for my Ubuntu-wasted computer at home, Windows 7 still works on wi-fi and I'll just let the space I allocated to Ubuntu (200GB) sit there since it can't connect to wi-fi. I bought a USB adapter but everything I read said it's real hit or miss. That seems to be a theme. 

Thanks again for all the help. Ubuntu is working great besides Win 7 on my office computer so I can show people what it can do - and warn them it is not for the faint of heart! Or, at least, the faint of heart reliant on a wireless connection!

---

### Post by nzjethro on 2011-06-17
> **jjb2011 said:**
> Well, I was following the advice of the fellow above who advised:

"When you know which partition your Linux Mint is, right click that partition and select "Delete", then go Edit > Apply all Operations. Before you can delete it, you may have to Unmount th Mint partition."


Ah, apologies. I've only never had to unmount partitions from within extended partitions before, hence I didn't  know that problem would arise. Glad to hear you (sort of) got it working though.

---

