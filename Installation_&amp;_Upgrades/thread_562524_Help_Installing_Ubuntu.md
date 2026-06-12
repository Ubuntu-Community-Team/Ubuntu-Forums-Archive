---
title: "Help Installing Ubuntu"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by REXXER on 2007-09-28
Hi,

I have an HP Pavilion dv2000 CTO notebook (1.6ghz dual-core processor, 2gigs ram, and an nvidia geforce go 6150 gfx card) and when i try to install Ubuntu 7.04 x64 (the alternate verion, cause the normal version didn't work either, same problem)  it has an error when copying the file **///cdrom/pool/main/n/ncurses/libncurses5_5.5-2ubuntu1_amd64.deb**, it says it was corrupt. But when i run the cd check it has no preblems. PLZ HELP!!

Thank You Very Much,
Rexxer

---

### Post by rsambuca on 2007-09-28
If that is the core duo model, then it is 32bit architecture, so the 64bit OS won't work.

---

### Post by REXXER on 2007-09-28
no its core 2 duo, and im almost positive it is 64-bit

---

### Post by rsambuca on 2007-09-28
Ah, OK.  Yes, the core 2 Duo is definitely 64 bit.

---

### Post by rsambuca on 2007-09-28
Did you check the md5sums prior to burning?

---

### Post by REXXER on 2007-09-28
no, how do i do that?

---

### Post by rsambuca on 2007-09-28
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, make sure you burn your installation cd's at a very low speed to avoid single bit errors.

---

### Post by REXXER on 2007-09-28
i just compared them, and they are the same

ill try burning at a lower speed

---

### Post by rsambuca on 2007-09-28
> **REXXER said:**
> ill try burning at a lower speed

For reasons I don't understand, that often cures installation problems, despite what the CD Integrity Check says.

---

