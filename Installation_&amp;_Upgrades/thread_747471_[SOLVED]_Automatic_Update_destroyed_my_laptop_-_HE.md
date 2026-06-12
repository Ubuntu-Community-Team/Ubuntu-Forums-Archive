---
title: "[SOLVED] Automatic Update destroyed my laptop - HELP!"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by nirpius on 2008-04-06
I am on Kubuntu 7.10. I just used synaptic automatic update to update a couple o files when I started it up. I think 5 were for some printer framework and the last, I can't remember.

As soon as the update was finished, Amarok crashed. I ignored this as it seems this version of Amarok s pretty buggy anyway so I clicked on my quick launch icon and nothing happened. So I went into the Kicker menu and it just had the names of all the programs but no icons. Clicking on any of them didn't work. So i clicke on shut down and there were no icons on the little popup screen that came up then either. I clicked above were it said shut down or whatever it says (where the icon should have been) but nothing happened. So i tried ctrl-alt-del to shut it like tht and I got nothing. So I held ctrl and typed r e i s b which someone told me once can shut it down safely bt this did nothing either.

I left it for 5 minutes, then held the power button in until my laptop turned off. Then I turned it back on and it wouldn't boot. It todl me that it couldn't load a hard drive or something. I tried numerous live CDs and none of them could even load. Eventually (on the 3rd attempt) I got it to load with Kubuntu 7.10 but then half way through the install (when it says prepare partitions) there is nothing listed for me to click on - it can't find ym hard drive. I tried looking in dolphin and konqueror too and it couldn't find anything there either.

Does anyone have any idea what to do? I have loads of music on my home partition and some family photos too, although they are backed up so I don't really want to clear the disk but I will if that's the only way.

Many thanks in advance

PS I am not particularly technically minded, I have no dea what most terminal codes do but I am prepared to pull an all-nighter here and look them up so any replies would be greatly appreciated.

Thank you again

---

### Post by nirpius on 2008-04-06
I just tried again, sma eproblem. I clicked next on the blank partition screen and it said

> No root file system is defined

Please correct this from the partitinoing menu.

---

### Post by momist on 2008-04-06
Holy **** nirpius ,

This is bad karma, but don't panic.  You say you will pull an 'all nighter', but I would recommend you don't do that.  I make most mistakes when I'm tired, and when I'm anxious as well it's worse.

There are tools available to recover whatever is on your hard drive, and even to re-install from scratch after shunting the valuable stuff to one end of the drive.

I'm no expert (yet), but I would recommend System Rescue-CD which has some valuable tools.  I'd say sleep on it, get a copy of System Rescue, and read up some on this forum about it.  It could just be that the boot loader needs recovering, or that there has been a hardware failure.  Either way, take it slow and careful and the damage might look trivial after a month.

Good luck, and I hope someone else comes in with constructive ideas.

---

### Post by nirpius on 2008-04-06
Thank you.

I am downlading system rescue now. I have also downloaded gparted live cd to check if that can find my hard drive but I'll read up on sysem rescue before doing anything else.

---

### Post by Pumalite on 2008-04-06
You can use TestDisk too: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
And you can recover your stuff from most Live CD's
Here are a few programs to do it:
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by greenstar on 2008-04-06
If I had to take a stab based on your description, I'd say you have a hard drive failure. Are you able to remove your hard drive and install or attach it to another PC? If so, do that and see if you can access your hard drive with a live cd. If you can, it might be a problem with the hard disk controller or perhaps the drive's connection to the motherboard has become loose.

If your hardware is working fine, then you should be able to run from LiveCD and be able to access your drive. I recommend SLAX, it's what I would use for simple drag-and-drop or terminal-based file recovery. For almost everything else I like Ultimate Boot CD, it has hundreds of utilities for nearly every imaginable purpose. YMMV

Good luck.

Greenstar

P.S. I seriously doubt that Automatic Update had anything at all to do with this, just to set the record straight for others who might read this (though I have been wrong before).

---

### Post by nirpius on 2008-04-07
Thankyou to everyone. I am trying out these leads now. I will get back to you with the results when they materialise. I would have replied sooner but I've been at work.

---

### Post by nirpius on 2008-04-08
I tried those things but to no avail so i have sent in my laptop to the computer shop for a new drive :( on the othewr hand, it was only £50 so that's not too bad - even if the shop was called Corporate Micros but we'll ignore that.

---

### Post by greenstar on 2008-04-08
Sorry I wasn't able to help more. The upside is that you didn't break your Ubuntu, your hard drive did.:biggrin:

Greenstar

---

