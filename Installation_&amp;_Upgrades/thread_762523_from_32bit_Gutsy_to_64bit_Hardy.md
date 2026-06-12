---
title: "from 32bit Gutsy to 64bit Hardy"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by s_raghu20 on 2008-04-22
Hi,
I have this this system running for about an year now. 

Since its been used for some time, quite a few things have been accumulated/installed.  

I have been playing around with Hardy beta and RC for a few days and I think its ok for my purposes.  Also, I did a sort of upgrade for myself when i chose 64 bit instead of 32bit.  My hardware actually supports it and so I thought why not..

I did not face any problem with 64 bit. Did some reading here and there and liked the idea of going forward with 64 bit only.

Now I feel like upgrading my regular working env (32b Gutsy) to Hardy and also do the 32b => 64 bit migration. 

To my knowledge, there is no way an OS can be migrated from that point of view. I would most probably have to reinstall it from scratch ?? right ?

However, to achieve this "migration/upgrade" I was thinking of the following route, tell me your views on this...

[LIST=1]
[*]In Gutsy, generate a package download script using Synaptic.  This should create a list of all packages that are installed in the gutsy environment.  
[*]Make sure my home directory is not on / (root) partition, so that when its formatted, the home dir still lives and can be re-used later on.
[*]Install Hardy 64b on the same hdd partition.
[*]Plug in the old home directory with the new one.
[*]Using the Synaptic's package download script, reinstall the same set of packages that were installed in gutsy.
[/LIST]

I have both good and bad feelings about this idea already.   I am not 100% sure if the package list from Gutsy will work as I want it to be in Hardy...

I wonder if I am the first one trying this kind of migration/upgrade thing ?  Has anybody tried it before ?

Ideas ?
Experiences ?

---

### Post by jcfisher on 2008-04-27
I've never tried the Synaptic package download script, but I have come across a few pointers on making reinstalling less painful.  Specifically, from the Novell website, have a look at [Install Linux Frequently Without the Hassle]("http://www.novell.com/coolsolutions/feature/11802.html").

Essentially, it recommends dividing your hard drive into several partitions.  One large partition is used for your data, and several (the number of partitions is your choice) smaller partitions are used to install multiple copies of your operating system.  So to upgrade using this system, rather than removing your 32-bit Gutsy, you would simply install 64-bit Hardy into a separate, new partition and have them running simultaneously.  Then if you needed to go back into your old system, you would have no trouble doing so -- it's as simple as picking another option on the bootloader.

The article also brings up one other point about converting.  Some of your settings, stored in your home folder's "dotfiles," will be important to you after you upgrade.  If you keep all of them, however, oftentimes some of the dotfiles won't work with the newer software versions.  So instead of just mounting that data partition as your home folder, the article suggests mounting it as /data. and creating symlinks from your home folder to your data (stored in /data), and to the dotfiles (also stored in /data) where you have saved settings.

I hope that helps.  Best of luck with your upgrade, and let me know if you get the package script to work, since I'll probably be trying the same upgrade too in a few weeks.

---

