---
title: "Problems installing Ubuntu on new PC"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2007-12-19
I just bought a new barebones kit from TigerDirect and I can't get Ubuntu to install on it.  Here are the PC specs:

PC Chips motherboard, with integrated LAN, sound, video - NVIDIA MCP61 chipset
Seagate 500gb SATA drive

I've tried 7.10 live CD and 7.04 live CD.  Both get to a certain point then show garbage on the screen and lock up.  I've loaded 7.10 on this hard drive on another PC (i386), so I know the drive is good.  I've installed a different hard disk that has Windows 200 on it and was able to boot into it, so I know the system is ok.

How do I determine what it's getting hung up on and correct it?  If there are any messages or logs that would help diagnose this I'd be glad to post them.

Thanks,
Rich

---

### Post by timseal on 2007-12-19
It might be your graphics card.  Do you have the alternate install CD?  Try with that.

---

### Post by 64mgb on 2007-12-19
Alternate CD does not work either.  It gets 64 % through "installing additional components" then dies...the screen looks like it's repeating the "installing additional components" message over and over.

Rich

---

### Post by xeth_delta on 2007-12-19
> **64mgb said:**
> Alternate CD does not work either.  It gets 64 % through "installing additional components" then dies...the screen looks like it's repeating the "installing additional components" message over and over.

Rich

What speed did you use to burn the CDs? Many times high speeds produce problems. Try something below 4x, then check the integrity of the burnt CD.

Also, it might be a good idea to check if the downloaded image is corrupted.

---

### Post by 64mgb on 2007-12-19
Woo hoo!  Success!  After burning a new CD at 8x (which was the lowest my software/cd/cd burner would allow) and getting the same results, it dawned on me that the CD ROM drive I was using was just dragged off the shelf and was quite old.  So I swapped one out of another machine and...voila!

Thanks for all the input!

Rich

---

### Post by xeth_delta on 2007-12-20
> **64mgb said:**
> Woo hoo!  Success!  After burning a new CD at 8x (which was the lowest my software/cd/cd burner would allow) and getting the same results, it dawned on me that the CD ROM drive I was using was just dragged off the shelf and was quite old.  So I swapped one out of another machine and...voila!

Thanks for all the input!

Rich

Great! I have to admit I am surprised at how many installation problems have a root in how the CD is burnt.

Good luck,
Xeth

---

### Post by 64mgb on 2007-12-20
> **xeth_delta said:**
> Great! I have to admit I am surprised at how many installation problems have a root in how the CD is burnt.

Good luck,
Xeth

Well, in this case it wasn't a problem with how the CD was burned, but a problem with the drive I was using to try read it with.  But similar results!

Thanks again!

Rich

---

