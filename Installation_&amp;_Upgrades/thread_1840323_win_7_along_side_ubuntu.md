---
title: "win 7 along side ubuntu"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by nego0 on 2011-09-07
Hi 
i found  an old 40gig hard disk laying around 
so i wanted to install win7 on it along side my already installed ubuntu 11.04
so started the install untill you get to your drives.
I can't install on that 40gig drive 
setup says that it can't create a new filesystem or find existing filesystems

Couldn't find anything about it on the forum 
only if you use 1 hard disk and partion it with gparted ect...
But i'm using 2 disks so i think i don't need 2 do that


Thnx

---

### Post by YesWeCan on 2011-09-07
Hi. Is this 40GB an EIDE drive? What type is your Ubuntu drive?
So Windows doesnt see it. Does it show up in the bios?
If it is EIDE have you checked the jumpers?
Can you set the 40GB to be first in  boot priority?
What if you disconnect the Ubuntu drive before installing Windows?

---

### Post by nipunshakya on 2011-09-08
> **nego0 said:**
> Hi 
i found  an old 40gig hard disk laying around 
so i wanted to install win7 on it along side my already installed ubuntu 11.04
so started the install untill you get to your drives.
I can't install on that 40gig drive 
setup says that it can't create a new filesystem or find existing filesystems

Couldn't find anything about it on the forum 
only if you use 1 hard disk and partion it with gparted ect...
But i'm using 2 disks so i think i don't need 2 do that


Thnx

I would suggest you to unplug the drive that has ubuntu installed in it...then restart your pc and start installation of windows......
OR, you can once run gparted from your liveCD and then format the 40gig with NTFS partition and then begin your installation with your windows.... 
i guess you should unplug your ubuntu drive for installation in both suggestions...

here's a similar suggestion link..but it has one hdd involved, but you can unplug one of your drives and try it

[http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu)


Goodluck.
Regards,WinuxUser

---

### Post by Mark Phelps on 2011-09-08
My own experience sides with others -- that claim that having each OS on its own physical drive is the best way to go.

That allows each drive to be independently bootable -- which comes in real handy if you need to do filesystem repairs.

It also prevents the problem of overwriting MBRs and accidentally overwriting existing filesystems or corrupting them.

---

### Post by nego0 on 2011-09-08
Ok Thnx guys
gonna try that

---

### Post by nego0 on 2011-09-08
> **Mark Phelps said:**
> My own experience sides with others -- that claim that having each OS on its own physical drive is the best way to go.

That allows each drive to be independently bootable -- which comes in real handy if you need to do filesystem repairs.

It also prevents the problem of overwriting MBRs and accidentally overwriting existing filesystems or corrupting them.

I've installed win7 on the other drive
but the only problem now is that it automaticly starts ubuntu
do you need to do that in the bios or something?

Thnx

---

### Post by oldfred on 2011-09-08
Ubuntu should find the windows install with this:
```

sudo update-grub
```

---

### Post by nego0 on 2011-09-08
Got it working with startup manager 
Thnx

---

