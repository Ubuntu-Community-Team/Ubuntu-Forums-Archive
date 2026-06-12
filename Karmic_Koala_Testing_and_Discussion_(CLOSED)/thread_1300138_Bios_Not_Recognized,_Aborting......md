---
title: "Bios Not Recognized, Aborting....."
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ted3929 on 2009-10-24
I've seen this discussed before but have never seen a solution posted.

I have Karmic on a Gateway UC7300 laptop.  When I boot I get the unrecognized BIOS warning along with an abort message but Karmic boots anyway.

Just a minor inconvenience but it seems it's taking another 5 to 10 seconds of boot time for this message.

Has anybody figured a resolution for this problem?  Appears to affect a wide variety of laptops, not just Gateway models.

Thanks:confused:

---

### Post by VMC on 2009-10-24
> **Ted3929 said:**
> I have Karmic on a Gateway UC7300 laptop.  When I boot I get the unrecognized BIOS warning along with an abort message but Karmic boots anyway.
Thanks:confused:

This is the first time I saw this error message. It's coming from grub2, correct?

I thought this [link]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") would help since they add success or failure to the machine used, but nothing about any notes to expand upon.

Googling, I found a patch for grub+196, what version grub is at the top of your grub menu screen? Should say beta4.

---

### Post by Ted3929 on 2009-10-25
That did it!  Hopefully it's that easy for everybody else.  Thanks!

---

