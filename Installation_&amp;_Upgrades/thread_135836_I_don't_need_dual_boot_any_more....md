---
title: "I don't need dual boot any more..."
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by david_e on 2006-02-24
I was dual-booting Windows Xp and Ubuntu Breezy with GRUB.

After a cupple of mounths of happy Linuxing :mrgreen:  I have decided to kill windows once for all, so I used the live CD to delete Windows partition and to merge it with the ext3 partition. (I had to move the ext3 partition to the first part of the disk)

I was able to edit grub so it doesn't show windows boot option any more, but I am tired to see Grub menu starting ALL the times: is there a way so I can configure grub to display the menu only if I press the "DEL" key (or another key it doesn't matter) within 3 secs or it starts Ubuntu 5.10, like it does if u just install Ubuntu on an empty computer?!?

I have searched the forum very mutch but I have only found topics about ubuntu removing or double booting....

---

### Post by lha on 2006-02-24
Open menu.lst and find line
#hiddenmenu
and uncomment it, resulting in a line
hiddenmenu

Find a line with
timeout 10
(The number may be different for you.) Replace that number with 3.

---

### Post by david_e on 2006-02-25
THX I was able to set GRUB like I wanted it to be!

---

