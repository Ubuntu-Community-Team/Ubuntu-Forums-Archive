---
title: "Why does UBUNTU kill /home ??"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by RossDV8 on 2008-11-10
I have been using other Linux distros for more than 10 years and watched them grow and improve.  In nearly all popular distributions when you install, you are offered the choice of reusing the existing /home.

I had been so used to this that I could change versions and distros at will.  I do major backups from time to time, but there are some things that are a pain to backup.  Mozilla settings and Thunderbird mail are two that come to mind.

I installed Ubuntu ages ago and it was running ok, but I saw 8.10 was out so I decided (silly me) to install it without reading the forum.

First thing was I lost my networking.  Looked it up on another computer and found a heap of posts on problems so I found 8.04 and installed that instead.

Now.  I kept my /home on a separate partition, but if I install Ubuntu and choose to mount that partition as /home It tries to create its own /home and mount my partition as well.  It then comes up with an error "cannot enter /home from root" and goes blank.

I edited fstab from a live CD, but the format is different from other Linux distros, so that didn;t work.  So I reinstalled using a few options, which didn;t work either.

I spent an entire day and part of the night and it is still not satisfactory.  I have saved most of my data - the stuff that was already backed up mostly.

What I lost was about 6 years of emails in Thunderbird, all my Firefox settings (a lot easier fixed than lost mail) and some of my documents, like my phone book text file.  (The latest changes since the last major backup)

I have just downloaded a different Linux distribution, one that installs properly.

I hope someone from Ubuntu development reads these forume and can:
Have a look at the way other distributions install.
Modify Ubuntu to look for an existing /home, as others have done for many years.
Set Ubuntu with the option to reuse an existing /home so settings and mail are automatically kept.
To do this, they also have to make sure .mozilla firefox and .mozilla thunderbird in /home are not overwritten.

Almost everyone else can do it (and has done for many years) - why not Ubuntu?

On the distros that keep the existing /home, it doesn;t matter if it is on the root drive or on another partition - they all keep /home intact.

Only Ubuntu destroys data.  Yes, I know it warns us to back up, but as I mentioned, it didn't even mount a separate partition as /home.  AND, it overwrote my backup files on that partition while it was trying to mount it as /home.  (As wella s creating a /home in the root partition)

I know this because I tried to mount another partition as home on a different install and that partition wasn;t available either, but there is now a copy of Ubuntu's /home folders on it!

My other computer is just finishing downloading another distro.  One of the beautiful things about Linux.  On the other hand, I am not abandoning Ubuntu altogether.  I have several computers.  Those that are used for non-critical stuff will still run Ubuntu so I can watch it develop.  The computers that have important long term data will run other distros. 

I simply can't afford to be restoring 100 gigabytes of data whenever I update Ubuntu!

RossD

p.s.

I admire Canonical for sticking to its 6 monthly release cycle, but I don;pt admire them for releasing 8.10 when it is clearly still in beta, with many unresolved bugs.

---

### Post by Chunky Dunk on 2008-11-10
Sorry you feel that way, but you can reuse a previous home partition... Just selection the option that lets you manually set up the partitions, instead of the guided option. This will let you choose what partition gets mounted where on your new install. Also, there will be check boxes that let you choose which partitions get formated... Make sure your /home isn't one of them! I've kept my /home through the last few upgrades, so I know it works.

---

### Post by RossDV8 on 2008-11-10
Thanks Chunky, but as I mentioned in my post, I did choose the old home partition to be mounted as /home, and Ubuntu still created a new /home in the root partition AND tried to mount sda6 as /home - causing the cannot enter home from root error message.

I was pretty sure my previous Ubuntu install didn't kill stuff either, but I can;t be sure.  maybe this is a problem with 8.10?

having said that, I could not get 8.04 to mount my separate partition as /home either, and yes I AM aware of the format/don;t format option.

It can't be all that difficult to detect and offer an option to reuse your old /home.  Most good distros have been doing it for years.

I'm far from being a new user of Linux.  I started using it on a daily basis at Red Hat 4, and had been messing with it before that.  I grew up with Unix.

I'm not knocking Ubuntu - just asking the developers to fix something that shold have been in the distro from the start.

RossD

---

### Post by slakkie on 2008-11-10
Had a similar issue when I reinstalled Hardy via a netinstall.

I totally forgot to mount /home so the root partition had a /home for my user. Removed that and added (via the GUI) my /home slice (which as sda6 iirc) and added it as automatic mount (auto option). I restarted my box to check if the mount went OK. It failed. I saw that the fstab line actually contained noauto and auto options. Fixable, but annoying. The GUI should have checked the fstab line for the noauto option and should have removed it.

We need to create bugs for this imo to get it fixed. The forums are not the correct place for this...

---

### Post by Grant A. on 2008-11-10
For some reason I have a problem similar to yours, Ubuntu always tries to format my /home partition. For this reason, I have stuck my data on a separate FAT32 partition to be mounted after install via editing FSTAB.

---

### Post by robin. on 2008-12-12
This is exactly the thread I've been looking for.

I'm interested in downgrading from Ubuntu 8.10 AMD64 to Xubuntu 8.04 AMD64.

I dual boot ubuntu and vista on a Dell Studio 15 laptop. 

When I set up ubuntu, I set up a separate /home, /, and swap partition.

My questions are as follows:

Will installing Xubuntu over Ubuntu cause any conflicts with the information I have in my /home?

What specifically should I watch out for when partitioning manually in order to keep my /home?

e.g. In the partition maker, do I simply make sure the installation only installs a / (root) and swap partition and nothing else?


- robin.

---

### Post by zvacet on 2008-12-12
Try yo install using manual way and **don't format** home partition.Install Xubuntu on top of your Intrepid root partition.

---

