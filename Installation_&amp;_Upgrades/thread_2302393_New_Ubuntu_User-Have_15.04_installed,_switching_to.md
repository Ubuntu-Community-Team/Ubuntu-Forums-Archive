---
title: "New Ubuntu User-Have 15.04 installed, switching to Lubuntu 15.10-have issues"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by Ms.Fix-It on 2015-11-10
Hello and thank you in advance for your help! I'm pretty new in the Linux neighborhood, and looking forward to learning all I can, as I enjoy bringing new life to older systems that have been put out to pasture by previous owners. (I currently have eight laptops/notebooks that I'm looking forward to nursing back to health!)  With the end of Windows XP support, came my curiosity about the world of Linux, and a recent surgery sat me down long enough to begin to "research and apply". My first project is an HP Pavilion Entertainment PC.  It has a 160GB HDD, AMD Turion64x2, 1.5GB RAM, GForce 7150M/NForce 630M (I can send a more detailed list if necessary). The system had Vista Home Premium installed, but the best I can figure, the Windows Explorer file was corrupt. After running Ubuntu 15.04 Live (from a USB stick) for a bit, I installed it alongside of Vista, but it didn't function well, so I replaced that with Ubuntu 14.04 (this time I chose the option to wipe Vista off the HDD during installation). I had it working pretty well, except that I was having an over-heating problem. I recently read in forums that my system is fairly notorius for this, so it was recommended I use a lighter version.  I've deduced that Lubuntu 15.10 LTS  would be my best choice. (Please advise if I am mistaken!)
         I have run into a few obstacles with this transition, however.  I am currently using that Pavilion from a live environment using Lubuntu 15.10 on a bootable USB.  First of all, I wasn't sure if I should delete the partition that has 14.04 on it and install 15.10 in it's place, or if I might damage something doing it that way. (?) Also...that particular partition (Logical) says that it's 148GiB, so I thought I could just install 15.10 on it, and THEN delete the 14.04 installation, but when I tried that, I got an error saying there is no room left on the partition.  WHY is that?  Surely, the 14.04 installation did not take up 148GiB!  So what else is on that partition? ( It shouldn't be Windows files, because I chose the option to wipe those out when I installed 14.04. )   The HDD is as such:
 1>  /dev/sda1-    ext2      -243.00 MiB (used-201.55 MiB, unused-41.45 MiB){Boot}
 2>  /dev/sda2-extended  -148.81 GiB (--------- extended partition-----------  )
 3>  /dev/sda5- lva2 pv-148.81GiB(used-148.81 GiB, unused- 0.00 B){lvm}[mp ubuntu-vg]
 4>  /dev/sdb1- fat32  - .46GiB(used-888.61 MiB, unused-6.60GiB) {boot, lvm}[mp /cdrom]
 5>          ----  unallocated ------  1.92 MiB   -----   unallocated           -------          ------

Second problem;  When I tried to install Lubuntu 15.10 this morning, I got a message box requesting my "default" keychain password.  After trying to enter my regular log-in password 10 times and spouting off a few choice words, I very vaguely remembered something about a second password a couple months ago, when I did the very first installation.  Well...naturally I threw that away -literally- 4 days ago. Heck,  I had never been asked for it again, and I figured after several different installations, it must have been rendered obsolete.  I was finally able to do a few things without it today, but I would like to know if there's some way to find that password or some way to make the system NOT ask for it again?   Third problem:  For some reason,  if I turn off the system or re-start it...it takes FOREVER to boot up.  I get this same message over and over every two minutes,  it starts with 120 seconds, then 240 seconds, and so on, for 10 or 15 minutes, then the screen turns purple for another 20 minutes or so,  and then the homepage finally appears. Here's what it looks like:

{360.1766981}: INFO:  task kworker/1:1:36 blocked for more than 120 seconds.
{360.1767591}                Not tainted 4.2.0-16-generic #19-Ubuntu
{360.1768181}   "echo 0> /proc/sys/kernel/hung_task_timeout_secs" disables this message.
(Two minutes later it repeats this...starting with 480, then 600, etc.)

Didn't mean to write a Novella !  I look forward to your opinion and wisdom.  Thanks!

---

### Post by grahammechanical on 2015-11-10
First problem

You need to do some reading in Wikipedia on the subject of primary, logical and extended partitions. When working with old computers you will need to understand about the msdos partitioning table and the 4 primary partition limit.

/dev/sda2 is an extended partition 148.81 GiB in size. Tell the installer to put Ubuntu in sda2 and it will tell you that the partition is full because inside the extended partition called sda2 is a logical partition called sda5 and that is 148.81 GiB in size. = sda2 = full.

You need to tell the installer to put Ubuntu or Lubuntu or whatever in sda5.

Second problem

As you intend to reinstall anyway, why not take the Erase disk and install Ubuntu option and keep a note of any password. Do you choose to encrypt the home folder?  Do not forget that password.

Third problem

Might be fixed by a complete fresh install. A fresh install with the erase disk option will most likely fix all three problems.

Regards.

---

### Post by Bucky Ball on 2015-11-10
Welcome. Just a tip: You will greatly improve your chances of getting support if you use a few more paragraphs rather than the 'wall of text' approach. Many will take a look and move on. Good luck. :)

---

### Post by Ms.Fix-It on 2015-11-10
Thanks for reading/answering...in the future, I will be careful to utilize proper paragraph etiquette.  

In response to your response...Yes, I fully understand the rules of partitioning where msdos is present,  what I was saying is that I tried to install lubuntu yesterday morning,  _on the sda/5 partition_, and got an error message saying there was no free space on it.   I am just very confused about what could possibly be occupying_ every bit_ of 148.81 GiB, when to my knowledge, all that should be on it is an installation of Ubuntu 14.04.... :-k  ( It's really not that important right now, just curious.)

I'm not sure, but I think that my inability to install Lubuntu yesterday was because I "tried without installing" for a while, then later on I tried to install from inside the live environment.  I wanted to  				utilize GParted, just to check it out.  Nonetheless, I will attempt the Erase disk and install option in just a few minutes.  And yes, I did choose to encrypt the home folder, and I do have that password...the one I threw out was a computer generated one, referred to as "default keyring" or "keychain", and I promise, I won't make THAT mistake again.

As for the boot issue,  I don't think this new installation will fix it, because, if you recall my saying...I had originally installed Ubuntu 15.04 along side of Windows, then later on I did a fresh install of 14.04 using the "Erase disk and Install" option.....and that did not affect the booting error, for the better or the worse.   It has been screwed up since the first installation, and I haven't attempted to fix it, as I was dealing with other issues.  

I am going to try the fresh install of Lubuntu right now, so I shall return with the results in a little while.   Thanks again  for sharing your time,  wisdom and knowledge!      

Cheers

---

### Post by Ms.Fix-It on 2015-11-10
I will certainly take that under advisement, Dear....and Thank You.  They really did teach me a few things in grammar school, and proper use of paragraphs was one of them.  Shame on me for slacking off!           

God Bless:KS

---

