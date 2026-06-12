---
title: "Karmic tripleboot with HP Quickweb and w7?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by z_diver on 2010-03-19
Has anyone tried to install Karmic on a laptop that has HP's new Linux on a chip OS installed?  I think it's a scaled down Splashtop desktop and at least a portion of the OS is hardware based.  I sure wonder what would happen if/when I try to install grub and Ubuntu.

Feedback and hints would be great.
p.s. The machine in question is an HP Pavilion dv4-2140us.

---

### Post by z_diver on 2010-03-21
This will come as little surprise, I kinda hosed the system.  Right now only 9.10 is booting although all my windows files are there and it tries to boot.  Here is what I did.

First I unchecked [COLOR=DarkRed]Start Quickweb[/COLOR] in the Win7 control panel.  Easy enough.  I then rebooted the machine again and resized the main partition using disk manager.  Fair enough.  Still booted.  Then created a partion from within disk manager.  (That might be where a problem arose but not certain).

I then restarted the 9.10 cd and tried verified it works.  All good so I installed using manual partitioning on the free space i created earlier with Windows.  Swap first, ext3 for the rest as /.  Installed and rebooted but this time only 'buntu would boot and w7 wouldn't work.  It starts to boot but [COLOR=DarkRed]after the windows boot logo w7 just reboots again[/COLOR].  Hmmm. The windows system files and my data is all there so what could cause windows to reboot like that?

---

### Post by dyslexia on 2010-03-21
Probably writes the partition table in a slightly different manner.

let us know what you discover, linux-on-a-chip is a great idea but it's bound to get weird when it enters the windows gravity well.

---

### Post by Blue DaNoob on 2010-03-30
Yup. I hosed mine too. I think I know where I failed.

I started with a Wubi install in Windows 7. That got corrupted during the updates, so I started over. Got Wubi working, but there is no sleep functionality, so I decided to move it to a dedicated partition. I ended up using [UNetbootin]("http://unetbootin.sourceforge.net/") with Partition Manager to shrink my windows installation from a USB key drive. That worked! QuickWeb and Win 7 were still booting. I let Windows go through it maintenance a couple of times as directed by the tutorial. Now it was time to reclaim the disk space into a new partition.

That was my first bottleneck. Again with Partition Manager, I tried to format the unclaimed space as a new partition. Unfortunately, you are only allowed 4 partitions total. And they already existed: Boot, Win 7, Win 7 Recovery, and HP Tools. Plus, now, a ton of unclaimed HD space. I read that could use UNetbootin with [SystemRescueCD]("http://www.sysresccd.org/Main_Page") to create extended virtual partitions or some such thing, but I decided to just erase the rescue and tools images, and reformat all the reclaimed space into 2 new partitions: one for the root, and one for swap (twice the size of RAM). Partition Manager was able to handle all this as well, although it got a little scary. Rebooted to test, and QuickWeb and Win 7 launched no problems.

I launched Ubuntu under Wubi and installed [Lubi]("https://launchpad.net/lvpm") to migrate the virtual disk over to my new partitions. The first time it failed with a Grub error. 15 I think. The second time it worked better, but still wouldn't boot.  Win 7 and QuickWeb were still launching, but no Ubuntu. I decided to use UNetbootin again to just do a brand new install of Karmic.

I found [this guide]("http://photonymous.blogspot.com/2010/02/dual-booting-hp-mini-210-hd-with.html") about installing a Triple boot system, but I didn't follow it because I had already started down a different path.

In the end, I think I installed Grub in the wrong directory or something under advanced options in the last step. Grub booted, and I could launch Ubuntu, but now Windows 7 wouldn't boot at all. I tried in vain to repair the damage using [SuperGrub]("http://forjamari.linex.org/projects/supergrub/") but it was beyond me.

In a final bout of frustration, I reformatted the whole drive with a fresh copy of Ubuntu. And that's how I broke QuickWeb. I think I saw some files in Windows 7 that QuickWeb might have needed to operate. It's enabled in the BIOS settings, but it won't launch.

I could probably do without Windows 7, but I was really diggin that QuickWeb. Anyone know how to bring it back under Ubuntu? Does QuickWeb have any relationshiup with Grub or should it run first. I guess I'm not sure if Grub broke it, or if removing Windows broke it.

Anyway, I hope all that helps someone.

---

### Post by Blue DaNoob on 2010-04-05
And according to HP Tech Support, Splashtop aka QuickWeb requires Windows 7 Installation to work. If you delete your Windows 7 Partition, you will need to order recovery disks if you want QuickWeb back. It will not work on top of a straight Ubuntu installation. Linux QuickWeb requires Windows.

---

### Post by louistan3 on 2010-06-07
Has anybody figured out how to do a tripleboot? 

I just recently got an HP laptop and was wondering if i could do this.

I dont want to lose the quickweb functionality as it seems pretty useful.

---

### Post by jajaja_622 on 2010-09-26
> **louistan3 said:**
> Has anybody figured out how to do a tripleboot? 

I just recently got an HP laptop and was wondering if i could do this.

I dont want to lose the quickweb functionality as it seems pretty useful.

I have the same question! I dont want to loose the quick web functionality, please if anyone knows share with us :)

---

### Post by tpspencer on 2011-01-29
I've not tried this (yet) myself, but I found this description on how to do this on the HP pages:

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-mini-210-quickweb-install/td-p/212868](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-mini-210-quickweb-install/td-p/212868)

---

