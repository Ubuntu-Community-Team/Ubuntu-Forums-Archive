---
title: "GDM log into windows 98"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by acolic on 2006-07-26
Hi,

i have a duel boot desktop which has Ubuntu and Win 98 on it. On start up I can choose to boot into Win 98.

What I would like to do is set up the desktop so it is more user friendly for my daughter. I want here to log in with her username/password and then have it boot into win98. With my username/password I want it to boot Ubuntu.

There are just too many kids games for here that don't work on Linux. I tried wine but most did not work.

Thanks

Alex

---

### Post by cilynx on 2006-07-26
I'm sad to say that your best bet is probably going to be having the machine boot Win98 by default and you choose Ubuntu from the GRUB menu.  By the time you've got GDM running, you're way past the point that you can boot Win98.

---

### Post by acolic on 2006-07-26
I was afraid of that.

If I set it up to boot into Win 98 is there a hack that I can use to simplify it for me to boot into linux.

Something like if F1 is held down during boot have it go into Linux?

Thanks

Alex

---

### Post by jimmygoon on 2006-07-26
You can make it boot into win98 unless you press 'Esc' withing X number of seconds of a little prompt coming up... and then you could choose win98 or ubuntu...

Would that work?

---

### Post by cilynx on 2006-07-26
Back in the LILO days, I had LILO installed on a floppy that booted Linux.  The HD was setup to boot Windows.  That way, floppy in == Linux.  Floppy out == Windows.

Not sure if GRUB can install on a floppy or not.  Not sure if you have a floppy on your machine...maybe the same could be done w/ a cheap usb key?

---

### Post by jimmygoon on 2006-07-26
> **cilynx said:**
> Back in the LILO days, I had LILO installed on a floppy that booted Linux.  The HD was setup to boot Windows.  That way, floppy in == Linux.  Floppy out == Windows.

Not sure if GRUB can install on a floppy or not.  Not sure if you have a floppy on your machine...maybe the same could be done w/ a cheap usb key?

Actually thats a great idea... although I had another one too.... Remeber loadlin.... I vaguely do... I bet you could some how make it to when you signed in at the win98 login... a script would run to dump the win98 kernel (is there such) and then load the ubuntu kernel and start ubuntu.

But I don't know how to use loadlin ;)

---

### Post by cilynx on 2006-07-26
Autorunning loadlin is indeed an interesting idea.  I don't know how much a performance hit you take that way though.  If you're just looking at low-power games for your daughter, maybe running Win98 under vmware-server (free VM) under Ubuntu and having that autorun when she logs in....same idea, other direction.

---

### Post by acolic on 2006-07-27
Hi,

thanks for all the suggestions. Since my daughter uses the computer 75% of the time I just changed ubuntu to boot into win98by default.

I would have tried VMWare but I installed ubuntu on an old machine and I don't think the speed would have been there running Ubuntu and VMWare.

Alex

---

### Post by cptnapalm on 2006-07-27
I do remember one odd utility, many years ago, which was called Linux95 or something like that.  While in '95, with this installed, you double clicked the icon and it would do a reboot into Linux.

---

