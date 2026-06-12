---
title: "Boot freeze at Configuring network interfaces"
date: 2009-07-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-14
For the 2.6.31-2 and now 2.6.31-3 kernels, boot progress freezes at "Configuring network interfaces". Prior to upgrading upstart, 2.6.31-2 was working properly. I can only successfully boot into 2.6.31-1 now.

If I Ctrl-C at the freeze, 2 more steps are completed:

Cleaning up temporary files... [ OK ]
setting up console font and keymap... [ OK ]

then I get:
 
init: rc-sysinit main process (1123) killed by INT signal

I assume this is the result of hitting Ctrl-C previously?

---

### Post by tekstr1der on 2009-07-14
Resolved this by editing /etc/network/interfaces back to default. Somehow something added auto ppp0 entries to the file. Simple fix.

---

