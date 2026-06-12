---
title: "Adding more HDD space?"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by AngelFox on 2011-07-01
Hey am new here & new to ubuntu but I do love it :D
More then my windows 7 <3 Now the problem is I got a 1.36TB HDD and I only set Ubuntu to use 7.3GB and now am sort of space how can I add more to it?

Am running a side by side install Got windows 7 32-bit as my main OS and ubuntu :3

Thanks 
-Fox

---

### Post by Bucky Ball on 2011-07-01
What is already on the HDD? Do you have free space?

To expand the Ubuntu partition it is as easy as booting from the LiveCD, opening System>Administration>Gparted, right click your Ubuntu partition (/), unmount then expand ... BUT, you need to have the free space to expand in to. 

If you have Ubuntu on 7Gb and Windows on the rest this means you are going to need to shrink Windows to create free space.

7Gb is fine for the / partition for a base install but 15Gb would be better if you intend adding lots of apps. What would help is a separate /home for all your data (music, vids, etc.) on its own partition outside of /. I would perhaps think about reinstalling, this time with a plan based on your experience, creating something like;

/ = 20Gb
/home = big as you like
/swap = size of your RAM

... with Windows remaining where it is. You could add;

/share = NTFS file system

... for sharing data between your Windows and Ubuntu, if you intend to do that, as Win will read and write to NTFS but do neither with EXT* partitions (used by Ubuntu).

Welcome to Ubuntu and the forums and good luck ... ;)

---

### Post by AngelFox on 2011-07-01
> **Bucky Ball said:**
> What is already on the HDD? Do you have free space?

To expand the Ubuntu partition it is as easy as booting from the LiveCD, opening System>Administration>Gparted, right click your Ubuntu partition (/), unmount then expand ... BUT, you need to have the free space to expand in to. 

If you have Ubuntu on 7Gb and Windows on the rest this means you are going to need to shrink Windows to create free space.

7Gb is fine for the / partition for a base install but 15Gb would be better if you intend adding lots of apps. What would help is a separate /home for all your data (music, vids, etc.) on its own partition outside of /. I would perhaps think about reinstalling, this time with a plan based on your experience, creating something like;

/ = 20Gb
/home = big as you like
/swap = size of your RAM

... with Windows remaining where it is. You could add;

/share = NTFS file system

... for sharing data between your Windows and Ubuntu, if you intend to do that, as Win will read and write to NTFS but do neither with EXT* partitions (used by Ubuntu).

Welcome to Ubuntu and the forums and good luck ... ;)


Gosh that's confusing :popcorn:  Well my HDD is 1.38TB On windows it says I got 1tb left of space :) 

The part that gets me lost is this >Gparted, right click your Ubuntu partition (/), unmount then expand  ... BUT, you need to have the free space to expand in to. Sorry <3

-Fox

---

### Post by Bucky Ball on 2011-07-01
If you have one terrabyte:

* Boot from a LiveCD (the one you installed from) and choose 'Try Ubuntu';
* Once you are at a desktop, running from the CD, go to System>Administration>Gparted (partition editor);
* Right click on the partition you want to expand (where your Ubuntu is installed, the root partition shown as '/');
* Click 'Unmount' if it isn't already unmounted;
* Right click on the partition again and choose 'Expand';
* When you're done, double check the pane at the bottom which shows what actions you are about to apply;
* Click 'Apply' and you're done.

That will expand your Ubuntu partition.

---

### Post by AngelFox on 2011-07-01
> **Bucky Ball said:**
> If you have one terrabyte:
 
* Boot from a LiveCD (the one you installed from) and choose 'Try Ubuntu';
* Once you are at a desktop, running from the CD, go to System>Administration>Gparted (partition editor);
* Right click on the partition you want to expand (where your Ubuntu is installed, the root partition shown as '/');
* Click 'Unmount' if it isn't already unmounted;
* Right click on the partition again and choose 'Expand';
* When you're done, double check the pane at the bottom which shows what actions you are about to apply;
* Click 'Apply' and you're done.
 
That will expand your Ubuntu partition.
 
Sounds easy :) Only thing is that I never used a CD I used wubi Where can I downlaod the CD?
 
& Thanks for being so nice and making it noob friendly <3

---

### Post by Bucky Ball on 2011-07-01
No probs. Friendly bunch here (generally!). You can download just Gparted by itself if you like and save some time:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

The first ISO should do it. Make a CD and boot from that. If you want to run it from a Ubuntu LiveCD (always handy to have around) select your image from here, probably the 64bit if you have dual-core:

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

