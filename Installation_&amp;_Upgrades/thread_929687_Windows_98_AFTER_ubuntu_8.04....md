---
title: "Windows 98 AFTER ubuntu 8.04..."
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by finalrequiem on 2008-09-25
I wanted to install Windows 98 on a small (9 gig) partition because I want to use it for some older software that doesn't seem to like Wine on my notebook.  I used gparted and created a fat32 partition after my main linux partition.  I then used the Win98 setup disk to boot the computer and started the setup.  Here is where I hit a snag:  It says "Drive C: is not a format that Win98 can use.  Would you like Windows to format the drive?".  Not sure exactly where I should go next...  Is it not recognizing the fat32 partition?  Is fat32 what I should be using? I couldn't find anything addressing that specific problem.  Thanks!

---

### Post by wpshooter on 2008-09-25
It is my understanding that ideally, Windows O/S should be installed prior to installing Linux.

I don't know that it will do you any good but have you tried looking at the partitioning with a WIN98SE bootable diskette / fdisk ?

Perhaps FDISK then FORMAT from the WIN98SE bootable diskette.

Might want to make sure that you have a backup of any important stuff in Linux before you try any of this.

---

### Post by finalrequiem on 2008-09-25
That is the idea I've gotten as well... Anyone else know how it can be done the way I want to do it?

---

### Post by oilchangeguy on 2008-09-25
> **finalrequiem said:**
> That is the idea I've gotten as well... Anyone else know how it can be done the way I want to do it?

run it as a virtual machine from within ubuntu.

---

### Post by finalrequiem on 2008-09-25
Maybe a dumb question but how different is that than using something like Wine?  Does it involve a separate partition (I'm assuming no...)?  Is it actually running Win98 or an emulated form?  Thanks...

---

### Post by oilchangeguy on 2008-09-25
> **finalrequiem said:**
> Maybe a dumb question but how different is that than using something like Wine?  Does it involve a separate partition (I'm assuming no...)?  Is it actually running Win98 or an emulated form?  Thanks...

no, not a dumb question. when using a virtual machine, you actually install the operating system (guest) as a program in the host operating system. you can then click on the vm program and run the os as you would if it were a stand alone install.

---

### Post by finalrequiem on 2008-09-25
So, when running Win9X as a VM, how does it handle installing and storing Win9X programs?  Does it create some sort of virtual fat32 storage or does it just use the linux partition?  Or is it easier just to tell me "It just does!"

---

### Post by oilchangeguy on 2008-09-25
> **finalrequiem said:**
> So, when running Win9X as a VM, how does it handle installing and storing Win9X programs?  Does it create some sort of virtual fat32 storage or does it just use the linux partition?  Or is it easier just to tell me "It just does!"

you run it as you would normally, install programs, etc. yes, "it just does".

---

### Post by finalrequiem on 2008-09-25
Word... I'll give that a shot.  Now to figure out how to do it...

---

### Post by oilchangeguy on 2008-09-25
> **finalrequiem said:**
> Word... I'll give that a shot.  Now to figure out how to do it...

locate virtual box. it should be in add/remove. or synaptic package manager.

---

### Post by finalrequiem on 2008-09-25
Just grabbed it.  Wasn't sure if that was a good program but took the plunge.  Thanks for the advice.

---

