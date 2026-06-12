---
title: "GRUB doesn't recognise Windows on other HDD"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by fubar0 on 2006-05-17
Hello, 

I have got Windows installed on an IDE harddisk, now I installed Breezy on a SATA drive. My intention was to have them on different drives.

Problem: I can now only boot into Breezy, GRUB doesn't recognise the Windows partiton automatically on the other drive, even if it is set 'bootable'.

How can I 'tell' GRUB to include Windows in the start-up screen?

Thanks in advance

---

### Post by mozkill on 2006-05-17
hmm... i dont know the answer but you might have a problem having 2 different bootable drives.   i think in this case you are talking about something that the BIOS would have to support...  will your motherboard BIOS prompt you for which drive to boot from?   if that were the case then you could just have 2 different bootable drives and not worry about GRUB handling it since the BIOS would sort it for you...

i hope that made sense....  good luck.  i dont know too much about GRUB.  i hope you get a better answer.

---

