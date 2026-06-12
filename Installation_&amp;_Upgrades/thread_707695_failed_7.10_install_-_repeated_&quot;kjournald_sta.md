---
title: "failed 7.10 install - repeated &quot;kjournald starting&quot; message"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by BSalters on 2008-02-25
Recently I just set my first steps into Linux world. So far, no real luck yet.

I am trying to install Ubuntu 7.10. The installation seems to work perfectly. The live CD works nicely, and 'everything' seems to work when using the CD. Answering the questions during installation gives no problem either.

Problems start however when trying to boot for the first time from harddrive. No matter what I try, I end up with: 
Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _

Using the -nosplash option I discovered that the last thing that shows, is a repeated dual line:
[109.251947] kjournald starting. Commit interval 5 seconds
[109.251957] EXT3-fs: mounted filesystem with ordered data mode.
[109.261894] kjournald starting. Commit interval 5 seconds
[109.261998] EXT3-fs: mounted filesystem with ordered data mode.
[110.470020] kjournald starting. Commit interval 5 seconds
[110.470029] EXT3-fs: mounted filesystem with ordered data mode.
...
[116.540922] kjournald starting. Commit interval 5 seconds
[116.540927] EXT3-fs: mounted filesystem with ordered data mode.

In  total 15 times. 

I have found several postings relating to the (initramfs) prompt, but none seem to match this problem. Are there any suggestions specific to this?

Thanks!

NB: System information
ASUS P5K-e motherboard
Q6600
8800GTS videocard
2*SATA 500GB Samsung HD, in RAID0, holding windows XP
1* 160 IDE harddrive, dedicated for Ubuntu

---

### Post by BSalters on 2008-02-27
Gentle kick.... Does nobody have information on what a repeated

....
[110.470020] kjournald starting. Commit interval 5 seconds
[110.470029] EXT3-fs: mounted filesystem with ordered data mode.
....

means during a (failed) install? 
Is there any other way of finding out what exactly is going wrong here?

---

### Post by masterthor on 2008-03-02
I get the same exact problem but in different circumstances: 
As my cdrom unit is toasted and I can't get another one, I'm looking for ways to boot an iso from the hard drive. So trying to add to grub kernel parameteres "boot=casper find_iso=/path/to/iso" on a Hardy Alpha5 image. It boots up, shows a few kjournal things like in the above post, and throws me in the initramfs prompt.

---

### Post by BSalters on 2008-03-03
Hmm, no offense towards all the volunteers here that offer countless hours of free helpdesk support to other users here, but....

I am trying to finally make the switch from being a long-time windows user, to Ubuntu. To me, no matter how wonderful an OS is once it works, it is also of crucial importance that errors come with a clear and understandable error message.

In my case, installing (or actually: booting) does not work. Instead I get some non-descriptive prompt. From numerous hours of searching on the internet, I have found that it maybe has to do with my choice hardware. Or with my dual-boot setup. Or something else. The amount of times that people suggest to "burn the CD again" is also striking, including the amount of times you read that it didn't help.

What is most frustrating though, is the fact that nobody seems to be able to figure it out. I've posted a question with - I believe - all relevant information, but that is apparently not enough to trigger someone. Why doesn't (in my case) the booting process fail with a message like "unable to intialize harddrive", or "conflict in boot menu" or something else that points me in the correct direction?

Or is there perhaps a website that documents what to do when installing Ubuntu does *not* go according to plan, and fails in a specific way? 

Again - no offense towards anyone trying to help out users here, completely for free. Just a suggestion / question from a slightly frustrated Ubuntu - wannabee....

PS: of course, answers to my original problem are still more than welcome

---

