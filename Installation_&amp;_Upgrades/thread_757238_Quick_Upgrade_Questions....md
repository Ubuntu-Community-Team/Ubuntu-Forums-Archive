---
title: "Quick Upgrade Questions..."
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Literati on 2008-04-16
Hi all, I'm a new Ubuntu user, and have a moderate understanding of how everything works, and as Hardy is coming up in just a few days, I'll be upgrading for the first time then, so I just have a few questions.

I have two HDDs. An 80G Boot Drive, and a 400GB /home/ drive.
I know this is the 'best' setup you can have but I want to know what will be affected.

The way I see it, Wubi will walk me through formatting my 80GB drive, and will leave my 400GB /home/ drive again correct?

Will all the programs I have installed on my computer be gone, or are they stored on the 400GB drive?

Will I need to re-mount my 400GB drive as the /home/ drive once I upgrade to Hardy?

And to install and format my 80GB, you'd suggest to switch the BIOS to switch from the Live CD and then install it? Or just run it from inside Ubuntu already, or what?

---

### Post by dstew on 2008-04-16
Do you have Windows on your computer? I thought Wubi was a Windows program for installing Ubuntu.

If you already have Ubuntu, then you have at least a root file system. Is that what you are referring to as your Boot Drive? You might want to leave your current Ubuntu system on there, in case Hardy has problems. In that case, you could shrink your current Ubuntu partition, and create a new root partition for Hardy out of the unallocated space.

Your installed programs are in the root file system, and your personal files and configurations files are in your /home. So, if you delete the old root file system, you will lose your installed programs. But, they most likely would not work in Hardy anyway (new kernel) so trying to save them would not make sense. Better just to install the new versions into Hardy.

It is best to use a Live CD and do a new install.

---

### Post by Literati on 2008-04-17
Oop. My bad on Wubi. No I don't dual boot (Ubuntu only here!)

Yes I mean root.
So I'll still install onto the 80GB and shrink the partition there (and then dump it comepletely when I know Hardy's working fine?)

I'm kind of glad you say that my installed programs will go away (That includes the library files too right?) I installed a lot of programs before finding ones that I liked, so I'm sure I have some crap floating around that I no longer need. Now I can be selective :) 

Thanks for the information! :)

---

### Post by dstew on 2008-04-17
> So I'll still install onto the 80GB and shrink the partition there (and then dump it comepletely when I know Hardy's working fine?)That sounds like the most reasonable plan. Good luck.

---

