---
title: "I/O Error, no Boot Menu after Install"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by ooboontwo on 2011-03-28
**SOLUTION: Burned a new Ubuntu install CD. The first one had an error during burning.**

Hello,

Downloaded the ISO image, burned it to a disc and began installing Ubuntu on my laptop (also has Windows Vista on it). I am beginning the process of migrating off Windows entirely. I played around with Ubuntu using wubi for awhile.

Install seemed to work perfectly. The installation completed and asked to reboot. After hitting the button to reboot the Ubuntu CD popped out and my screen went black.

Then I saw a long list of I/O Errors... sr0 or something.

Machine never shutdown. I manually shut it down after waiting a few minutes.

Now, my machine simply boots into Windows Vista. No boot menu. However, I can tell that there is an ext4 partition (with ubuntu, I'm guessing) because my windows C drive is 20 Gigs smaller than it was before. (That is how big I made my ubuntu partition when I installed using the CD.)

What do I need to do to get this working?

Cheers,
Cody

---

### Post by Dutch70 on 2011-03-28
Did you shrink your partitions using vista? If not, you're very lucky if you can still boot vista. You may want to run a check disk 1 or 2 times to make sure your disk is ok.

Then boot to the live cd & select "Try Ubuntu" to make sure everything works ok.
I would do that before moving to any further steps.

---

### Post by ooboontwo on 2011-03-28
Nope, didn't shrink my partition... not sure what that means...

What good will "trying ubuntu" do me? How can I access the ubuntu I just installed?

Sorry, I'm not a computer n00b, but I am new to linux.

Cheers,
Cody

---

### Post by Dutch70 on 2011-03-28
> **ooboontwo said:**
> Nope, didn't shrink my partition... not sure what that means...

What good will "trying ubuntu" do me? How can I access the ubuntu I just installed?

Sorry, I'm not a computer n00b, but I am new to linux.

Cheers,
Cody

Without sounding sarcastic, shrink means to "make smaller" 
vista doesn't like being messed with from other programs. There is a tool in vista to shrink the partition that vista is installed on.  

Trying Ubuntu will tell you if it will run on your hardware and probably help fix your problem.

---

### Post by ooboontwo on 2011-03-28
Gotcha. I assumed "shrink" meant smaller, but I didn't know what that meant in the context of partitioning for ubuntu.

I did try my cd and now it won't boot at all. Just another black screen with white text that boots me back to a basic command shell prompt. *sigh*

I had Ubuntu running through wubi. I realize that is not a "real" install, but I assumed that it would test all my hardware out and everything. Is that true? If so, it ran perfect from my wubi install. No problems with any hardware or performance.

My laptop is a Fujitsu Lifebook A6025, Dual-Core Pentium w/ 1 GB RAM.

So... now what?

Thanks for all the help. I really would like to kick my windows habit, but like so many others, I am finding it to be a rather discouraging task.

I don't mind using the terminal every now and again, but it would be nice to use the GUI most of the time. I was so excited with how smoothly the install went... and now this...

I'm not going to bash ubuntu like a newbcake, but I do wish it simply worked for me... the first time... every time... heck, even just "most times". LOL (That's all I get from Windows anyway...)

So, again, thanks for the help. Let me know what I need to try next.

Cheers,
Cody

---

### Post by bcbc on 2011-03-28
> **ooboontwo said:**
> Hello,

Downloaded the ISO image, burned it to a disc and began installing Ubuntu on my laptop (also has Windows Vista on it). I am beginning the process of migrating off Windows entirely. I played around with Ubuntu using wubi for awhile.

Install seemed to work perfectly. The installation completed and asked to reboot. After hitting the button to reboot the Ubuntu CD popped out and my screen went black.

Then I saw a long list of I/O Errors... sr0 or something.

Machine never shutdown. I manually shut it down after waiting a few minutes.

Now, my machine simply boots into Windows Vista. No boot menu. However, I can tell that there is an ext4 partition (with ubuntu, I'm guessing) because my windows C drive is 20 Gigs smaller than it was before. (That is how big I made my ubuntu partition when I installed using the CD.)

What do I need to do to get this working?

Cheers,
Cody
This sounds like a similar prob: [http://ubuntuforums.org/showthread.php?t=1532663](http://ubuntuforums.org/showthread.php?t=1532663)

In one the CD was bad. So try burning another one as described here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

PS if wubi runs great, then so will Ubuntu.

---

### Post by Dutch70 on 2011-03-28
Smart move not to bash Ubuntu, the more you learn about it, the more you'll come to love it & understand why things like this happen. 
There is a LOT of room for errors, from the download, the burn, and the hardware. That's not counting human errors.

Do you have a usb stick? It would be much easier if you do.

First you need to make sure you've gotten rid of everything related to Wubi. It's not a good idea to install grub, if you have Wubi installed. 

You should probably run check disk once, maybe twice, until you get no errors. To make sure your windows isn't messed up.

Then check the md5sum of the downloaded .iso
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Then check the disc you burned.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

Then we'll go from there.

BTW, "shrink" is windows terminology for partitioning, not Ubuntu. Ubuntu is resize...LOL.

---

### Post by bcbc on 2011-03-28
If you still have the wubi installed, you can save your settings/data or even migrate it to a regular install. It's not necessary to remove it before setting up a dual boot (the regular Ubuntu won't even know it's there).

---

### Post by ooboontwo on 2011-03-28
> **bcbc said:**
> If you still have the wubi installed, you can save your settings/data or even migrate it to a regular install. It's not necessary to remove it before setting up a dual boot (the regular Ubuntu won't even know it's there).

I wish I had known that... I already uninstalled wubi a few days ago.

I will do everything suggested here when I get home from work tonight and let you know how it goes.

Cheers,
Cody

---

### Post by ooboontwo on 2011-03-28
OK, the MD5 Checksum was fine for the downloaded .iso, but the CD returned 1 error in 1 file when I checked it according to your instructions.

I am reburning the disc at the slowest speed possible. Where do I go after that?

Cheers,
Cody

---

### Post by Dutch70 on 2011-03-29
I had to go for a while also, but I noticed you marked the thread solved. I'm guessing since you found an error on the cd, and burned another one. Then marked the thread solved, you just reinstalled and everything is working. 

Do you mind letting us know what you did so that others can find your solution?

---

