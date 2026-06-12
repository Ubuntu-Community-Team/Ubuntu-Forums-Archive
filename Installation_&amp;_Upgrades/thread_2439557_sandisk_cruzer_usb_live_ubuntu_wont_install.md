---
title: "sandisk cruzer usb live ubuntu wont install"
date: 2020-03-29
forum: Installation &amp; Upgrades
---

### Post by kingofswords on 2020-03-29
right I am sick to the back teeth of this as I've spent all weekend trying to install Ubuntu in an solid state drive .
after about 6 tries with Rufus, universal USB installer etc.
someone please tell me how to get it working,I've tried on normal HDD with same error message... syslinus 4.07 ....... ERROR :No configuration file found No DEFAULT or UI configuration directive found! boot:
any ideas?

---

### Post by ajgreeny on 2020-03-29
It sounds as if your .iso archive file was probably corrupt in some way.  When you downloaded it did you check the hashes to make sure it was good?
See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by kingofswords on 2020-03-29
> **ajgreeny said:**
> It sounds as if your .iso archive file was probably corrupt in some way.  When you downloaded it did you check the hashes to make sure it was good?
See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

i didnt but have tried various versions of linux with same result , all made from windows. i dont know if that makes a difference.

---

### Post by ajgreeny on 2020-03-29
What filesystem is on the USB install disk? It needs to be fat32.

What version of Ubuntu are you trying to install?
All instances of that error that I can find point to the use of very old .iso files such as 10.04

---

### Post by kingofswords on 2020-03-29
its fat32 and mint 19 xfce 64bit v2.

although ive tried with version 18 aswell.

---

### Post by QIII on 2020-03-29
So, you are asking about Mint, not Ubuntu?

---

### Post by yancek on 2020-03-30
The most likely source of your problem was pointed out in the first response post above.  You always need to verify the download as getting an iso file that large from the Ubuntu servers to your computer gives ample opportunity for corruption.  Posting some info on your hardware might be useful.

---

### Post by slickymaster on 2020-03-30
*Thread moved to **Installation & Upgrades**.*

---

