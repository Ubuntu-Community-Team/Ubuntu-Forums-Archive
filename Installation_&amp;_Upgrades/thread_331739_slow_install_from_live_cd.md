---
title: "slow install from live cd"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Gill Bates on 2007-01-05
I've been messing around with an old amd 800 trying to get it to read a dvd so I could run the livecd.  To make a long story short I just have the motherboard sitting on my workbench with some cards cables etc. hooked up and the cd is now loading.  Unfortunately I only stuck 128 megs of memory in the mb.  I have another 128megs I just didn't bother installing.  Now I'm afraid to shutdown since it took so long to get the dvd to boot.  Is the lack of memory what's taking so long?  I put 98 on the hdd to get the machine working and plan to overwrite that with ubuntu if it ever loads.  That's an option isn't it?  I'm also concerned that the hdd I'm using is only .5 gigs.  Will I have to start over with a 2 gig drive to get a full install or can the file system just add another hdd and be happy?  Will this 2001 663as_ultra mb with an amd800 chip and 256 megs be a usable system or should I go for faster hardware.  If this system is too slow to be a desktop would it be ok as a home server?  Thanks from a newbie :D

---

### Post by mykalreborn on 2007-01-05
this post shouldn't be here. it should be in the general help section. anyways...

1. why would you need a dvd? ubuntu live CD is on one cd. probably you don't have a cd-rom?

2. the live cd must have at least 192 ram to be able to run properly. i would suggest at least 256 and if you have some money maybe even more - like 384 pr 512.

3. you need at least a 1.5 gb harddrive to install ubuntu's program files. but i would recommend a 5gb one at least so you can store your files on the drive. i don't think you could use it as a desktop system - who wants to use a desktop computer with it's wires and chips sticking out :p. and as a server. i dunno. i think you must have a little cpu muscle to do that. but i'm not sure on that. depends on what you need the server for i guess.

---

### Post by Gill Bates on 2007-01-05
1 Well I have some cd media but only 650s.  

2 I actually ran the cd on my main system (y2k) but it was slow and I didn't want to mess with that box.  This mb/cpu was in an old box I upgraded for my kids.  What I really want to know is how long it will take to get to the point that it puts the install option on my screen?  Or do you think it will just not work with 128 and I need to kill it and add the other dimm?

3. I do plan to put it in a box if I ever get it working the way I want.

As to being in the wrong forum I did sign myself as a newbie.  The slashdot article the other day got me interested in ubuntu.  My only unix experience is as a developer with solaris at a big company which means I know the cshell interface, how to code bourne scripts, various unix/sed/awk commands, and some odds and ends I've picked up.  I've never been allowed root on a unix box.

---

### Post by mykalreborn on 2007-01-05
> I've never been allowed root on a unix box.

never? you don't know what you're missing :p

you should download the alternate cd. it installs without the graohical interface so you won't need that much RAM.[link]("http://ubuntu-releases.cs.umn.edu//6.06/")

or you could download xubuntu, because ubuntu can use quite a bit of ram. xubuntu is "lighter":[link]("http://www.xubuntu.org/")

it's a good thing you know some commands, because you're probabaly gonna need them.

---

### Post by Gill Bates on 2007-01-05
Well I have coded key zero in authorized libraries.

That dvd drive is still spinning.

---

### Post by Gill Bates on 2007-01-05
I gave up and added the other dimm.  It looks a little more reasonable with 256 but it's still taking forever.

---

### Post by mykalreborn on 2007-01-05
yeah! it takes a long time. you could try doing something else while it loads. loke grab a cup of tea or something. it won't seem so long ;)

---

### Post by macogw on 2007-01-05
I got it to run on 192mb on a P2.  It didn't run well.  Live CDs take a bit of time to load because they run entirely on the ram.  I am unfortunately discovering that all of my computers require PC100 ram and I only have DDR, so I can't upgrade ANY of them.

---

### Post by mykalreborn on 2007-01-05
by the way. a friend of mine tried to boot the livecd on a pentium III, - hp bundled, with 256 mb ram, 750 mhz processor and a non 3d accelerated matrox video card. we tried ubuntu xubuntu and linux mint to boot but the only one that worked was gparted livecd. the other ones would show me the boot options (start or install etc) and then remained silent. the guy has a pretty f***up cd-rom but i've written the cd's at 8x or 16x. so it should work. any idea why it doesn't?

