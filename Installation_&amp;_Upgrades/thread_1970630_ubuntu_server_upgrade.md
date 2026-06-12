---
title: "ubuntu server upgrade"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by regulardrake on 2012-05-01
I recently made a LAMP/Fileserver server with Ubuntu server 11.10, oh probably 3 or 4 months ago. I updated to 12.04 lastnight and everything went smoothly, but I noticed after the reboot the MOTD said i686. I thought wait a mintue didn't I install 64bit. So after scratching my head for a bit I remember having trouble installing from a USB drive, it keep failing around the 50% mark. So I gave up and tried burning the iso to a CD-R and I must of been a dumbass and burnt the 32bit that I used for my server at work instread of the 64bit one for home.

So now I am woundering is it worth wiping the drive again and reinstalling as a 64bit or just say screw it and leave it alone. So I was looking for anyone's input. Here are my specs of the PC. 

CPU - AMD Athlon 64 x2 Duel Core 5400+
Memory - 2Gigs (I don't plan on upgrading to more memeory. So that would be one reason to stay 32bit)
Motherboard - Sorry can't remember the model number, its an Asus board.

Thanks

---

### Post by lykwydchykyn on 2012-05-01
Not worth it, IMO.  In fact, at 2GB you might even see worse performance on 64 bit due to increased memory use.

If you were 4Gb+ and running lots of heavy stuff (virtualization, e.g.), then maybe.  Otherwise, stick with 32bit.

---

### Post by regulardrake on 2012-05-02
> **lykwydchykyn said:**
> Not worth it, IMO.  In fact, at 2GB you might even see worse performance on 64 bit due to increased memory use.

If you were 4Gb+ and running lots of heavy stuff (virtualization, e.g.), then maybe.  Otherwise, stick with 32bit.

Thanks man, that's the answer I was looking for.

---

