---
title: "Next release grub"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by anthony2010 on 2012-08-19
Straight question.

Will the grub issue be resolved for the next release?

I ask because nothing in the forums helps when every Ubuntu / ubuntu derivative I try inevitably collapses into the ball ache singularity that is >Grub rescue.

I want a system that works without having to read the equivalent of war and peace ever few weeks to figure out what to do.. which I never have, I am left with a complete re install every time followed by the configuring of the system every time and a partridge in a pear tree.

I know I'm asking a lot in expecting a stable operating system but if this isn't going to be fixed would somebody please tell me so I can make other arrangements?

Thanks.

Anthony.

---

### Post by darkod on 2012-08-19
Straight answer.

Grub works.

However, there are a number of situations, sometimes even hardware related, that could create problems. As with any software.

For example, some older boards have BIOS limitation that it can't read boot files beyond 137GB on the disk. With disks today being much larger than 137GB, if grub config files end up beyond the limit they will not be able to be read which is the BIOS limitation, not grub.

Usually that is the most common reason for the grub rescue prompt. Are you sure you are not affected by it?

And anyway, a complete reinstall is rarely needed what ever the grub problem is. Even grub can be easily removed and reinstalled, without reinstalling the whole OS.

But you have to find what your issue is first, obviously you have one. I started using ubuntu when 9.10 came out as first time user, not knowing anything about it, and never had any issues with grub.

---

### Post by oldfred on 2012-08-19
I also have not had much if any issues with grub2. My issue is kernel mode video drivers and I have to use nomodeset in the grub menu to boot the liveCD or first boot until the proprietary drivers are installs.

Many of the most common issues can easily be solved and this gui tool solves most of those:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

But I like to have several repairCDs including Supergrub, Knoppix and gparted.

---

### Post by Blasphemist on 2012-08-19
You could run the boot info script in darkod's signature or make yourself a boot-repair disk or even install boot-repair in your working installation. These options will allow you to pass very good configuration detail to us for review. We'll be able to see if there is something to be addressed.

No offense, just a reminder. When something happens, the first thing to think of is what did I just do or do since the last boot in this case. It is right that fixing boot issues very rarely causes a need to re-install anything more than grub.

---

### Post by anthony2010 on 2012-08-20
No offense either but:

1. The system runs a quad core processor so I feel sure its not that its due to an 'old board'

2. I didn't 'do' anything.

Please let me explain. I've had exactly the same problem with Mint, Ubuntu and Ubuntu Studio.

What happens is that after a few weeks of perfectly functional computing, the OS starts to play up. Internet gets slow, booting starts to require 'rescue mode' then eventually, I end up with just the 'Grub rescue' prompt.

Its not me, its not my hardware, its something about 12.04.

I cant fix it because the rescue disks dont boot before my tv screen says 'no signal'

I too have been a user of ubuntu since the days of Ubuntu 8.04, mint 5 and good old freespire! I've never had this problem until 12.04 was released. I'm not alone either, look at the boards. 

Its not going to be resolved all the while we are in denial and pointing the finger at peoples bios or what they did last. The problem lies within 12.04.

Ant.

---

### Post by oldfred on 2012-08-20
When it starts slowing down that is the time to investigate why.

Have you checked log files? 

Is system filling up either some run away process in log file or too small  partition somewhere?

Does hard drive pass as ok in Disk Utility Smart Data?

---

### Post by darkod on 2012-08-20
Are you sure the hdd is not playing up with you?

The grub rescue would show up if the root (or boot) partition goes "missing". Before that happens, slowing down and needing the recovery mode might sound like the hdd playing up.
Is the SMART data OK?

Sata cables, physical connection? Plug it into another sata port and give that a go, etc...

---

### Post by anthony2010 on 2012-08-22
Hi.

Wel I did as suggested and run a smart data test on the hard drive.Its healthy.

The cables are secure too.

Now my other computer (a 32 bit laptop) is exhibiting the same difficulties. Namely, the - [ ] x have disappeared, I cannot use the menu's on any of the widows because the also disappear as soon as I try to scroll on them. Also firefox does not allow me more than a few minutes to navigate a webpage before it freezes and a reboot is required.

I dont know if this helps home in on the problem but cairo dock has developed a black background instead of the transparent one its had for weeks.

Clearly, its not my systems because the exact symptoms are appearing on two very diferent computers. Further the htpc is 64 bit and the laptop are 32 bit. Therefore, I put it to you all again.. theres a fault in the OS or in an update because the machines seem to work fine for a couple of weeks before becoming unusable. In the past, before 12.04, they worked fine.

I am going back to Ubuntu Studo 10.04 on both machines for now because that was the last OS that worked fine.

I dont have the luxury of poncing about trying to figure this stuff out. I need a machine that works.

I cannot mark this as 'solved' because it isn't. Reverting to an old OS because a new one doesn't work and because figurig it all out is a task for someone with a bloody doctorate in computer science, does not resolve the problem.

Ubuntu is broken.

Ant.

---

### Post by Blasphemist on 2012-08-22
First, take no offence. You do realize that millions are using ubuntu without your problems right? The computer is nothing if not relentlessly logical. The same cannot be said of us humans. There is an old tech support saying that every user should think of when problems show up, because a lot of the time it is applicable. PEBKAC. Problem exists between keyboard and chair. Whenever we have issues the first thing to think of is what have I done? What may I have done during installation is a good place to start since it is the beginning and in your case the issue is affecting both of your systems which are using different kernels and app versions in some cases (64 vs 32 bit). 

I'd create a boot-repair usb or cd. You can use it to provide a good config report for troubleshooting now and to recover the next time you get the rescue prompt.[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by YannBuntu on 2012-08-22
**@anthony:** you are not the first one with this kind of problem with 12.04.
You may be affected by this 12.04's GRUB regression: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887)
Please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URLs for each of your computers.

---

### Post by Quackers on 2012-08-22
YannBuntu, not sure how that would be a regression, as such.
There was a reply to your bug an hour ago asking for clarification.

---

### Post by anthony2010 on 2012-08-22
Hey all.

I didn't want to come off as a whiner.. Im an avid fan and outright advocate of ubuntu / studio / mint and have enjoyed Fedora and Gentoo in the past. Theres no way I'm leaving the linux world. I just need to crack this...

Once again.. its not me! Its nothing Ive done! Ive successfully ran Ubuntu and derivatives thereof for five or six years without any major issues beyond the usual learning curve. Hello! It must be an update or this grub regression yann has spoken of. 

When time permits, I will set up an old laptop, pop 12.04 on it and follow the thread yann has offerred. Once cracked, I will mark as solved and post the solution.

Peace and linuxy solidarity.

Ant.

---

### Post by oldfred on 2012-08-22
Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it does not use the slideshow.

---

