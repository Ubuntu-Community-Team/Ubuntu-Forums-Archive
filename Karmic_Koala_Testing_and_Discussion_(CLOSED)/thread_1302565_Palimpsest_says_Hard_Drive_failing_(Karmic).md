---
title: "Palimpsest says Hard Drive failing (Karmic)"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by noob555 on 2009-10-27
Palimpsest disk utility has been telling me that my hard drive is failing ever since I upgraded to Karmic.  Specifically, it says that I have numerous reallocated sectors and several more awaiting reallocation.  Please see attached screenshots for the specific error messages.

After searching the forum, it is unclear to me whether or not this is just a bug.  Should I be worried?

---

### Post by alphaniner on 2009-10-27
There's a number of tools you can use to determine if your HDD is bad.  Some manufacturers offer bootable tools that can scan drives for bad sectors.  I'm guessing your drive is a Hitachi.  Go [here]("http://www.hitachigst.com/hdd/support/download.htm") to download their tools.  I have used their bootable utility before, it's good.  There's also the linux tool **badblocks**.

Presumably the data Palimpsest is using is coming from **smartctl**, or at least **smartctl** queries the same SMART Attributes.  You could try running **smartctl** from the command line to see if it returns the same results.

---

### Post by raprap30 on 2009-10-27
Offtopic: What theme is that?

---

### Post by noob555 on 2009-10-27
> **alphaniner said:**
> There's a number of tools you can use to determine if your HDD is bad.  Some manufacturers offer bootable tools that can scan drives for bad sectors.  I'm guessing your drive is a Hitachi.  Go [here]("http://www.hitachigst.com/hdd/support/download.htm") to download their tools.  I have used their bootable utility before, it's good.  There's also the linux tool **badblocks**.

Presumably the data Palimpsest is using is coming from **smartctl**, or at least **smartctl** queries the same SMART Attributes.  You could try running **smartctl** from the command line to see if it returns the same results.

Thanks.  It does look like a Hitachi drive.  I presume you mean the Drive Fitness Test mentioned on Hitachi's website.  Should I use the Binary Diskette or CD Image to create the bootable app?

---

### Post by noob555 on 2009-10-27
> **raprap30 said:**
> Offtopic: What theme is that?

Not sure that it actually is a theme.  I've downloaded a few in the past, but as I recall I was just playing around with the colors one day and ended up with this particular scheme.  I like it because it's dark, but easy on the eyes.

---

### Post by alphaniner on 2009-10-27
> **noob555 said:**
> Thanks.  It does look like a Hitachi drive.  I presume you mean the Drive Fitness Test mentioned on Hitachi's website.  Should I use the Binary Diskette or CD Image to create the bootable app?

Yup, Drive Fitness Test is the one.  I would favor the 'Binary Diskette' if you have a floppy drive.  It'll be faster to create, and you won't waste a CD-R.  Otherwise, use the CD Image (if you have a CD burner).  If you have neither, try badblocks.

---

