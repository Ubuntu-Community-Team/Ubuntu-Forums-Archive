---
title: "Install Windows without touching the MBR"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by fokuslee on 2007-04-20
How do you install windows without overwriting stage 0 of grub Which is already installed.  I really perfer not to restore grub after window wipes it out
better yet if someone knows how to dual boot windows xp and trixbox please let me know 
Thanks in advance



-Network+ is so gay CompTIA = Evil TestOut Makes crappy test prep
T.T

---

### Post by maxamillion on 2007-04-20
I am not going to say its impossible because I don't know for a fact, but I will say this: I have never heard of this being accomplished and I personally don't think you can tell windows not to touch the MBR but in the event you find a solution, please post it.

---

### Post by fokuslee on 2007-04-20
i correct myself stage 1 and 2 are both on grub root device not mbr 
so i guess the part of grub that is on mbr is stage 0 
maybe im wrong on that too.

---

### Post by jerseyman on 2007-04-20
You can solve this problem with SuperGrubDisk. Just install Windows normally and let it overwrite mbr. Then boot from SGD and it will fix and return the old grub back and you will be able to boot linux again. I have done this several times because i had re-install windows many times. There is an article about SGD at linux.com.

[http://www.linux.com/article.pl?sid=06/09/19/1759237](http://www.linux.com/article.pl?sid=06/09/19/1759237)

---

### Post by fokuslee on 2007-04-21
Thank you i ended up using the grub disk i think its the only way but all is well again
thank you
oh sgd is really easy to use! its  a keeper on my usb stick

---

