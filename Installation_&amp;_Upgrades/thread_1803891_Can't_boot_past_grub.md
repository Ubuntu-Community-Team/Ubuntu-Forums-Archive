---
title: "Can't boot past grub"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2011-07-14
Hi,
My laptop sustained an injury and since the fall, it cannot progress past grub.  The grub menu appears, but regardless of what option is chosen, the machine reboots (exception: memtest works fine).
Any suggestions out there on what to do to save my laptop?
Thanks

---

### Post by tommcd on 2011-07-14
Try running Ubuntu from the live CD.
If the laptop runs ok from the live CD, then try reinstalling Ubuntu to the MBR of the hard drive like this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
If this does not help, you will have to consider the possibility that the laptop's hard drive may be damaged.

---

### Post by kacheng on 2011-07-14
Thanks,

I'll have to download and create a LiveCD or USB key - I usually used that laptop for that work.

Is it typical for the MBR to sustain damage in a fall?

---

### Post by tommcd on 2011-07-15
> **kacheng said:**
> 
Is it typical for the MBR to sustain damage in a fall?
Well, the hard drive can easily be damaged during a fall.
Was the laptop on and running during the fall?
In any case, at this point you have nothing to loose by trying to run Ubuntu from the live CD and or reinstalling grub.

---

### Post by Mark Phelps on 2011-07-15
Unless your laptop was one of the "ruggedized" versions (i.e., Panasonic ToughBook), that is designed to take abuse, the filesystem was almost certainly corrupted with the laptop fall.

Just how much damage was done to the hard drive is uncertain.

If you can find out the make and model of the hard drive, you should go to the manufacturer's website, and if they have a utility for examining the health of the drive, download that and run it.  They will typically need the log from that utility when deciding on warranty replacement.

---

