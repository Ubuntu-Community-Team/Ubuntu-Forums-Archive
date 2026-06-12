---
title: "Broken USB Keyboard and Mouse after latest updates"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Psychobudgie on 2008-10-14
Following an update this morning the usb keyboard and mouse are no longer responding. I can get USB to function if I revert to kernel 2.6.24-19. 

In the kernel log for 2.6.27-7 it doesn't show the usb devices initialising which it does show quite clearly in the latter.

Anyone else had any similar issues?

---

### Post by boc-sixtyniner on 2008-10-14
yeah. it's really annoying. try ctrl+alt+f3 or whatever to get to another tty. That's been working for me, which seems to suggest that it's a problem between X and the new kernel.

---

### Post by Psychobudgie on 2008-10-14
It doesn't work here. Devices aren't responding at all. Have had to revert back to the older kernel to get things working again.

---

### Post by Tlon on 2008-10-28
I am having this same problem, only I am using what is supposedly the LTS.  Really.  Irksome.  Trying to revert to the older kernel hasn't helped, either.

---

