---
title: "Could I do this with Ubuntu?"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by eBopBob on 2005-01-30
Hey folks,

Ok - I've a relatively new computer. Its basic specs are:

Intel Pentium 4
3.2GHz Processor with HT
250GB SATA Hard Drive
1024MB DDR RAM
nVidia 6600 PCI Express Graphics Card
DVD-Rom
DVD+-RW
Windows XP Home
Mouse/Keyboard/Monitor
6xUSB/2xFirewire/Mic/Earphones
Flash/Smartmedia/SD/MMC
And lots of other things...


My hard drive is currently split into three partitions:
C: 117GB
D: 112GB
E: 2.5GB

The E: drive is full up - It's basically a recover drive which allows me to restore XP back to factory settings. D: is a backup drive which allows me to store things there, and when I restore the system the items placed there won't be deleted. And the C: is the general C: drive where anything goes.

Now - I've only used 10GB of C: and 1GB of D: - So I've plenty of space left for Linux (and then some!).

This is what I'd idealy like:

C: 67GB (*Windows*)
D: 60GB (*Windows*)
E: 2.5GB (*Windows*)
SWAP: 2GB
Linux (1): 50GB (*This would be Ubuntu Linux*)
Linux (2): 50GB (*Flavour of the month Linux*)


So I'd still have my three Windows partitions. However I'd also have a SWAP partition (*It's 2GB because I've always been told it should be double the amount of RAM you have - And anyway, it won't make that much difference*), and two Linux partitions - One for my everyday Linux use and one for "flavour of the month" so to speak; where I can just in general test out other Linux distros and so on and just mess about.

However... now it comes to editing the current partitions and creating the three new partitions so in total I've six. I tried to do this with SuSE 9.1 Pro, however it could not do it with Windows XP Home. Oh well. Then I tried Fedora and it wouldn't allow me to change their sizes; it'd only allow me to change their format (eg: EX3, etc.). Then I tried Ubuntu - and well, I got scared. :P
It said before I can edit the partitions I must save this or that to the disk and I freaked out.

So basically - I'm asking for help.
Would this be possible to do with Ubuntu? If so, is it relatively easy? (Basically is it clear - I'm under no impression this will be easy, however what I'm hoping (*although somewhat doubting*) is that it'll be clearly explained).

And also, is this a good setup?
I was thinking of having three Linux partitions however in the end decided that two would be fine - As otherwise it'd have to be 40gb, 30gb and 30gb.

So, can anyone help?

Thanks :)

---

### Post by JohnQ on 2005-01-30
You might want other advice before you listen to me, but it works...

I was able to resize my NTFS partition on my laptop using Ubuntu's partitioner but it's still nerve racking.  Before you resize ( and have to resize each partition C: D: E:  and put Linux between them otherwise you'll what's on those partitions (unless you back up your restore data and person things on DVDs))  you need to run defrag on all partitions and then go into Windows system settings and disable Windows System Restore.  
Then go into Ubuntu installer and enter into the menu for the first partition.  You'll next select the size 117GB and then type in the smaller amount.  This resizes that partition.

Defrag moves all of the scattered data back to the front of the partition (so resize doesn't delete any) and disabling System Restore also makes sure there is nothing at the end of partitions.

I definitely recommend that you use three Linux partitions.  Two for Ubuntu's root and some other distro's root, and the third for /home to be shared by both.  That way no matter which distro you boot you'll always have your data/personalizations.

Best of luck.  And since you have a DVD burner, before you do anything to alter the partitions, you might want to make backups.

John

---

### Post by bitfoo on 2005-01-30
I would agree with three linux partitions if you are going to keep switching the flavor of the month. So basically you would need 4.  Easiest thing to do would be to resize one of the windows partitions with enough space for all the linuxes, and install it in there. Powerquest partition magic will do it in windows and qtparted should be fine in linux. Sound like you may have already tried with qtparted, so give Powerquest's Partition Magic a go, and then put in that Linux cd. :)

---

### Post by eBopBob on 2005-02-02
> Before you resize ( and have to resize each partition C: D: E: and put Linux between them otherwise you'll what's on those partitions (unless you back up your restore data and person things on DVDs)) you need to run defragment on all partitions and then go into Windows system settings and disable Windows System Restore.
Ok - How should I defragment it though? When I defragmented my laptop to put Linux on (*Then it was SuSE*) I was told to uncheck certain options to make it go quicker. I now have a much faster system though - Should I again have it as a "minimum" defragmentation, or should I just have it as standard?


> I definitely recommend that you use three Linux partitions. Two for Ubuntu's root and some other distro's root, and the third for /home to be shared by both. That way no matter which distro you boot you'll always have your data/personalizations.
Ok - This I'll need help on though. So this basically means that I'll be able to access all my general documents and files from Ubuntu and "flavour of the month"? I'm very worried about doing this, as I'm not sure how well it'll go. And what about when I want to change flavour of the month - will it then be very complicated or just as easy as selecting which partition to install it onto?
I'll definitely think about this; however am not sure about it - Not really sure if I can do it, and what complications it'll have in the future.


> And since you have a DVD burner, before you do anything to alter the partitions, you might want to make backups.
Yeah - I am planning to go and buy a blank DVD-RW (*Boy it costs soo much though! &#8364;5.00 just for one!*) and then I'll backup everything I have on my computer - although it isn't much. It's just best to have a backup before I go into it rather than trying it with no backups.


> Best of luck.
Thanks! I'll definitely need it.


> I would agree with three Linux partitions if you are going to keep switching the flavor of the month. So basically you would need 4.
I would basically need four what? Four partitions? - Don't forget I'll be keeping Windows, which is three, and then swap, and then if I do have three it'll make a total of seven.


> Powerquest partition magic will do it in windows and qtparted should be fine in Linux. Sound like you may have already tried with qtparted, so give Powerquest's Partition Magic a go,
I'm going to try and get Partition Magic from a friend and try to partition it that way; however if I cannot get it from a friend I'll give Ubuntu's installer a go - That may actually help me for the future when using Linux though (*If I were to use Ubuntu's installer*), but I'll see what happens.
Also, how have I tried qtparted? - Which distro uses it?



Also, a question I forgot to ask. The current available version of Ubuntu is 4.10 - Should I use this, or wait until April I think it is for Hoary? I only have a 56k Internet connection; meaning it is very slow to update and download large files. I may received ADSL via satellite soon however I'm not entirely sure when that'll be; and that's even if I get it.

---

### Post by eBopBob on 2005-02-03
Anyone?

---

### Post by eBopBob on 2005-02-04
> Ok - How should I defragment it though? When I defragmented my laptop to put Linux on (Then it was SuSE) I was told to uncheck certain options to make it go quicker. I now have a much faster system though - Should I again have it as a "minimum" defragmentation, or should I just have it as standard?

> Also, a question I forgot to ask. The current available version of Ubuntu is 4.10 - Should I use this, or wait until April I think it is for Hoary? I only have a 56k Internet connection; meaning it is very slow to update and download large files. I may received ADSL via satellite soon however I'm not entirely sure when that'll be; and that's even if I get it.

Anyone?

---

### Post by dikki on 2005-02-04
You should choose full defrag. You need every data to be at the start of the partition.

Powerquest's (by now, Symantec's) Partition Magic can do everything for you. Partition resize, data movement, everything.

The Warty or Hoary question is what I can't answer exactly; if you would like a stable environment, choose Warty. I installed it, too. And you can still upgrade if you feel yourself brave enough. If you would like to learn Linux, and you feel yourself able to solve problems, that can occur using Hoary, then take Hoary. 

For a first system, I'd take Warty, and when everything works, dist-upgrade to Hoary.

---

### Post by brousch on 2005-02-04
That is quite the ambitious setup!

Since you have just dropped a bundle on such a nice system, have you considered simply buying a second hard disk just for Linux? That way you don't have to mess around with resizing NTFS or worry about destroying data on your existing hard disk.

I see a 120GB SATA on Pricewatch for only $74 ...

My motto is always KISS.

---

