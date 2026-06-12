---
title: "Partitioning"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by stefan.416 on 2007-06-21
hey everyone im making a dual boot Ubuntu - Windows XP system with Ubuntu being the primary boot. i have two 80GB hard drives and im wondering what would be the best way to partition them and the best size partitions to use. thanks

---

### Post by stamateviorel on 2007-06-21
oohhh you cand use fdisk :D

---

### Post by stefan.416 on 2007-06-21
im askin what size should i make the partitions.

---

### Post by Herman on 2007-06-21
Hello stefan.416,

I would think a good way would be to install Windows first on the first hard disk and then Ubuntu. I would leave the second hard disk for data and backups, including a partimage copy of both operating systems once they are fully set up and all the software is installed.
It all depends on you and how you are planning on using your computer. My wife and I are used to Ubuntu now and we hardy use Windows XP at all anymore. It's so weak and vulnerable to viruses and all kinds of malware. [Security Report: Windows vs Linux | The Register]("http://www.theregister.co.uk/security/security_report_windows_vs_linux/") We have 80.0 GB hard disks and we have Windows on about 10.0 GB and Ubuntu on 69.0 GB with 1.0 GB swap area. 
Someone who is new to Ubuntu and not sure if they will like it or not yet, (because they aren't used to it yet maybe), might install the exact opposite way, 70.0 for Windows and 9.0 for Ubuntu with a 1.0 GB swap area.

It doesn't matter so much these days how big or small you make your partitions, you can always resize them whenever you want with a [GParted -- LiveCD.]("http://gparted.sourceforge.net/")

On the second hard disk you might make one or more data partitions. Ubuntu can read and write to NTFS pretty well nowadays but most people prefer to have a FAT32 partition so either operating system can read and write to it. 

It doesn't really matter too much how you make your partitions as long as you install Ubuntu and have fun. :D
Oh, well there are [Partitioning Rules]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Partitioning_Rules"). 

If you want to have Windows on one hard drive and Ubuntu on the other, here is a link to confused57's excellent how-to on that, [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902") . That's another good way to do things, it really doesn't matter which way you set things up, there are lots of ways that are good.

Here's the link for aysiu's site too, he has a nice page on partitioning, be sure to look for that there, [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Regards, Herman  :D

---

### Post by theproject on 2007-06-21
I do not get this at all.....i have windows vista, 120gb harddrive, how can i tell if its dual? I want linux, i dont care if its my only OS i dont really want to duel boot. Im willing to try something new, want to attach beryl to it and all that, BUT i cant figure out how to install it on my computer, doesnt work. The "live" cd that i "made" didnt work, i left it "starting up" on the same screen for two hours. I just dont understand any of this. I need to learn how to get it on my computer.

---

### Post by Herman on 2007-06-21
Hello theproject,
Okay, first, what kind of computer do you have? Doe it have an 'i386' processor or 'dual core'?  You can use the i386 install CD for either, but the dual core install CD, 'AMD64', I think will only work if your computer is dual core.

Or it could be that you have some other special hardware that the Ubuntu CD needs to be specially adjusted for at boot time. Rarely, but possible, you could even have some special hardware that Ubuntu doesn't support quite yet. Are you using the latest Ubuntu CD? Or an older version of Ubuntu?

Have you tried booting the CD in another computer to see if it's just your computer or the CD that might be the problem?  My wife and I have two identical computers and one time I had a lot of trouble with hers. I couldn't install anything. It would play all kinds of CDs and DVDs with music or movies just fine but when we tried to use any software CDs or DVDs it used to act up something terrible.  I fixed the problem by  cleaning her DVD drive, [Computer Cleaning Guide - Clean Computer]("http://www.computercleaningguide.com/"), but that didn't work so I did this, [Cleaning your DVD drive]("http://www.llamma.com/xbox/Repairs/cleaning_your_dvd_drive.htm") and that worked, now my wife's computer has two versions of Ubuntu installed.  However, I don't mean to imply that your computer could have the same problem. I just wanted to illustrate that the problem could be anything.

Maybe if you can provide a little more info I or someone else here can help you or maybe not, but it's worth a try. :D
How old or new is your computer? What kind of monitor have you got, (widescreen or standard?), what kind of video card (graphics card) does it have? Things like that if you can find out, could be the clue that someone might need to know if they want to help you. 
Regards, Herman :D

---

