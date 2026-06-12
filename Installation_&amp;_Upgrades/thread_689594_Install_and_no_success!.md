---
title: "Install and no success!"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by D-Rick86 on 2008-02-06
Hey all, I'm brand new with this Linux/Ubuntu deal, so please bare with me... :D

I am having problems getting Ubuntu to work on my laptop. I recently had Vista crap out on me, so I took it off my system, never to be used again. I figured I would try Ubuntu out since my buddy swears by it. I boot it from the CD and go through the install and everything goes great. When I get about 79% into the install it says it's creating the user, then the window disappears and I get a /target that comes up on the desktop and the CD stops spinning in the drive. I was reading an FAQ that says the disk should automatically spit out and tell you to restart your machine, yet this never happens. I just got a new motherboard but have no info on it. I'm running an Intel Duo Core 1.73Ghz with 2Gb Ram and a 160Gb HD. Anyone have any suggestions on how to get Ubuntu onto my hard drive another way? Please help, I need my computer back!

---

### Post by jan quark on 2008-02-06
its a sort of cop out answer

but various installation problems can be solved by using the alternate CD
I f you haven't used this already download it burn it safely
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

and install in text mode
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

if that "solution" won't work we will have to dig deeper...

---

### Post by solarwind on 2008-02-06
It's possibly a corrupted cd (somehow) or a one in a million situation. Just try again. Something like this happened to me before but I tried it again and it worked!

---

### Post by D-Rick86 on 2008-02-06
I have tried about 3 times from the same CD. Should I try burning it at a slower speed?
I used Roxio on my girlfriends laptop, which I think can do .iso files.

---

### Post by solarwind on 2008-02-06
> **D-Rick86 said:**
> I have tried about 3 times from the same CD. Should I try burning it at a slower speed?
I used Roxio on my girlfriends laptop, which I think can do .iso files.

Boot from the cd and hit "check for defects" I think it's called.

---

### Post by jan quark on 2008-02-06
or something like 

"verify written data" or "check midsum"

---

### Post by D-Rick86 on 2008-02-06
Checked it out. Disk doesn't seem to have any problems with it.

jan quark,
I'm going to try the alternate CD when I get back from class. Maybe that will do something.
Thanks so far you guys!

---

### Post by D-Rick86 on 2008-02-07
Ok, so I tried the Alternate CD that you had suggested. Things were running smooth until I got to the Install Software part then it said that the install had failed. So I tried a few of the steps afterwards and the Lilo Boot loader failed too. I got a "Lilo Install failed at running "/sbin/lilo error code : 1

Do I have to change some settings around in my BIOS to handle the Ubuntu OS or is there some sort of code or trick that I am missing? Thanks!

~Derek

---

### Post by bwtranch on 2008-02-07
LILO doesn't work very well on 64 bit machines. You should use GRUB as a bootloader. I don't know what the default is on the alternate CD because I've never used it. The only other thing I can think of is to use the minimal CD and install from the internet. Been hearing a lot of problems with laptop installs and I'm not sure why that is. Seems to come up with machines that had visdah on them, more often than not. Hmmm. Also, might try partitioning the drive manually. You can (although this is seldom done) use the whole disk. Just one big partition. You could also try another Linux distro like Knoppix or Gentoo or even (hack) Fedora. I'd try Knoppix first, you don't install anything. It just runs as a live CD. There is a way to install it, but I wouldn't bother. Hope something I said helps. Don't give up, it's worth it. Linux/Unix is the best, it's just a little tough to get started.

---

### Post by D-Rick86 on 2008-02-07
I have been checking 'use entire disk' during the install.
If I am to partition it manually, is there a guide you can link me to that tells you how to do it? 

Also, so if I can get Grub on the machine but noot Lilo, that shouldn't be a problem?

---

### Post by SteveHillier on 2008-02-07
> **D-Rick86 said:**
> I have tried about 3 times from the same CD. Should I try burning it at a slower speed?
I used Roxio on my girlfriends laptop, which I think can do .iso files.

In my experience of burning CDs I am guided by some information I received many years ago which never burn at the full speed the cd can take.
I always burn as about half the maximum speed so for modern drives and disks that offer 48x or 52x I use 24x burn speed.
I don't normally get burn corruptions.
Good luck

---

### Post by bwtranch on 2008-02-07
Yeah, well the option "use entire disk" actually means it creates the partitions for you. It doesn't actually make the whole disk one partition. Trouble is, you have to get some kind of working OS on your machine before you can do anything! I think the Gentoo option is a good one. Only problem is Gentoo is really not for beginers. (sp) (whatever) Ubuntu really is the best when first starting out. If you can get it to install, of course. I wish I could figure out what the problem is with your install, but you said you did a checksum and it is an iso IMAGE. right? I'm kinda at a loss at this point. Let me know. I'm going to be up for a while longer, maybe we can figure it out.

---

### Post by kesman on 2008-02-07
What? Lilo for bootloader? I've never seen ubuntu alternative install disk to mention lilo. Maybe you downloaded a wrong version?

---

### Post by bwtranch on 2008-02-07
Re#13 Yeah, I always thought Ubuntu used GRUB. I just didn't know since I've never used the alternate. But, if it is LILO and he has a 64-bit machine, that probably is the problem.

---

### Post by bwtranch on 2008-02-07
But wait a minute, that wouldn't make it hang on install! Ah, it's late and I must be full of beans.

---

### Post by kesman on 2008-02-07
Yeah, but it would cause alternate install disk not to work.

---

### Post by D-Rick86 on 2008-02-07
I just flat out cannot get Ubuntu to install on my machine! Ugh.

Is there an older version like the Feisty Fawn that might work better for me than Gutsy? I'm beginning to hate everything about computers in general... :-P

Oh and you need some sort of OS to install Ubuntu? That might be my problem because I wiped Vista off my machine. (if I understood your post right... :S)

I need an OS that I can put on my hard drive so I can get programs on it that I need for school. With Gentoo, is it relatively easier to get a clean install done?

ANY sort of input from somebody would be appreciated. I am a noobie... :-D

---

### Post by D-Rick86 on 2008-02-07
I'm going to try out the 7.04 release of Ubuntu and Gentoo.

I will give updates as I go. Chances are I will need more help!

---

### Post by D-Rick86 on 2008-02-08
Ok I can't get anything to work...

Anyone know of any versions of Linux that have a higher success rate with a post-Vista Gateway Laptop?

---