---

### Post by macogw on 2007-01-05
ATI card?  It might be booting up beyond that menu...you just can't see it.

---

### Post by mykalreborn on 2007-01-05
matrox si also an ATI card? i didn't know that.
it may boot beyond this but X doesn't start. maybe it's the deskop envoirment. gparted booted, and it uses something else than gnome or kde or xfce.

---

### Post by Gill Bates on 2007-01-05
I finally just left it and went to bed.  When I came back 7 hours later the cd had stopped but I couldn't get the screen to come back.  I moved the mouse and hit enter a couple of times and could hear the hdd working but no desktop.  Since I had to go to work I couldn't hang out and wait to see if the desktop would eventually wake up.

When I started it it ran through the loading screens and then a brown rectangular window opened.  At the bottom center it said something like window manager and at the bottom left an icon appeared.  Mouse movement was slow and jerky.  I know from running the cd on another machine that an install option should come up but it never got there while I was watching.

Should I just give up on the live cd and use the server cd or xubuntu?

---

### Post by mykalreborn on 2007-01-05
not the server cd. maybe the alternate cd. you just install it without entering the x graphic envoirment on the cd. it shloud work for you.
you can find it here:[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by Erik Trybom on 2007-01-05
Yep. The alternate CD is the way to go. Since it's text-based it should run even on very old computers.

In my opinion the alternate CD should be the standard one, and the live CD should be promoted more as a try-out edition for those with fast computers.

---

### Post by K.Mandla on 2007-01-05
(Moved to Installation. ;) )

> **Erik Trybom said:**
> Yep. The alternate CD is the way to go. Since it's text-based it should run even on very old computers.
Ditto that. Skip the live CD with this one. Go for the full-speed text-based install! :mrgreen:

> **Gill Bates said:**
> Is the lack of memory what's taking so long?
Probably, in part. The live CD needs a lot more space to run. But check your BIOS settings too; it really shouldn't take an 800Mhz machine that long to do its thing.

> **Gill Bates said:**
> I'm also concerned that the hdd I'm using is only .5 gigs.  Will I have to start over with a 2 gig drive to get a full install or can the file system just add another hdd and be happy?  
Unfortunately, yes. If I were you I'd cut it short and put the larger hard drive and more memory in. Chances are you'll want more memory when it's installed, and a full Gnome install will take up close to 2Gb of disk space anyway.

> **Gill Bates said:**
> Will this 2001 663as_ultra mb with an amd800 chip and 256 megs be a usable system or should I go for faster hardware.  If this system is too slow to be a desktop would it be ok as a home server?  Thanks from a newbie :D
Usable, yes, but probably not with Gnome. Look into Xubuntu, which it should run without issue. I use Xubuntu 6.10 on a 1Ghz machine, and I have used it on 750Mhz machines as well.

Or even install just XFCE, without the full Xubuntu package ... or Fluxbuntu, Openbox or FVWM-Crystal (my favorite). There are a lot of options, and it doesn't have to be relegated to the boring job of home server either.

---

### Post by Gill Bates on 2007-01-06
I used the alternative cd and it loaded and seems to run well.  One thing I was not sure of was the disk partitioning.  I had loaded 98 on it just to get the machine setup and intended to overwrite it and make it a 100% ubuntu box.  Then they offered me different options for the replace partition w/o explanation.  I dug around in the doc and it seemed to say that lvm simulates the multible partitions in traditional unix in one partition which makes growing the file system easier.  So I went with that.  That sounds like the newer versions of Solaris that have also made growing file systems easier.  Can some one edify me on LVM and if that was a good decision?  The hdd I used was a 6 gig drive.

---

### Post by mykalreborn on 2007-01-06
> Can some one edify me on LVM and if that was a good decision? The hdd I used was a 6 gig drive.

i don't know. i've allways used ext3 in linux. but i guess it shouldn't be a bad decision. i'm not sure

---

### Post by Gill Bates on 2007-01-07
Update:  I was getting ready to chuck this mother board.  Everything, including the DVDs I burned was failing.  I kept getting segmentation errors which someone said were usually memory related so I pulled out the first dimm and moved the second dimm to it's slot.  The clouds suddenly parted and the sun started shining.  Even my DVDs started working.  Thanks all.

---

### Post by mykalreborn on 2007-01-08
allways glad to help a fellow linuxer

---

