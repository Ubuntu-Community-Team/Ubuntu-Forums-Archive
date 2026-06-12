---
title: "installation help ASAP"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Agent66 on 2005-11-13
To say that I am happy with this OS or even Linux would be quite a feat. I wanted to try this up and coming OS and so far, I'm tempted to tell people to continue to use WIndows.

My problem - after extensive tries, I finally got ubuntu breezy badger installed on my second hard drive. When the installation completed, it went to the grub loader or whatever, asking if I wanted to use several versions of ubuntu or if I wanted to load XP. I guess I wasn't fast enough, cuase it automatically went into the first one highlighted. However, at the load screen, it completely froze.

This is where my problems began or perhaps they started with the silly notion of using this particular OS.

So I decided I had no choice but to restart. The first time, not only did my computer freeze at the BIOS or rather the POST screen, but it will now no longer load windows XP. In fact, several times I have gotten the grub error 21. Even when I try to fix this horrible mistake, XP won't even boot from not only a copied CD, which was used to install it the last time, but even a Microsoft enterprise edition of XP that I received from school. It freezes after catching on the cd. In fact, but my computer is currently frozen with a black screen, causing me to seek answers on my roommate's very backwards Porteguesse laptop (no offense to anyone from Portegual, honest!)

I'm at the point of either completing erasing everything on my master drive - which defeats the purpose of wanting ubuntu on a second drive - or taking out both hard drives and taking them over to a friend's to be diagnosed. To say that I'm highly frustrated is an understatement. The reason I picked this particular distribution of Linux was because how simple it seemed and how easy the install went. And now look.

In a nut shell, I can no longer get into windows XP either by normal boot or booting from a CD. The only thing I can do with Linux is boot from a CD, it still doesn't erase the grub thing that is now on my master drive. At this point, I wish I had never entertained the idea of using linux.

This is kinda desperate situation. I no lkonger have a desktop computer and I'd rather not rely on my roommate's nor do I want to travel all the way to work just to start on my homework. The purpose of using the second drive was so I can try out linux, while still keeping XP, now it looks like I've totally f@!$ed up my drives.

I'd like to get some feed back in the next three hours - yeah I know, but I do have things to do - any help. thanks:confused:

---

### Post by Herman on 2005-11-13
Agent66!
               Sorry to hear of your unfortunate circumstances, but there are quite a few things you can try to get the situation under control. If you are mainly concerned with bootinf Windows to begin with, you could try a GAG CD. That's about the quickest for most people, it works for me and no-one who I have given that advice to so far has provided any negative feedback about it so far. If it doesn't work for you, please let me know.:D    GAG won't boot Ubuntu though, until you install a boot loader to your Ubuntu partition, but you can make a decision about that later.
Instructions for how to make a GAG floppy are in the 'Boot Loader Help' page which you will find if you click on my signature link, below.
Secondly, regardless if whether that works or not, try checking out some of the install instructions there too, and when you have time, you might be able to put Ubuntu in again better next time. It sounds like maybe you'll need to erase all you previous attemps and install over the top maybe, I'm not sure exactly what it looks like. Maybe let us see you partition table when you get to 'manual partitioning', if you like, and we can advise you. (Herman).

---

### Post by BreezyCricket on 2005-11-14
Hi 66:

Sorry to be the 'bearer of sad tidings', but I think that when it comes to Operating Systems, Linux will only ever be an 'Also Ran'.

If you are having trouble installing linux, just wait till you try installing add-on programs.

As for myself, with this Distro, I have not even been able to burn an 'error free' CD to install with, so I think I will just give it a miss.

---

### Post by linbetwin on 2005-11-14
[quote=BreezyCricket]Hi 66:
 
Sorry to be the 'bearer of sad tidings', but I think that when it comes to Operating Systems, Linux will only ever be an 'Also Ran'.
 
If you are having trouble installing linux, just wait till you try installing add-on programs.
 
