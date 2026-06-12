---
title: "MSI Wind Box DC100 wont suspend or hipernate - and wont boot after trying"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by theWasp9 on 2012-09-02
I just installed Ubuntu 12.04.1 LTS (danish) on a brand new MSI Wind Box (DC100). Everything works fine (after a couple of tries, where it wouldnt boot). But it wont start again after bringing it to hipernate. 

The power switch is flashing, and the hardware wakes up again after pressing it. But it doesnt boot or load an image. It just wakes up. The screen doesnt turn on either.

Anyone has any experience?

---

### Post by komasoftware on 2012-09-08
same here :(

---

### Post by komasoftware on 2012-09-08
I manage to boot the box by putting the USB back in with the install image. No other way to get out of hibernate/suspend status.

even a complete shutdown (disconnect power) does not help.. it remembers the state it was in, i reckon.

---

### Post by theWasp9 on 2012-09-08
I experienced the same, and couldn't even choose boot device - that is no boot at all. But after a couple of days switched of, it booted with the MSI bootloader.

Except from this problem, ubuntu seems to run alright on the machines (I sat up two identical).

---

### Post by komasoftware on 2012-09-08
this seems worth to try ... replacing suspend with userspace suspend : see 
[http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=854](http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=854)

didn't try yet though...

---

### Post by komasoftware on 2012-09-08
old post i notice now... not sure if still relevant.

---

