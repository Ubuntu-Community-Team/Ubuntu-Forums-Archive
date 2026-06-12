---
title: "Dual-booting Windows 7 and Ubuntu 9.10?"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by CoffeeCoder on 2010-03-21
Hi everyone, 

I absolutely love Ubuntu. I was finally able to try out a Live CD (of the beta of Lucid Lynx) the other day and now wish to install Ubuntu 9.10 onto my laptop (which I'll later upgrade to 10.04 when it comes out in late April).

I'm just a little confused when it comes to the dual-booting process. I'll admit I'm very scared about the whole "creating separate partitions" thing, and thus I think I'll just install Ubuntu alongside Windows as detailed in [[COLOR="Blue"]this[/COLOR]]("http://www.psychocats.net/ubuntu/wubi") tutorial. However, I want to get the experts' opinions before I do anything drastic, and also ask a couple of questions. 

First, will I be able to turn this install into a full-fledged partition later on? Or will I have to choose to do that now if it's the better thing to do?

Second, if I want to officially turn the install into its own partition, what will I have to do to resize my Win7 partition? I've looked into it, and it sounds difficult and a tad frustrating since Microsoft decided to keep the MFT nudged tightly in one place, limiting the amount of space you can resize the partition to. I understand how to do it, it just sounds frustrating/scary. I guess I'm really asking; do you guys know of safe software that will allow me to resize the Win7 partition easily and safely? Then I can follow the official Ubuntu help guide tutorial about it...

Alright, that's all I've got. Thanks to any and all who respond!

---

### Post by lsk3993 on 2010-03-21
Ok, now I am in no way an expert on Ubuntu or dual booting at all. In fact I am very new to Ubuntu and wouldn't be confident enough to use it if it wasn't for the helpful people here that I know I can turn to if I need help.
Still, I will try answer your question based on the little experience I have.

I have used Wubi before because it seems like the best choice for users who want to safely try out Ubuntu however I don't think it is advisable to use if you intend to use Ubuntu on the long run (someone correct me if I'm wrong here).
When I was using Ubuntu in Wubi before it wasn't as fast as it is now that I have made a proper install and I also encountered problems with the Grub bootloader due to it not really being a proper install I think...

I would say if you want to use Ubuntu for a long period of time then take the time to give it it's own proper partition. If you just want to test it, then use Wubi.

Also, I often rely on Ubuntu (either by Live CD or booting into it) to fix Windows screwups so I wouldn't feel very comfortable having Ubuntu being reliant on Windows...

---

### Post by CoffeeCoder on 2010-03-21
> **lsk3993 said:**
> I would say if you want to use Ubuntu for a long period of time then take the time to give it it's own proper partition. If you just want to test it, then use Wubi.

Also, I often rely on Ubuntu (either by Live CD or booting into it) to fix Windows screwups so I wouldn't feel very comfortable having Ubuntu being reliant on Windows...

I also wouldn't be very comfortable having it rely on Windows. I like the idea of having two separate, independent operating systems on my laptop. I don't want them to rely on each other. 

I already have tested Ubuntu with the Live CD I mentioned earlier, so I know I definitely want to install it. I'll look into giving everything its own partition. I think I can do it, it's just scary. :P

---

### Post by lsk3993 on 2010-03-21
> **Jeremy Gardner said:**
> I also wouldn't be very comfortable having it rely on Windows. I like the idea of having two separate, independent operating systems on my laptop. I don't want them to rely on each other. 

I already have tested Ubuntu with the Live CD I mentioned earlier, so I know I definitely want to install it. I'll look into giving everything its own partition. I think I can do it, it's just scary. :P
I'm not sure how useful this will be, but have a look at [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
Obviously skip the Windows install bit...
I'm sure if we give it time someone more knowledgeable than me will lend a hand though. They're good at that here :D

---

### Post by wilee-nilee on 2010-03-21
Wubi is not a along side install it is a pseudo virtual install inside of Windows and is good for trying Ubuntu out. People run into various problems with it being that it is attached to windows.

If you want to try out Ubuntu without changing anything a thumb-drive is a good way to go. You can install with the ISO running the thumb or a full install that leaves the thumb running like a full OS.

The dual-boot is easy in the end as the way most people end up. You just want the partition resizing done with the disk manager in W7, leaving you the open space for a install of Ubuntu alongside. The Wubi is a inside not alongside.

You could also down load the sun virtual machine if you have enough ram and try out Ubuntu in a real virtual this may be the easiest way to check it out and have it completely removable never touching the Boot Record.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Suns Virtual is really easy to use in MS.

