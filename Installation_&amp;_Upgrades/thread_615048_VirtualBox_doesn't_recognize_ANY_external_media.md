---
title: "VirtualBox doesn't recognize ANY external media"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by bokorpop on 2007-11-16
So I've got Win XP installed in my Virtualbox, and now I am trying to get files from my external hard drives and/or flash drives onto XP, only when I click on "my computer" they don't show up. When I plug in my flash drive, Ubuntu recognizes it just fine, but in my Virtualbox, it appears as if nothing was inserted. How to take care of this?

---

### Post by mendozaro on 2007-11-16
There is no way to use VirtualBox for external usb drives or as my knowledge goes no other device linked to usb. In fact VirtualBox has no support for usb.

Another problem you will encounter is that VirtualBox does not manage the shared folders corectly or atleast to say buggy. So when you will try to move files from VirtualBox to Linux (host) it will be buggy.

I stoped using VirtualBox exactly for this reasons.

BUT when this two issues will be sorted out VirtualBox will be a great option for running win programs in theyr native enviroment (except 3d cause VB designers stated that there will be now 3d support for VB ever... than again who knows?)

---

### Post by bokorpop on 2007-11-17
Alright then, how do I setup a "shared" folder between viirtualbox and linux so i can put files onto the Vbox?

Also, I've heard of people syncing itunes in virtualbox, so how does that work if it recognizes no usb devices?

---

### Post by kyphi on 2007-11-17
Of course you can access your USB devices in VirtualBox.

Look through your VitualBox Manual, all the instructions are there.

You can download it from the Innotek site at 

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

There is also a revised version of VB recently released.

---

### Post by bokorpop on 2007-11-17
I read the manual but still have no idea how to implement usb. Secion 3.7.6 talks about how to get USB support, and talks about a "USB" section of the settings window of the virtual machine. When I click on settings, however, I see no such "USB" section. I have the very  latest version of vbox too.

Any suggestions? I would really really hate to uninstall linux b/c I need a couple of windows programs(no, wine or substitute programs won't work). But I digress...

---

### Post by kyphi on 2007-11-18
> I would really really hate to uninstall linux b/c I need a couple of windows programs(no, wine or substitute programs won't work). But I digress...
Yes, you do.


I use VB 1.5.2 and that has a USB entry in Settings.  I really don't know what has gone wrong with your installation of VB.  I assume that you have installed your guest additions.

---

### Post by bokorpop on 2007-11-18
I am elated to say this problem is SOLVED.


The friggin problem was that I had VBox OSE installed instead of the regular version, and OSE has no USB support.

I'm sorry everyone and thanks for your help!

---