As for myself, with this Distro, I have not even been able to burn an 'error free' CD to install with, so I think I will just give it a miss.[/quote]
 
And is Ubuntu, or Linux in general, to blame because you haven't been able to burn an error free CD?

---

### Post by BreezyCricket on 2005-11-14
Ubuntu is the only one that I have had any trouble with.

---

### Post by yesplease on 2005-11-14
@agent66: did you restore the boot order in the bios? 

Perhaps it helps to unplug your second disk so the faulty install does not interfere with repairing the windows mbr on the first hard disk.

---

### Post by adrianhensler on 2005-11-14
You could also try a fdisk /mbr (use a Windows bootable install CD to get to the recovery screen; if you don't know how to do this a quick goolgle ( [http://support.microsoft.com/?kbid=307654](http://support.microsoft.com/?kbid=307654) ) until you find a quide that describes the process in a manner appropriate to your skill level. You may also need the FIXBOOT command with fdisk; it's been awile since I did this.

This will get rid of the grub bootloader and allow Windows to boot assuming that is what you are looking to do.

I would bet that the issue is with the grub installation; see if editing the grub boot commands for either Windows or Linux help; I had to delete the first lines (looked something like "hd(0),0" (from memory; I had to delete them and didn't save them) to get things booting properly.

I'm not a grub expert; so maybe someone else can help check to see if your grub entires are okay.

Good luck, I'd like to suggest sticking with it a bit longer; in my opinion the rewards are worth it.

Adrian

---

### Post by AgentZ86 on 2005-11-24
Hi all,

Just FYI chances are that those who are having linux problems and want to try to tap into the power of linux. I would suspect that they are also having windows problems as well.

I've been in myown computer sales and service business and most of the problems I have to fix are windows problems at $55 per hour or I won't even look at it.

Anyhow having said that there is no such thing as a perfect OS, however I've had better success with my Linux Box then my Windows box, but keeping in mind it's also a learning curve in which you may not be prepared for.

New users coming from windows think they will simply put in a disk install and their on their way and all the installation processes and terminology that they have learned is very diffucult to unlearn. The best start in Linux is to forget that you know anything, force yourself to admit you nothing about computer hardware or software at all.

Then start over and start your learning process. Sure you can install and tinker with your computer, but I would not recommend using the same hard drive that you plan to use for productivity work or getting things done until you are more comfortable with the processes.

Understand how to setup your partitions for linux and why, understand what happens when installing and why, then this would be a better argument to say hey I did everything right and the result was not what I wanted.

But to burn a CD using Windows Nero and then bootup and expect everything perfectly and attempting to dual boot your machine on the first go, you had better be prepared to foul things up a bit before you get started. Such as backing up your data and forgetting windows for now just install on a fresh hard drive and get familiar with the process first.
Also this will let you know if your CD is reading the burned CD properly, and the the initial install on your hardware will work correctly.

Then start thinking about Dual boot or otherwise.
You could even install a cheap 4-6 gig hard drive just for practice etc.

My customers incidentally have the very same problem with windows they try to upgrade or install the latest windows or download even updates and things and hosed their system. Everything gone, paritions gone, people do the craziest things. They even erase windows folders to make room for more music files etc. and then blame the computer. Not the user, not the OS the computer.

Anyhow sorry for your troubles but I've had similar problems in the past before I knew what I was doing and now have 4 primary partitions nad 1 extended partitions and 3 logical partitions and can dual,triple,quadriple,quintuple boot etc. and all OS's seem to be working in harmony including winblow xp home edition for my game only unfortunately, but still working.

I know this is not very helpful really but perhaps can give new perspective on installing Ubuntu, or any other linux for that matter, as it is well worth it.
:) 
FYI my wife knows nothing about computers and she uses my linux box to sell on ebay everyday and browse write letters etc. printing and printing shipping labels and other things watching excersize vids etc.

Anyhow it's fun you will love it in time as many other do, be patient and get to the bottom of this subject so you can get on with enjoying your new Ubuntu OS

---

