---
title: "What happened to easily creating partitions in 7.10?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by volksolwagen57 on 2007-11-03
In 7.04 there was a neat side scroll bar that you could use to manually partition ONE hard drive. I wouldn't be making this post to ask how to do something I once knew how to do. Intuitive user menu's just went out the door for a more cryptic, more technical install process. Isn't that counter-productive? Anyway, I can't figure out how to add a partition to an already existing windows partition. I've got a 500gb hard drive and I want 350gb to be used for ubuntu. What's the big deal? Will I have to install 7.04 then upgrade? Thanks for your response in advance.

---

### Post by mikewhatever on 2007-11-03
Everything in the installation process looks the same as in 7.04. What are the options you do get to edit partitions?

---

### Post by volksolwagen57 on 2007-11-03
For one, there is no longer the scroll bar that I can use to configure how much space I can use for partition. Then there is no way I can just input an integer and press enter. It's not easy. Instead I have to manually create an ext3 partition and creat a root "/." This would be no problem. I get it. The only thing I don't get is that, to me, there is no way to just partition a SECTION of the partition as a whole (the whole hard drive). I don't want to reformat the whole drive to ext3. I couln't figure out how to make an hda/sda2. Only the hda/sda1 can be modified completely. What gives?

---

### Post by bluepowder7 on 2007-11-03
to me, the gnome partition editor in 7.10 works basically the same as in 7.04  you can resize any parition by editing it and pulling the left / right ends of the box.

i suppose you can delete an existing partition, and then create two new partitions in its place - the first 150gig being the same type as what the whole thing was (like NTSF), and making the remaining 350gig as an ext2 or ext3 partition.  mind you, i haven't tried this myself, but if you just redo the start-end points and don't format the newly remade NTFS partition, i would ASSUME that the data on there is still relatively secure?  unless it was fragmented all over the place and chunks of it were in the 350gig section...

just a thought...

---

### Post by volksolwagen57 on 2007-11-04
I found the problem- the reason why my partition editors weren't working. I tried burning gparted on a bootable disc and found that I have "physical damage" to my hard drive. I should be getting a replacement next week. Thanks for all your help.

---

