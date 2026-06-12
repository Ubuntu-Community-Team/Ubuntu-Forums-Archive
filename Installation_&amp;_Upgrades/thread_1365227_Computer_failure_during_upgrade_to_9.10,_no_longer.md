---
title: "Computer failure during upgrade to 9.10, no longer responding"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by paulmmj on 2009-12-27
That sums it up, a Fijitsu Siemens laptop of mine failed during the upgrade due to overheating, and now it isn't responding to boot from CD. I'm not sure what to do, and I'm in need of assistance. Any help much appreciated!

---

### Post by paulmmj on 2009-12-27
You should note that I by not responding to the boot CD, I no longer receive the "Try Ubuntu Without Any Changes" screen, sorry for double posting!

---

### Post by MooPi on 2009-12-27
Let it sit over night and blow some canned air through it's vent. Try again tomorrow.

---

### Post by taurus on 2009-12-27
Have you looked at the BIOS to see which device is first in the boot order?

---

### Post by hansdown on 2009-12-27
Hi paulmmj.

**If** the problem is due to overheating, then you should look at a new machine.  

Not trying to be funny.

EDIT: 

What model are you using?

---

### Post by paulmmj on 2009-12-27
```
mountall: symbol lookup error: mountall: undefined symbol: udev_moniter_filter_add_match_susustem_devtype
init: mountall main process (711) terminated with statues 127
```

Well, it has been overnight. I left a fan blowing on it. As far as I can tell from it's BIOS, it'll go to CD first. It seems to "sit" on the CD, and then give up and go to hard drive. While if I pick "CD-ROM", it just "sits."

---

### Post by taurus on 2009-12-27
Can it boot from a USB thumbdrive?

---

### Post by paulmmj on 2009-12-27
> **hansdown said:**
> Hi paulmmj.

**If** the problem is due to overheating, then you should look at a new machine.  

Not trying to be funny.

EDIT: 

What model are you using?

Well, it's my grampa's old machine, and he wants to use it to try Ubuntu before switching his main computer, so as far as new ones, already there. It's all good, you're right, I think this is the first it's been used in a while...

It's called "Alimo D 7800" as far as I can tell.

EDIT:

> **taurus said:**
> Can it boot from a USB thumbdrive?

I'm not sure how to make one... I've got a working Ubuntu machine and a flash drive, I imagine those are the proper resources. Sorry for being a noob, but how does one go about make a live USB?

---

### Post by hansdown on 2009-12-27
Looking at the specs, it would be "difficult to get any **newer** operating system to work elegantly".

---

### Post by taurus on 2009-12-27
From a working Ubuntu machine, go into System -> Administration -> USB Startup Disk Creator.  Make sure you have already downloaded the ISO image to your machine first though.

---

