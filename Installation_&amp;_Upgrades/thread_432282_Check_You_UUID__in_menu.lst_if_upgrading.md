---
title: "Check You UUID  in menu.lst if upgrading"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by zdude on 2007-05-03
I noticed a horrible slow-down and near lock up in feisty last night and noticed my hard disk was trashing for sometime. I also noticed that I had NO swap usage but near 100% ram usage - so I knew I had a swap problem. Turns out the the UUIDs in my menu.lst AND fstab did not match my drive uuids (use "sudo vol_id /dev/hdax"). Once I fixed this everything was smooth as butter again.  
[rant on]Whoever in kernel programming that put these UUIDs in should be kicked hard in the nuts! This looks like something some dumbass M$ programmer put in the kernel. Why would you guys do this???? I hated GUIDs when I programmed MS crap and here it is again. What's wrong with  /dev/hda1? or /dev/hda5 in the fstab/menu.lst? 
[/rant off] 
Thought I give others a heads up before this kicks you in the groin unexpectedly.

---

### Post by undecidable on 2007-05-04
Now don't be too harsh ;-)

[/gentle on] uuids take a few minutes to get used to,
but they make systems much more robust.
eg every time you change partitions your device nos (eg /dev/hda2) will change
but not uuids.  

Adding/ removing hdds can cause device nos to change but not uuids.

Some laptops with basy or slots for hdd or dvd will also cause device nos to change,
but again not uuids.[/gentle off]

---

### Post by zdude on 2007-05-04
I understand the reason, esp. for laptops but the UUIDs in my fstab and menu.lst, matched each other, they did not match the actual vol_ids. Somewhere there was a change and it wasn't from me changing my drives - this is a desktop computer. The computer still booted, so I did not realize there was a problem but the swap would not mount, which I did not notice until I maxed out phy. ram. Sorry about the rant but I hate GUIDs after using them in M$ programming, they were a nightmare and I just freaked when I saw them raise their ugly head in my Linux install.

---

### Post by undecidable on 2007-05-04
Yeah, a possible error in a particular user config is different from a design decision.  

My point really was that you have a group of people who are making decisions that they believe will add to stability or functionality for us as users (rather than for Hollywood or to strengthen their own monopoly).  They are making these decisions honestly and in good faith.   Even when they might be wrong (or right but we disagree), or when the decision is a good one but there is a bug in implementation,  they really do not deserve abuse.

Goodness knows, there are enough people in the world who genuinely deserve our precious and excellently crafted abuse (ethnic cleansers, environmental louts, patent trolls,...) without scattering it where it does not belong.

---

