---
title: "Vista CD won't boot"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by dgg on 2007-10-25
Ok, so I do have Ubuntu 7.10 and had it for a few days.

But I want Vista because of gaming and supported programs, like the adobe CS3 package.

I have two seperate hard drives, one is 300GB and the other is 500GB.

So as said I have Ubuntu installed on my 300GB, and I want to install Vista on the other which shouldn't be much of a problem... If the cd would boot.


The BIOS is set to have the CD to boot, and the CD arrived today so there is no problems with it.
But when it says it will boot form the cd it's just blank... It just tells me it's going to boot it, then after 2-5 minutes it gives up and boots Linux.

Anyone know what the problem is?
If it for any weird reason should help: It is the Windows Vista Home Premium version.

---

### Post by dgg on 2007-10-25
Help? :/

---

### Post by orange2k on 2007-10-25
Doesn`t Vista come on a DVD?

---

### Post by dgg on 2007-10-25
> **orange2k said:**
> Doesn`t Vista come on a DVD?

I don't know, but my cd drive plays DVD cd's.
I even checked right now to be sure.
Also says "CD-RW/DVD±RW Drive" in the computer window.

So that's not the problem.

It just won't start when I start up the pc.
And when I try to open the cd when logged in on my Linux it says "There is probably no media in the drive"

---

### Post by Doomguy0505 on 2007-10-25
Hmm, my friend had this problem too, maybe it is an upgrade only disk? If you are dual booting then your supposed to install windows first because of the MBR

---

### Post by dgg on 2007-10-25
> **Doomguy0505 said:**
> Hmm, my friend had this problem too, maybe it is an upgrade only disk? If you are dual booting then your supposed to install windows first because of the MBR

Hmm, not an upgrade, it only says it includes the possibility to upgrade (reffering to what it says on the cd)

Well, I don't know if it's exactly dual booting or not when you are installing them on different hard disks.
But if it is, then there is my problem.

But how do I un-install the Ubuntu when all I got is a vista cd, an Ubuntu cd and one empty hard disk (nothing on) and one hard disk with Ubuntu?

---

### Post by cwj88 on 2007-10-25
Is there something wrong with the DVD its self?  Maybe you could try it on another machine

---

### Post by dgg on 2007-10-25
Hmm, yea. My dad just tried on some other computers.
They didn't want to boot it either.

So we are assuming it is a upgrade cd, even though it doesn't state so anywhere.

So I'll install XP and then upgrade it into Vista.
So much work, for something so dumb. :)

---

### Post by mrfelker on 2007-10-25
Vista - or any other Windozes will only boot off the first hard drive and off the MBR as well.
So you will need to make sure that in the BIOS the disk with Vista is recognized as the first hard drive.  Ubuntu however boots using GRUB - which if installed as well to the MBR OR any partition you make bootable (last item for a new partition install.  Installing to the MBR will overwrite the Windoze MBR and allow a dual boot system.  Ubuntu will "see" the Windozes installation.  The general rule is to install the oldest or most brain dead OS first.

---

