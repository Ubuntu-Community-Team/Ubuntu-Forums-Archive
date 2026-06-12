---
title: "Operating system not found"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by aquielisunari on 2010-06-02
I formatted my 2nd hard drive(IDE) inside of windows. So I had a clean 80 GIG HDD. I downloaded the wubi installer and allowed it to have 30 GIGs of the newly formatted hard drive. I restarted it and it just used my 250GIG SATA drive. I then restarted and pressed esc. to make it use the 80 GIG and it said operating system not found. I then deleted it and tried again. Same result. I then reformatted it marked it as active and  installed Ubuntu again and it did boot the 80 but it said the NTLDR is missing. So HELP. Please.

---

### Post by darkod on 2010-06-02
It says OS not found because you are trying to boot from the second disk. Wubi does not install a bootloader on the disk, it just works inside windows.
If you want to use wubi, you still have to boot from your first disk and use windows bootloader that is on it.
Are you sure you correctly specified to wubi where to install? If you told it to use the partition on the 80GB disk, it shouldn't install on the 250GB except maybe some boot files because your windows OS is on the 250GB disk too.

---

### Post by aquielisunari on 2010-06-02
so then I need to order one of those free disks and use the CD. Yes I specified the 80 but since my computer couldn't see an operating system on it it wen to the main one with XP. BTW how can I make this solved? You answered my question and I am satisfied.

---

### Post by darkod on 2010-06-02
Above the first post, in Thread Tools there is Mark as Solved option for you. You have to be logged in obviously, to know it's your thread.

---

