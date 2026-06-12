---
title: "i686 Ubuntu iso"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by arealperson on 2014-10-19
I can't find a correct iso image for a dell i686, the x86-x64 will not work, the i386 will also not work
I downloaded this but it did not work.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  (I selected the 32 bit for less than 2gig mem.) It fails.

Could someone direct me to a valid i686 image for ubuntu ?

Thanks,

---

### Post by Vladlenin5000 on 2014-10-19
The x86 = i386 **is **the correct one and should work for any 32 or 64-bit system.
Please describe what isn't working so we can help you.

---

### Post by arealperson on 2014-10-19
I get this message...

"This kernel requires an x86-64 CPU, but only detected an *i686* CPU"

When I put the i386 disk in, it simply will not boot of the CD.

---

### Post by Vladlenin5000 on 2014-10-19
> **arealperson said:**
> "This kernel requires an x86-64 CPU, but only detected an *i686* CPU"
It's a 32-bit CPU therefore only a 32-bit OS can be installed. Such message is to be expected whenever you try to run a live session and/or install a 64-bit OS in a 32-bit system. You can run and install a 32-bit OS in a 64-bit system - actually most factory installed Windows are 32-bit regardless of the CPU architecture - but not the other way around.

> When I put the i386 disk in, it simply will not boot of the CD.
Then there's something wrong with that CD*.
- Check the MD5 of the downloaded ISO and if it matches then
- Burn using the proper settings of the burning software you're using - "burn image to disk" or similar - and at a low speed (recommended by many; personally I never had a problem and I always burn at the maximum speed). 
- Some reading: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

* If it's really a CD, not a DVD, then definitely there's something wrong. Since a long time ago Ubuntu ISOs DON'T fit in a CD. You must use a DVD or a a USB pendrive.

---

### Post by deadflowr on 2014-10-19
Could be the machine itself can't handle the kernel, being as the 32-bit kernel is pae enabled.
Far-fetched, perhaps, but maybe something.

It would probably be helpful to know the cpu, if possible.

---

### Post by mörgæs on 2014-10-20
If PAE were the problem we would have got an explicit message about it, but yes it would help to know the cpu details.

---

