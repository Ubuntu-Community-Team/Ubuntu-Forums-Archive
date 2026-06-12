---
title: "SH: Grub&gt; at boot when installed through XP"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by ChadSH on 2010-02-19
Hi, I am extremely new at using linux OSs, I have only booted to a live CD a couple of times, and don't know the first linux command. I just recieved my CompTia A+ Certifiation, and I'm Taking My Net+ exam Monday morning. I have extensive experience with all Windows OSs. Here is my problem: I installed a new HD in an old HP machine that has a 650MHz processor, and 448 MB of Ram. The HD is a WD 160G Caviar Blue 7200rpm. I formated the drive NTFS with WD datalifegaurd tools, then partitioned it into two halves; 74.5 G each I believe. The plan was to install Windows XP, and then Install Ubuntu next to it (on same partition), so that I could use the second partition for storage. I successfully installed Xp SP3 with all critical/recommended updates, defragged the drive, and then tried to install Ubuntu 9.10 from the Live CD - Has been MD5 verified, and CD checked. When I tried to install it by booting the cd, I got an error permission denied. I then tried to boot into XP, and do the install from the CD as it opened up in Windows. Still got the permission denied error at or towards the end of the install. I then dsownloaded the wubi installer, let it download a new iso and run overnight. as far as I know, this was successful, because I now have the Option to boot from 1 - Windows, 2 - Ubuntu. Here is where I am very confused, and stuck. When I try to boot into Ubuntu, I get this: SH: Grub> or something very very close to that at boot. I have no clue what to do at this point, so I have to control alt delete, and the go back into Windows. Any help would be greatly appreciated. This PC is for my 11 year old son, and he wants ubuntu, and I am very interested in learning the commands myself. Just don't have time to play with it much now because of school, and studying for my certs. Does anyone know what I need to do, so that it will just boot into the Ubuntu GUI from here? Also, a good link to some starter linux commands would be nice! would like to know how to do commmand line commands to format, error check, defrag, etc. Thanks alot in advance! Chad
 
after clicking Ubuntu at boot screen this is what I get:
 
GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions. ]
 
sh:grub> _

---

### Post by kansasnoob on 2010-02-20
The fix is described here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by ChadSH on 2010-02-20
That fix didn't work, still trying to find.  Thanks for the quick reply though!

---

### Post by kansasnoob on 2010-02-20
Thought I'd give this a bump to see if another pair of eyes might see something I didn't :)

---

### Post by ChadSH on 2010-02-22
Ya, I couldn't find a fix, and I'm not familiar with ubuntu commands, so I have to keep XP.  Too bad, I liked the look and feel of ubuntu.  Seems way Buggy!  I don't have time for it.  I now see why it is free.  :(

---

### Post by meierfra. on 2010-02-22
> 448 MB of Ram

That's a little low for Ubuntu 9.10. You might give Xubuntu a try. Don't waste your time on Wubi. If a  regular install does not work, I can almost guarantee you that a  Wubi install won't work either.


> I don't have time for it. 
Give Xubuntu a try, it won't take that long.

---

### Post by Linuxneophyte on 2010-09-21
Unfortunately my friend it is not the Ubuntu that is the Problem. MS Viruses do not play well with others. Don't sell the "FREE" O.S. down the river, when it is actually a problem with the way MS controls the systems.

---

