---
title: "Dual Boot Solution"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-02-28
Hi all. Just wanted to post this in case it can help out anyone else who has had the misfortune of installing Ubuntu on their machine, dual booting with an already loaded Windows whatever, only to be faced with a grub error or just plain can´t find the correct boot partition. I spent hours on this and found a simple solution, or should I say, Herman did.

[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

This is the bomb. If you are locked out, this disk will let you boot from it and take care of all (most) of your dual booting problems.

Just a tip, when you are installing Ubuntu alongside a Windows installation, don´t write your linux info to the Windows MBR (master boot record residing on the first part of disk 1 with the Windows installation). This can be a nightmare ride, as I have found! I wonder why the option to do this is there in the first place. I´m sure wiser heads than mine might have the answers but for me, this is what worked.

I was faced with grub error 17 and really couldn´t lose the windows setup (for uni which is about to start and dumping that would take me half a day to set up again, and never quite the same, if you know what I mean!). I hunted and tweaked and twiddled for about 4 hours (again), and then stumbled across ´Herman´s Super Grub Disk´. I made a CD from the ISO, booted from it, gave me some options and I figured out what was right for my situation from their excellent documentation page (it will fix most boot problems with varying configurations). Within seconds, it was informing me it had succeeded in fixing the grub boot loader and I should reboot!

Na, this is not right. But sure enough, on restart, I was looking at the familiar grub list with all my OS´s ready to go. They all booted fine and life was beautiful once more!!!

Hats off to Herman and if this is old knowledge, then forgive me for reiterating, I just had to tell someone! If I´d have found this elegant little piece of software (there is even a usb dongle version) about two months ago, which is how long I have been working on getting my laptop and desktop dual booting with Windows vista and xp respectively and Ubuntu Studio, it would have made my life a lot easier. Here´s hoping it makes yours´ a little easier, too. :)

---

### Post by Herman on 2008-03-01
:) Hello Bucky Ball,
I'm glad you like Super Grub DIsk, but adrian15 is the developer of Super Grub DIsk, so he deserves all the credit, not me. I just use it a lot to try to help people and I wrote a web page about it.

It's a good idea in most instances to upgrade your MBR to GRUB, because GRUB is the world's greatest boot loader and boot manager, as long as the computer you want to use it in is suitable. Not everyone knows how to use GRUB yet, that's the main problem with GRUB.
In 99.9 % of installations, GRUB installs to MBR and automatically configures itself correctly to give a trouble-free dual or multi boot set-up.
It's a good idea to plan ahead and have a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") before starting to install a dual boot or multiple boot to be ready just in case things do turn out a little other than expected.


Super Grub DIsk is good because very often the problems with GRUB happen at installation time which means new users who haven't had time to learn about GRUB yet are faced with not only a GRUB problem, but also with a command line interface they're not at all prepared for. With Super Grub Disk anyone can still boot, it's menu based so you don't have to know any grub commands.
Experienced users can solve almost any booting problem very easily with GRUB, especially when we have had time to learn how to use  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
GRUB is actually a small operating system in it's own right and it's the only  boot loader that has a command line interface to help you boot in all kinds of circumstances.
In some instances GRUB's command line interface isn't available either, and Super Grub DIsk also provides one, just press your 'c' key from a menu. 
For this reason even GRUB experts who do know all about how to use GRUB from the command line may find it handy to have a copy of Super Grub DIsk in their tool collection.

I recommend installing GRUB to MBR when you install Ubuntu in most standard PC computers. 
If you're not sure, you can make a backup of the original MBR with the Ubuntu Live CD beforehand, here's how, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

The MBR is not part of the Windows file system and it isn't even in the Windows partition. The boot sector is often confused with the MBR, and the boot sector is the first sector of the Windows partition. Neither GRUB nor Ubuntu will touch your Windows boot sector unless you force them to, so installing a dual boot set-up with GRUB is quite safe. Even if your system doesn't boot, you won't lose any data, and almost all booting problems are easily fixed, just ask here in Ubuntu Web Forums for help. You won't need to re-install any operating systems. Super Grub Disk will help you boot until your new GRUB can be fixed.

Anyhow, thanks for your happy post there, Bucky Ball, and good luck to you. I'm glad you're enjoying Ubuntu. Just a couple of little points I wanted to make, you'll come to understand later on I think probably.
Hey, did you find [screencasts.ubuntu.com]("http://screencasts.ubuntu.com/") yet? There are some excellent videos you can download in which you'll learn how to do all kinds of things in Ubuntu. Even experienced Ubuntu enthusiasts can pick up a lot of neat tricks and tips from watching these great videos. I know I'm certainly learning a few things! Everyone should watch them, especially if you're new to Ubuntu.

Regards, Herman :)

---

### Post by himagain on 2008-03-01
Hi people, especially Bucky & Herman, 
Wow! This should be a "sticky" and part of Ubuntu's offerings!
If ONLY I had found out about it earlier!

Anyway, now *I* know and everyone else NEEDS to too!

Thanks people!
"We who are about to try, salute you".[I] (Often mistaken as a Roman Gladiator saying, but actually by Newbies trying to fight THAT Ogre and persevering with trashed Lux install after trashed install) 
[/I]

---