To explain, Gparted is a partition editor that comes default as part of Ubuntu. ;)

This is all good, but as you have a look at Gparted and learn the ropes a bit, you may want to consider re-installing later on and creating the partitions yourself rather than letting Wubi do it. Whenever you use an auto-install method it creates the partitions at sizes *it* wants which don't always fit with what the *user* might prefer.

---

### Post by oldfred on 2011-07-01
Bucky Ball has given great advice if you have separate partitions, but then you mentioned wubi. I do not know wubi either.

Is your install wubi which is just a file inside the windows NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Wubi is for windows users to try Ubuntu without partitioning. But if you are liking Ubuntu and using it a lot, you may be ready to convert to full partitions. Even the designer of wubi expects you to convert:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Kixtosh on 2011-07-01
If Migrating from Wubi (a Windows installed Ubuntu), I think you need to:

1) Shrink your partition using Windows, not GParted first. Windows 7 doesn't like anything else messing with its junk, apparently! Before shrinking, however, you should defragment your Windows partition with the Windows disk defragmenter tool. Then, do it again. Then, do it again. It should take less time to complete each time. If it's still taking a long time by the third try, just do it again once or twice more for good measure.

2) Create a new partition for Ubuntu. This you can do using the GParted application, from a LiveCD. You"ll find it in the System menu. 

Note: You'll need to be able to burn an ISO image file to a CD to make the LiveCD beforehand. I'm not sure if Windows 7 can do this natively, or if you need to find a free utility first. You should even be able to use your Wubi Ubuntu to do it, in which case you won't need anything new at all. Look in the Ubuntu Applications menu for Brasero, or something similar. It should be with the Sound & Video group of applications. That would make it extremely easy. Try also to burn the LiveCD as slowly as possible. 4x speeds have worked well for me.

3) Format the new partition as Linux ext4, and follow the migration procedures to modify your Wubi installation.

Honestly, if you haven't been using Wubi for long, I would just forget about the migration of Wubi altogether, and just use the LiveCD you made create a side by side installation of Windows and Ubuntu. It's quite a simple process, especially if you have already shrunk your Windows partition. 

If the above procedure for creating various / and /Home partitions seems too daunting with your current level of knowledge of Ubuntu, I would forget about it for now, and just use a default installation. You can still change that further along down the road to Ubuntu Nirvana, when you are more familiar with everything. It's a lot easier than it sounds, most of the time, and a default installation is really very simple. Just remember to keep Windows happy by defragmenting, and shrinking Windows _with Windows_ first.

Link: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by AngelFox on 2011-07-01
First I would like to say thank you to everyone here :) You really helped me out and for a noob hehe ^.^ So I tried all your tuts but they where way to hard for me :( so I backed up all my passwords settings and such then I removed ubuntu using [Wubi]("https://wiki.ubuntu.com/WubiGuide") Then I reinstalled it but with a 19GB HDD :D Using [Wubi]("https://wiki.ubuntu.com/WubiGuide")
It seemed like the most easies way of doing  it :( 


But Thank you all for the help <3 I love you all and I sure do love ubuntu :KS

Thanks
-Fox

---

### Post by moonport on 2011-07-04
> **Bucky Ball said:**
> What is already on the HDD? Do you have free space?

To expand the Ubuntu partition it is as easy as booting from the LiveCD, opening System>Administration>Gparted, right click your Ubuntu partition (/), unmount then expand ... BUT, you need to have the free space to expand in to. 

If you have Ubuntu on 7Gb and Windows on the rest this means you are going to need to shrink Windows to create free space.

7Gb is fine for the / partition for a base install but 15Gb would be better if you intend adding lots of apps. What would help is a separate /home for all your data (music, vids, etc.) on its own partition outside of /. I would perhaps think about reinstalling, this time with a plan based on your experience, creating something like;

/ = 20Gb
/home = big as you like
/swap = size of your RAM

... with Windows remaining where it is. You could add;

/share = NTFS file system

... for sharing data between your Windows and Ubuntu, if you intend to do that, as Win will read and write to NTFS but do neither with EXT* partitions (used by Ubuntu).

Welcome to Ubuntu and the forums and good luck ... ;)

I've a very similar partition map. My Swap part. is 2Gb, as my RAM. Sometimes, this is an issue when you are trying to update to the next kernel release. I suggest 4Gb for Swap.
At least, this is my experience.
Regards.

---

