---
title: "Dual booting &amp; beginner advice"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by sabatier on 2007-09-18
Hi everyone, I'm completely new to Linux and Ubuntu but I've decided to install Ubuntu on my desktop. I'd appreciate some good advice before I take the big step and I've heard you're a decent crowd here at Ubuntu forums! Before I make the move I want to be clear in my head about what exactly I'm doing to minimize any problems that may occur after installation. After reading the posts in this forum, there appears to be many!

So here's my pc setup:
Dell Dimension 9150 Desktop
Hard drive 150 GB
OS: Windows XP

I want to dual boot Ubuntu and Windows XP. 

1) How feasible is dual booting? Sure, it works, but does it affect the performance of either operating system?

2) Partitioning - What's the best way to do it? Which tool did you use and can you vouch for its effectiveness?
    Should I install Windows on the entire disk first and then resize it in windows or what? How much space should
    be allocated to Windows?

3) Which should I install first, Windows or Ubuntu? I'll be reinstalling Windows anyway so the order doesn't matter
    to me.

4) How much space should be allocated to Windows? How many partitions for Ubuntu? I like the idea of having
a separate partition for /home in Ubuntu.

5) While you're using Ubuntu, is it possible to browse the files in your Windows installation or must you boot up
    Windows to do that?

I will probably still use Windows because unfortunately my degree is based almost entirely on Microsoft Excel and
Access. I'm not completely comfortable with switching to OpenOffice.org just yet, particularly as I'm about to start
my final year project and I need to be sure of the software I'm using!

You don't need to answer all these questions, any help will be greatly appreciated. I just want to make the
installation as smooth as possible. I don't want to be coming back to you with booting problems / OS shutting
down etc etc etc! Opinions please regarding your setup and experiences with Ubuntu/XP.

Regards,

Ruth

---

### Post by Herman on 2007-09-18
>  1) How feasible is dual booting? Sure, it works, but does it affect the performance of either operating system?
 Windows will start performing better when it detects the presence of Ubuntu and gets scared it will soon be deleted if it doesn't clean up its act.
No, not exactly like that, seriously, Ubuntu isn't vulnerable to most of the problems like viruses and malware threats that plague Windows on the internet. If you dual boot Windows with Ubuntu you will find that once you get your Windows system clean, if you refrain from using it on the internet, it will remain clean as long as you don't use it for internet any more. That means it will work better and last longer between re-installs. In fact it will never need to be re-installed again. So you Windows maintenance will drop to zero. (As long as you use Ubuntu for receiving email and browsing the internet.) So for all other things that use use Windows for, it will be faster.
>  2) Partitioning - What's the best way to do it? Which tool did you use and can you vouch for its effectiveness?
    Should I install Windows on the entire disk first and then resize it in windows or what? How much space should
    be allocated to Windows? The Ubuntu install CDs come with their own partitioning programs built into them, those are the best for installing Ubuntu with. If you really think it will be simpler for you to pre-partition, (in some low RAM computers it can help), [GParted -- LiveCD]("http://gparted.sourceforge.net/") would be the best, but any good 'Parted based partitioner will also be good.
Yeah, install Windows in the entire disk first, then resize it smaller with Ubuntu's partitioner to make free space with room for Ubuntu to be installed.
>  3) Which should I install first, Windows or Ubuntu? I'll be reinstalling Windows anyway so the order doesn't matter to me. You'll find it simpler to install Windows first, (if you really must have Windows at all). It's okay to do it the other way, but Windows first is the easiest, because then you won't have to re-install the boot loader. But that's not very hard these days anyway.
My wife and I both prefer single partition Ubuntu installs, not with a separate /home, because we both multiple boot. Remember, Ubuntu is free and we are allowed to install as many copies of it in one computer as we want. Having single partition installs makes multi-booting simpler. I like multi booting because I like to be adventurous and try our risky ideas, so I need a spare system I can use for that. My wife likes having two Ubuntus too, because if anything goes wrong with one of them while I'm away, she just reboots into the other one and uses that until I come home and help her with her problem, (not that she doesn't teach me things too in fact it was her that got me hooked on computers to begin with, but I tend to be okay on the maintenance and repair side of things though, she's the one who actually does things that are useful with computers).
> 4) How much space should be allocated to Windows? How many partitions for Ubuntu? I like the idea of having a separate partition for /home in Ubuntu. Those are matter for personal preference and no-one but you will ever really know. It depends how many files you want to keep in either system. If you have the good old FAT32 file system in Windows you'll easily be able to read and write to your Windows files from Ubuntu, so it won't matter. If you use the NTFS file system, in Windows you can still set up Ubuntu to read and write to NTFS, but Ubuntu doesn't come like that 'out of the box'.
These days it's easy to resize your partitions with a GParted LiveCD when you need to, so don't worry about it too much. 

