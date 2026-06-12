---
title: "My rant about upgrades and Ubuntu"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by jackelmatador on 2007-05-31
So I guess through the magic of updates it seems there was a kernel update and now half my system doesn't work.  Awesome I know, I have to go through and remember all the things I had previously compiled installed and updated to get the new kernel working.  And people wonder why isn't Linux more popular, this is freaken ridiculous!  I just can't believe that updates break everything, I know Windows isn't perfect (I have never owned OSX), but damn I never had so many problems.

---

### Post by bulldog on 2007-05-31
Mmm,...........simple solution,just use your previous kernel.:p

---

### Post by jackelmatador on 2007-05-31
Yah I know that is the simple solution, but shouldn't you be able to upgrade and not have to worry about all this crap?  I mean now I have to edit Grub to start -15 automatically because my wife won't hit escape to go to the grub menu, and then select kernel -15.

---

### Post by bulldog on 2007-05-31
Yep it's a lot of work.

Some times,when you have bad luck,this kind of things happen.
I,for myself didn't had any trouble with the upgrade,and I think I'm not the only one.
But others,including you,weren't so lucky,but I don't think you can avoid it.

I'm most certain,the developers do their best to make everybody happy.

---

### Post by stchman on 2007-05-31
> **jackelmatador said:**
> So I guess through the magic of updates it seems there was a kernel update and now half my system doesn't work.  Awesome I know, I have to go through and remember all the things I had previously compiled installed and updated to get the new kernel working.  And people wonder why isn't Linux more popular, this is freaken ridiculous!  I just can't believe that updates break everything, I know Windows isn't perfect (I have never owned OSX), but damn I never had so many problems.

Just switch the -15 and -16 kernel places in the /boot/grub/menu.lst text file.

This is a one time thing since grub will default to the first section.

---

### Post by stchman on 2007-05-31
> **bulldog said:**
> Yep it's a lot of work.

Some times,when you have bad luck,this kind of things happen.
I,for myself didn't had any trouble with the upgrade,and I think I'm not the only one.
But others,including you,weren't so lucky,but I don't think you can avoid it.

I'm most certain,the developers do their best to make everybody happy.

All the machines I installed Feisty on had no trouble with the -16 kernel.

---

### Post by madscientist on 2007-05-31
When you say "previously compiled" that implies you had build kernel modules yourself.  Anything you built yourself you certainly can't expect Ubuntu to magically detect and rebuild.  I don't have any kernel modules I built myself (I use the restricted drivers package to get support for my nVidia graphics card, and I use the VMWare packages to get those modules) and I upgraded with no need to rebuild anything.  There ARE some stability issues with the new kernel which led me to drop back down again (and this is a big bummer, for sure) but everything worked.

If you're wondering why you have to recompile in the first place, that's just the way Linux works.  The kernel developers have a very different idea about how to do software development than most proprietary software companies.  If you want to understand their point of view, ask Google about "linux stable abi": this has been discussed over and over and over in various forms for the last 15 years.

If you wanted to provide us with a more precise list of the problems you had we might be able to give you some advice about ways you could avoid them in the future.  However, just posting a detail-free complaint about "half the system not working" doesn't help.  Well, maybe it helps you with your blood pressure :D

---

### Post by jackelmatador on 2007-06-06
Yah it was just a blood pressure thing.  My main problem was with a LAN card I have based on the et131x chipset.  Had to go back to the built in LAN search the forums redo my stuff then I was ok, just needed a place to rant after my wifes comment "I don't know why it takes so long"

---

### Post by Liakath on 2007-06-08
> **bulldog said:**
> Yep it's a lot of work.

Some times,when you have bad luck,this kind of things happen.
I,for myself didn't had any trouble with the upgrade,and I think I'm not the only one.
But others,including you,weren't so lucky,but I don't think you can avoid it.

I'm most certain,the developers do their best to make everybody happy.

I am one of those who was able to upgrade the kernel  2.6.20_2.6.20-16.28 without any hazzles and today I could upgrade to kernel 2.6.20_2.6.20-16.29 as was available on Repos along with NVIDIA working normally.
I have even added UBUNTUSTUDIO to my Feisty Fawn 7.04:)

---

