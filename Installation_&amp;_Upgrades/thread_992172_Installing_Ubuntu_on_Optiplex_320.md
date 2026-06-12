---
title: "Installing Ubuntu on Optiplex 320"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by randyrick on 2008-11-24
Has anyone had any luck installing any version of Ubuntu on this computer?  I can go through the installation just fine, but when it reboots into the installed system, I just get a blank screen.  Any help?

---

### Post by oilchangeguy on 2008-11-24
> **randyrick said:**
> Has anyone had any luck installing any version of Ubuntu on this computer?  I can go through the installation just fine, but when it reboots into the installed system, I just get a blank screen.  Any help?

computer specs would be helpful. cpu speed, amount of ram, and hard drive size. and version of ubuntu you're using.

---

### Post by randyrick on 2008-11-24
Intel Pentium D 4945MHz, 1GB RAM, 160GB hard drive, I'm trying to install Ubuntu 8.04 - 8.10 with no luck...

---

### Post by randyrick on 2008-11-24
Looks like this might work...

[http://backports.ubuntuforums.com/showthread.php?p=6116405](http://backports.ubuntuforums.com/showthread.php?p=6116405)

---

### Post by stringy-jb on 2008-11-30
Hi all, 

I have been facing problems similar to a lot of other people (or so it seems from reading all these posts in the forum). 

My situation is actually kind of funny -- I tried to install Ubuntu 7.04 sometime around late-May-early-June-ish last year on this (then) newly bought **[COLOR="Red"]Optiplex 320[/COLOR]** (specs: Intel Core 2 Duo, 2GB RAM, 160GB Harddrive) and following Stateman's [post]("http://ubuntuforums.org/showpost.php?p=2463643&postcount=4") managed to solve the issue (I am a fairly newbie to Linux and most of the time I just blindly followed the suggested steps). Well that worked and I was happy. 

From about a month ago I have been trying to make a clean install (my computer got slower -- so didn't try through Synaptic) first of 8.04 and then of 8.10 using the Live CD (verified and tried on other computers where it worked). The Live CD wouldn't even start installing/run Ubuntu from the Live CD without making any change but my computer would just stall -- blank screen -- I have tried some of the suggestions posted elsewhere on this forum but with no luck whatsoever (I find this very disturbing since with 7.04 it at least installed the thing) 

Well, I came to know about Wubi eventually, reinstalled Vista (which I hated to do but without any other options left out), installed Wubi and installed 8.10. Now the problem is I don't know of any way to get rid of the Vista, and in the current setting Ubuntu apparently uses only 20GB of the available 160GB. **[COLOR="Red"]I would never use the Vista and I just want to get rid of it ![/COLOR]** 


I have tried to go through most of the post related to my problem (however being new to the stuff, I might have missed something important from reading through them) but so far I have not been able to find an appropriate solution.

All I want is to make a clean install of 8.10 and just it (i.e no dual boot etc). Any suggestion will be greatly appreciated. 

Thanks a bunch in advance,
 
-- JB

---

### Post by JustCallMeCrash on 2009-02-04
Ok, I've got this exact system and the only way I could get it to work was to amend the boot options.  When you're presented with the first Ubuntu menu hit [TAB] and put all of the following behind the last word, but before the -- (make sure the -- stays intact and ONE space past your last letter... I don't know why this is so, but it's very cantankerous):

noapic nolapic noacpi pci=noacpi all_generic_ide hpet=disable pnpbios=off

And yes, that is a lot to type every time... that's why you'll want to throw it behind all the options in your /boot/menu.list
Best of luck and let us know how it goes.

Running Mint5 (Ubuntu based distro) Check the new version 6 out at [www.linuxmint.com](www.linuxmint.com)

---

### Post by shaiberger on 2009-02-19
Hi,

At first I was very happy to see this post. It allowed to -- finally -- move from Gutsy's kernel. But now I realized that with these options, I only get one core running.

Can anyone please comment on which of the options caused this, and how I can restore the second core?

Thanks,
   Shai.

---

### Post by shaiberger on 2009-02-19
Well, I solved my own problem...

I found out by some reading that the likely culprits are the _noapic_ and _nolapic_ parameters. Somewhere in the log of a successful (Gutsy-kernel) boot, I saw that the kernel expected up to 6 extra plug-n-play cores, so I also suspected _pnpbios=off_.

So my first attempt (with a live-cd) was to just kill all those three, and it worked. My parameters now are just

```
noacpi pci=noacpi all_generic_ide hpet=disable
```

And things seem to be working just fine. Two cores.

One little note -- on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/138305](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/138305) it looks like several people were pleased with just _hpet=disable_. I wasn't -- I didn't have sound; YMMV.

---

### Post by shaiberger on 2009-02-19
Surprise surprise -- this also fixed a problem I was having with VirtualBox -- a windows VM used to freeze in start-up...

---

### Post by mararual on 2009-02-24
Finally! I was looking for some way of installing Mint on a friends Optiplex 320. Thanks a lot to all, this worked great!

---