The partitioning seems daunting until you have done it a few time, the W7 disk management though makes it quite easy you can have it tell you how small it will let you shrink a partition, and do it in a live virtual partitioning environment.

---

### Post by CoffeeCoder on 2010-03-21
> **lsk3993 said:**
> I'm not sure how useful this will be, but have a look at [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
Obviously skip the Windows install bit...
I'm sure if we give it time someone more knowledgeable than me will lend a hand though. They're good at that here :D

Thank you so much! That is exactly the kind of clear-cut tutorial I was looking for! :D

---

### Post by lsk3993 on 2010-03-21
> **Jeremy Gardner said:**
> Thank you so much! That is exactly the kind of clear-cut tutorial I was looking for! :D
Be sure to let us know how it goes and feel free to come back if you need any help with it ;)

---

### Post by Mark Phelps on 2010-03-21
Before you start jumping for joy ... you might notice that one of the things that tutorial says you must have before you start is a Vista (or Win7 if you're installing that) Installation DVD.

You DO have one, right??

I'm guessing you don't -- because most people do not.

So, if you're running Win7, the first thing to do is boot into Win7, type backup in the old start area, and use the builtin Win7 Repair CD function to create and burn a Win7 Repair CD.  That will come in handy later.

Also, do NOT use the Ubuntu installer to shrink the Win7 OS partition.  Do it in the Win7 Disk Management utility.  But leave the unallocated space as is and allow the Ubuntu installer to format it as needed.

Finally, would vote against using Wubi.  Lots of folks are having problems getting Wubi to work on Win7 installs.  Save yourself the grief and do a separate partition install.

---

### Post by CoffeeCoder on 2010-03-21
> **Mark Phelps said:**
> Before you start jumping for joy ... you might notice that one of the things that tutorial says you must have before you start is a Vista (or Win7 if you're installing that) Installation DVD.

You DO have one, right??

I'm guessing you don't -- because most people do not.

So, if you're running Win7, the first thing to do is boot into Win7, type backup in the old start area, and use the builtin Win7 Repair CD function to create and burn a Win7 Repair CD.  That will come in handy later.

Also, do NOT use the Ubuntu installer to shrink the Win7 OS partition.  Do it in the Win7 Disk Management utility.  But leave the unallocated space as is and allow the Ubuntu installer to format it as needed.

Finally, would vote against using Wubi.  Lots of folks are having problems getting Wubi to work on Win7 installs.  Save yourself the grief and do a separate partition install.

Yes, I do have Windows Installation/Restore DVDs (but I'll double-check to see if it has Installation Repair options; I imagine they do, but I'm not taking ANY chances!). I burned them immediately after purchasing my HP laptop a few months ago, and had to use them back in early January thanks to a stubborn virus (Happy New Year to me! :P ).

Also, that tutorial guides one through a Ubuntu/Windows dual-boot project, even if you already have Win7 installed. You just have to clean up your hard drive of old/unneeded files (which I've been doing the last hour or so), run a defrag/disk cleanup, then determine how much space you'll want for each OS based off of currently available space (and set aside an additional partition for sharing files between both OSes). I currently have 161GBs total, so if I divide that up by two, each OS will take up 80.5GB. If I divide it by three (for the file-sharing partition), that's a little over 53.6GB for each OS, which was pretty much my target. I may give Windows more room, though, because it will still be my primary OS for video editing. However, I plan to use Ubuntu for nearly everything else.

So now I have to go eat dinner, do a defrag/disk cleanup, restart my computer, divide my partitions up and install Ubuntu. Thanks for all the help so far guys, this is a great community. :)

---

### Post by CoffeeCoder on 2010-03-21
> So, if you're running Win7, the first thing to do is boot into Win7, type backup in the old start area, and use the builtin Win7 Repair CD function to create and burn a Win7 Repair CD. That will come in handy later.

Sorry, I meant to ask you to clarify what you meant by this in my last post. What do you mean by "old start area", and do you mean that I need to do that just to create standard recovery discs? If so, then I already have those and won't need to.

---

### Post by CoffeeCoder on 2010-03-21
Sorry for the triple-post guys. 

I successfully installed Ubuntu 9.10 on its own partition, and both Windows 7 and Ubuntu work without any problems whatsoever. 

Thank you guys for all of your help! I can't wait to explore Ubuntu's full potential. I look forward to being a part of this great community in the future. :D

---

