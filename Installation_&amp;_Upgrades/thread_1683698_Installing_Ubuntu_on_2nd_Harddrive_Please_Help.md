---
title: "Installing Ubuntu on 2nd Harddrive Please Help"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by frank1e on 2011-02-07
Ok if theres en easy post that handles this please re-direct me I could not find it.  I will break down my setup / problem real simple.

1st Harddrive has Windows 7 installed.
2nd Harddrive is blank.

I want to install Ubuntu onto the 2nd Harddrive.  Without a CD or USB.  How do I do this? First I trie re-partitioning the 2nd hd with a linux ext3 partition and ran Unettbootin but for some reason the only way it shows my 2nd HD is under USB drives instead of harddrives. I installed it and it didnt work. For some reason it installed it with an ntfs partition and it couldnt boot.

Please help. Point me in the right direciton here guys, I know this would probaby be much easier with a CD but I dont have one and I just want to get this done. I know you know the way help a linux noob out cause I cant go without Ubuntu any longer!

---

### Post by frank1e on 2011-02-07
Ok if theres a better place for this please re-direct me.

I have 2 harddrives. First HD has Win 7. 2nd HD is blank. I have downloaded the Ubuntu 10.04 ISO. I am trying to install Ububntu onto the blank 2nd HD using Unetbootin because I do not know any other way and I am trying to do this without using a CD or USB.  Please help me.

Unetbootin doesnt seem to be working. Whether I partition the 2nd hd as NTFS or ext3 either way Unetbootin doesnt recognize it as a harddrive only as a USB drive for some reaosn. And it is an IDE harddrive slave.  Please any help greatly appreciated cannot go without Ubuntu any longer.  I want it installed on the 2nd HD so that if I want when I boot up I can choose boot option and just boot of the 2nd HD or even dual boot. Also hopefully the way it installs I will be able to take the 2nd HD out and use it as a primary in another computer and it boot straight to Ubunntu but if it doesnt work that way its not so important.

I basically just need someone to teach me how to install Ubuntu from harddrive. Is there a way to mount the ubuntu iso with like clone drive and do it this way? I believe I tried but when I do the autorun never works and all I can do is explore the iso as opposed to it running like an Ubuntu install cd.  Thanks for any help!

---

### Post by ugm6hr on 2011-02-08
Do you have a spare 1GB+ USB drive you could use?
If so - use usb-creator to sreate a LiveUSB, then just use that.
NB: You will have to use manual installation option to select the location of the Ubuntu boot files (grub2) when installing, to allow the 2 HDs to work independently.

---

### Post by oldfred on 2011-02-08
Much better to partition in advance:

Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Installs:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

