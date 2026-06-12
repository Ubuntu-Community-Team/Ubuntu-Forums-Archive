---
title: "Preemptive preservation of grub during xp install."
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Johndo1 on 2010-03-24
I have, in the past, installed windows along side my main OS, Ubuntu. Every time I install windows, the grub ends up disappearing and I have always had to re-install Ubuntu to get the grub back. I have a lot of files and it would take a while to back up so would anyone be so kind as to tell me if there is a way to preemptively preserve grub so it doesn't disappear after I install XP on half of my hard drive? 

thanks.

---

### Post by stlsaint on 2010-03-24
Installing windows on the system will continue to do this whenever you install windows AFTER xp. The only thing i could think of to circumvent this is to maybe give grub its own partition to prevent it from being written on but even at the i still believe that windows will take over boot loading as it writes to the MBR.

---

### Post by Mark Phelps on 2010-03-24
> **Johndo1 said:**
> ... so would anyone be so kind as to tell me if there is a way to preemptively preserve grub so it doesn't disappear after I install XP on half of my hard drive? 

thanks.

Actually, GRUB does not disappear, at least, not entirely.  The files are were written to the Linux partition remain intact.  

What does get overwritten is the small amount of stuff written to the MBR -- and there's no way around that.

You will have to reinstall GRUB to put its entries back into the MBR.

---

### Post by Johndo1 on 2010-03-24
Would there happen to be an easy way to reinstall grub, and make it point to both ubuntu and windows?

---

### Post by mikewhatever on 2010-03-24
Why not just backup the MBR and restore it after you are done with installing Windows?
[http://members.iinet.net.au/~herman546/p13.html#mbr_dd](http://members.iinet.net.au/~herman546/p13.html#mbr_dd)

---

