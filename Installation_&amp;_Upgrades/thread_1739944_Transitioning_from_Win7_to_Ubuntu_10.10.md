---
title: "Transitioning from Win7 to Ubuntu 10.10"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by boomcat on 2011-04-26
Last week I bought an HP desktop with an AMD-64 processor and a terabyte drive. Win7 was already installed. I installed Ubuntu 10.10 (the 64-bit flavor) as a dual-boot system and that seems to work fine. Then I installed Oracle's VirtualBox, plus extensions and Guest Additions to run within Ubuntu. And within THAT I have installed Win XP. This seems to work very well.

What I'd like to do is have a machine that boots into Ubuntu and to have my three Windows OS's (Win 2K, Win XP and Win7) available under VirtualBox. I have some legacy applications for each of them: a scanner that HP never wrote Win7 drivers for, a game, etc.

I could wipe the whole computer and start over, I guess. But isn't there some way to just "shove" Win7 off the machine without having to reinstall everything? I have registered install CD/DVDs of all the OSs.

---

### Post by Dutch70 on 2011-04-26
Post a pic of your partitions in Gparted & let's see what you've got.
Please use the paper clip in the toolbar to attach the pic.

---

### Post by boomcat on 2011-04-26
Let's see if this screengrab attaches properly using the paperclip tool...

---

### Post by Dutch70 on 2011-04-26
Wow, you've got so many options, I'm not sure where to start. Granted none that I can see are as simple as you would probably like. You've got to consider the warranty, the boot partition, and the recovery partition. 

A separate /home partition is a very nice thing to have with Ubuntu. So you may be better off to reinstall anyway. 

If it were mine, I would try to shrink the windows partition **from within windows only** down to about 100GB & dual boot with that one.
Then recreate the extended partition with 3 logical partitions inside of it. one for each...
**/** = 15-20GB is normally a good size, but since your running virtual machines & have so much space, you may want to go about 30+ GB.
**swap** = the size of your physical RAM plus about 10% to ensure that you can hibernate successfully. 
**/home** = the remainder of space in your extended partition.

I know this isn't what you wanted, but maybe it will give you some ideas, or help us to get a better idea of the direction you'd like to go.

---

### Post by boomcat on 2011-04-26
I never thought about it before, but a separate "home" partition would be handy, especially because 10.10 allows you to encrypt it.

I think I will reinstall from scratch, before I have more time invested in this install than I already have.

Thanks!

---

### Post by boomcat on 2011-04-26
By the way, is there a thread explaining how to make a separate "home" partition? That's not part of the usual installation process.

---

### Post by Dutch70 on 2011-04-26
> **boomcat said:**
> By the way, is there a thread explaining how to make a separate "home" partition? That's not part of the usual installation process.

There is several tutorials on the net. I think this one is a little older, so it uses things like ext3 instead of ext4 file systems.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Also, if you want to hibernate, you'll need a swap partition at least the size of your physical RAM, plus a little for overflow.
[[COLOR="RoyalBlue"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by boomcat on 2011-04-26
Cool!

Here goes...

---

### Post by Dutch70 on 2011-04-26
If I'm not too late, be sure to select "Try Ubuntu" and install from there. That way you have internet access during the install.

---

### Post by boomcat on 2011-04-27
Well, it's all done. It took about four hours, or about an hour for each OS. Had a crash or two during each install, but managed to recover. One thing that I forgot to do was to make myself a member of the "virtualboxusers" group. That held things up because it prevented the USB ports from getting through to the guest OSs. But right now I can share files across all four OSs (or "OSes"?) from one desktop. I can edit my old home movies using Premiere on W2K, scan documents with a legacy scanner in WinXP, and sync my iPhone with Win7.

Thanks for the advice. Much appreciated!

---

### Post by kaldor on 2011-04-27
> **boomcat said:**
> Well, it's all done. It took about four hours, or about an hour for each OS. Had a crash or two during each install, but managed to recover. One thing that I forgot to do was to make myself a member of the "virtualboxusers" group. That held things up because it prevented the USB ports from getting through to the guest OSs. But right now I can share files across all four OSs (or "OSes"?) from one desktop. I can edit my old home movies using Premiere on W2K, scan documents with a legacy scanner in WinXP, and sync my iPhone with Win7.

Thanks for the advice. Much appreciated!

I think iPhone syncing will work on Ubuntu. Try installing the Banshee media player, I hear great things about it with iPods and iPhones.

As for using Windows 2000 and XP, I'd really recommend updating some of your software and hardware. A new Ubuntu-compatible Scanner would be very useful. I got my printer/scanner for free when buying my laptop from HP (was a giveaway deal a few years ago). It's an [_HP Deskjet F4180 All-in-one_]("http://www.amazon.com/HP-Deskjet-F4180-Printer-Scanner/dp/B000QY6S74") and it worked out of the box on Ubuntu 10.10. It's older now, so it should be able to be found fairly cheap.

As for movie editing, maybe Pitivi on Ubuntu or Windows Movie Maker for Windows 7 (vastly improved, I hear) might allow you to ditch Win2000.

---

### Post by Dutch70 on 2011-04-28
> **boomcat said:**
> Well, it's all done. It took about four hours, or about an hour for each OS. Had a crash or two during each install, but managed to recover. One thing that I forgot to do was to make myself a member of the "virtualboxusers" group. That held things up because it prevented the USB ports from getting through to the guest OSs. But right now I can share files across all four OSs (or "OSes"?) from one desktop. I can edit my old home movies using Premiere on W2K, scan documents with a legacy scanner in WinXP, and sync my iPhone with Win7.

Thanks for the advice. Much appreciated!

Nice work, glad you got it all sorted out.

Don't forget to mark the thread "solved" with "Thread Tools" at the top of the page. :)

---

### Post by boomcat on 2011-04-29
Here's a screenshot of all four OSes, playing together.

---

