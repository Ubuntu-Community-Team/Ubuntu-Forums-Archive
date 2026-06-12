---
title: "Ubuntu 20.04 installation question."
date: 2020-08-09
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2020-08-09
Please see photographs of screen here: [https://photos.app.goo.gl/uTuQ2CjamVq8Z63K9]("https://photos.app.goo.gl/uTuQ2CjamVq8Z63K9") 
And here's the disk management screen from Windows: [https://photos.app.goo.gl/sg7rHZWM9aeZBSRM8]("https://photos.app.goo.gl/sg7rHZWM9aeZBSRM8")

This is 6GB RAM quad-core Win 10 machine I'm installing 20.04 on. I created @100gb of unallocated space in the main Windows partition while booted to Windows, but it's not clear to me that the default choice "Install Ubuntu alongside Windows boot manager" will install Ubuntu in that space. 

Would selecting the "free space" as shown in the second photo and clicking "Install now" prompt me for things like "where do you want to do the swap"? Because I've never been able to find anything that gives me to understand how I should do those "Something else" installs. 

Do I need to revisit the Windows partition manager and move the unallocated space to the "end" of the hard disk or something like that? Or will the default choice (alongside boot manager) use that 100 gb of unallocated space I created with swap, the grub boot loader, etc. 

I'm fine with doing the "something else" step-by-step with photographs of the screen posted here for further instruction. 

Thanks, 
Scott

---

### Post by guiverc on 2020-08-10
Ubuntu 20.04 LTS (and 18.04 LTS too) will use swap partitions, but by default will create a *swapfile* which is easier to change size of, so no it won't ask you where you want swap (but you can still create swap partition yourself if wanted; I still use them).

Me I'd use a *something-else* install as I like to specify where I create partitions (click on "+" to create partitions, "-" to remove partitions..)  

 I would expect "*install alongside*" to do exactly what you want, and I've done that install already today (QA-test install for 18.04.5), but if you're unsure, I'd use a partition tool to create a partition you want to use, and just select it using the *something-else* install.  It's what I always do when ensure (but always backup first, mistakes are just too easy to make!)

Where the free space is won't matter, though if your partition table isn't GPT, only 4 partitions can exist on an MBR partition table, so creation of new partitions won't be possible (I count 5 already so you'll be on GPT I bet).

---

