---
title: "I miss ubuntu"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by p1r0 on 2007-04-04
I miss my ubuntu. I'm using Mandriva and I just hate it. 
The problem is that it's imposible to install Ubuntu becaouse it doesn't work on my Intel desktop board. I got mandriva installed using the generic-ide option, but ubuntu doesn't have the generic ide drivers built into the kernel so it won't work that way.

I'm not asking for a solution, just sharing with you  all the way I feel. Ubuntu was the first linux I used as a main OS on my box (I've used Red Hat in the past) and I miss it.

Is there a place to send a formal request for future versions of Ubuntu to be complatible with the new Intel Desktop boards?

I hate to be forced into a distro I don't liko or even worse Windows. I say this because the same old windows xp works just fine on this board.

Best regards to all the comunity
p1r0

---

### Post by shotgunefx on 2007-04-04
Couldn't you just compile a kernel with that driver???

---

### Post by p1r0 on 2007-04-05
Can I do that before installing???
Because I need the kernel of the live cd (or the text installer) to have that driver.

---

### Post by shotgunefx on 2007-04-05
> **p1r0 said:**
> Can I do that before installing???
Because I need the kernel of the live cd (or the text installer) to have that driver.

D'oh, a very good point. A bit of a chicken and egg problem. I'm sure it could be done, just not exactly sure how to go about it.

Bear with me, is the generic-ide option a driver, a kernel patch???

Here's a link on customizing the live CD.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Another thing that might work is installing to a usb card or similar, and build the support you need, then copy it over to the HDD.

---

### Post by p1r0 on 2007-04-06
I'm not an expert on the subject and I got the help from Intel. But the option all-generic-ide (or something like that) tells the installation to load the generic ide driver. But the thing is that if it is not compiled in the kernel it can't rea the cd-rom to load it. When I installed mandriva with that option I then had to edit the lilo (the bootloader) to add the all-generic-ide option because if not it wouldn't load the os (the Intel guys missed that one).

But I've solved my problem (or made it worse I don't know yet) yesterday night I installed Ubutu 7.04 Beta and it works just fine with my mobo.

p1r0

---