>  5) While you're using Ubuntu, is it possible to browse the files in your Windows installation or must you boot up Windows to do that?
 Yes, of course you can! And if your Windows install ever comes down with a virus or some other serious problem, you'll always be able to boot into Ubuntu operating system to rescue all your files. You can copy and paste too and from Windows with Ubuntu or work on them and save the changes if your Windows has the FAT32 file system, but if it has NTFS, you can only copy files from it.
>  I will probably still use Windows because unfortunately my degree is based almost entirely on Microsoft Excel and
Access. I'm not completely comfortable with switching to OpenOffice.org just yet, particularly as I'm about to start
my final year project and I need to be sure of the software I'm using! Sure, well that's okay, dual booting is kind of like having training wheels on a bicycle, eventually you won't need Windows for anything anymore when you learn to use Ubuntu, but for now you are welcome to use both for as long as you ever need to. There's no time limit and there's no obligation. Just enjoy using both operating systems for whatever you like and hopefully you'll switch to Ubuntu when you are ready. It will happen by itself gradually without you being aware of it. Some day you'll think "hey I haven't booted Windows up for a long time,... what was that password again?... darn, I've forgotten it..

>  You don't need to answer all these questions, any help will be greatly appreciated. I just want to make the
installation as smooth as possible. I don't want to be coming back to you with booting problems / OS shutting
down etc etc etc! Opinions please regarding your setup and experiences with Ubuntu/XP. Well as a precaution , you could be prepared for any booting problems in advance by getting a [Super Grub Disk]("http://geocities.com/supergrubdisk/"), those are free and only a small download. 
You are welcome to come back and ask more questions if you want to know more. There are a few good websites for getting started with Ubuntu, a really good one is aysiu's [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I have one too, but it's more about the 'Alternate' install CD, and boot loaders, you probably won't need to know any of that, but you might be referred to it if you have a problem. Refer to my sig links at the bottom of this post.
As long as you MD5sum your downloaded Ubuntu .iso file before burning it to CD, and check the CD's integrity with it's own built in utility for that, you'll be fine. Oh, and be sure to make a backup of any important files before partitioning your hard disk, everyone does that. That's very important, although we hope you won't need it.
Regards, Herman :)

---

### Post by sabatier on 2007-09-18
Hi Herman, thanks a million for your comprehensive reply. It has really cleared up a lot of things for me. I'm gonna get that Super Grub disk right away!

Regards,

Ruth

---

### Post by WernerB on 2007-09-18
I am just starting to get going with Ubuntu on an oldish Win2000 machine.

Herman thanks for such an excellent and detailed reply, it  is just the information I needed.

Werner

---

### Post by Herman on 2007-09-18
Hello WernerB :)
No problem, I'm happy it helped you. :)

When installing Ubuntu in an older machine, the amount of RAM (memory) can be something to think about. Many older machines have less than 250 MB of RAM.

What I do is just try with the Ubuntu LiveCD first and if it's very slow I give up and pre-partition the computer with a [GParted -- LiveCD]("http://gparted.sourceforge.net/") first.

If your computer has somewhat less than 250 mb of RAM, the Ubuntu LiveCD will be slower, but Linux operating systems have the ability to use a special partition in a hard disk known as a 'swap area', which works like a page file in Windows, it's like a slow lane for the slow moving items in the memory, leaving the real memory free to handle the fast processes. If needed, the Linux operating system can use its swap area more and more to make up for a lack of hardware memory in the computer.
That means if you find that the Ubuntu LiveCD runs very slowly in an older type of computer or even seems to freeze up, you can benefit from using a [GParted -- LiveCD]("http://gparted.sourceforge.net/") to do your partitioning first, and make a swap area of 1/2 or 1.0 GB somewhere on your hard disk.
The LiveCD will find that swap area automatically and make use of it, and the next time you try with the LiveCD you will notice a huge performance boost! :)

If you still have trouble, then 'Alternate' install CD will be recommended instead of the Live/InstallCD, I have installed Ubuntu in computers with as little as 128 mb of installed RAM, with the 'Alternate' CD.  Fluxbuntu or Xubuntu would be worth considering for low RAM machines. 
But for most computers, the Live/Install CDs work the best. If you have RAM somewhere in the higher range between 250 to 512 MB area you won't have to do anything, the Ubuntu LiveCD will run well and install Ubuntu just fine. 
The cutoff area is vague because it depends on a few other details about your computer like the amount of CPU cache memory you have and other things too. In some modestly specced or older computers with less than 256 mb or RAM the Ubuntu Live/install CD will still work well without doing anything at all.

Anyway, just try it first and probably it'll work okay, if it doesn't then read this post again and try the pre-partitioning with GParted LiveCD trick, so you'll already have that swap area. :)

The GParted LiveCD is a special fast trimmed down LiveCD made just for this type of work and it uses a lightweight desktop, whereas the Ubuntu CD has many purposes. Other uses include rescue work and importantly, showing off some of the nice features of Ubuntu, which is why it needs average or better RAM.
Good luck and happy Ubuntuing,
Regards, Herman :)

---

### Post by Pumalite on 2007-09-18
Great Herman! Hey mods; you should make this a 'Sticky'

---

