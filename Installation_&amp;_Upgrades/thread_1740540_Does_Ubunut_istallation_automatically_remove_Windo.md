---
title: "Does Ubunut istallation automatically remove Windows?"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by litreblitreb on 2011-04-27
Hi there,

I think this is a very simple question for most people out there, but I have not found a clear answer with a normal search:

I have decided to get completely rid of my probelm-ridden windows xp on my laptop and use ubuntu. If I do a normal Ubuntu installation, will that also completely remove Windows and any problems it might have?

Background: My computer have caught a Trojan horse and will not boot. Rather than trying to repair Windows I thought this is a good occasion for my conversion to linux user. Can I just make an Ubuntu CD / USB stick, boot from that and hereby remove Windows and install Ubuntu? Or do I first need to get rid of Windows? (And how if so)?

I plan on doing the installation tomorrow when Ubuntu 11.04 will be released. I look forward to becoming a part of the Ubuntu community.

And yes, I have back up of all documents on my computer, so I am ready for a fresh start!

Thanks for any help and recommendations!

---

### Post by leeman101 on 2011-04-27
The easiest way for most people is to create an .iso image on a cd.  its a pretty simple task. You can install Ubuntu either next to Windows on your hard drive on a separate partition, or you can install ubuntu using the entire disk, therefore overwriting windows and gettign rid of it.  It's up to you.  A windows virus won't affect ubuntu, if you would like to keep windows for now.  Ubuntu has step-by-step instructions to guide you through the installation process.  it is not as intimidating as it used to be. it's very easy.  You don't even have to partition manually anymore, unless you want to.  

Since you can't boot into Windows anymore, and if you want to erase it, then just go for the Ubuntu install, and it will take care of everything for you.

---

### Post by EthioJOB on 2011-04-27
In a word, yes. Just take the whole hard disk drive and install Ubuntu on it, and any prior installations would be history.

In fact, making a complete installation of Ubuntu is the easier way of installing as you wouldn't have to worry about partitioning and stuff, though its not that difficult. I see that you want to make a complete shift. I'd say go for it, so long as you're sure that you don't want to go back to windows ever again.

You can also install Ubuntu alongside windows if you like, in which case you'll have to partition the hard disk. Anyway, its your choice and based on your question, my answer is you're good to go.

---

### Post by Bucky Ball on 2011-04-27
To the OP; Welcome! :)

Only problem with the approach suggested? Ubuntu will make one big partition on the whole drive. I personally would boot from the LiveCD (the ISO of Ubuntu you have burnt to a disk), choose 'Try Ubuntu' without installing to hard drive and get to a desktop. Then:

System>Administration>Gparted.

Kill the Windows! Just delete the partitions. You are running of the CD so all good.

Then restart and this time choose to install Ubuntu. When you get to partitioning section, choose manual, then a setup something like this:

/ = root partition; where the Ubuntu OS lives, 20Gb is plenty.
/home = where your personal data and settings live; as big as you like leaving enough room for;
/swap = your swap partition, size of your RAM should be fine depending on how much you have or if you fancy hibernating (in which case twice the size although that idea could be outdated).

This way, if you screw your Ubuntu install (by accident or otherwise) it is easy to reinstall the OS (on / partition) and you won't lose any REALLY valuable information as that will still be safely in your /home partition. ;) You just re-create / and leave the others as is (don't format during install and partitioning; it will use the existing /home and /swap).

My two cents, something to contemplate, and hope it is of some help. ;)

---

