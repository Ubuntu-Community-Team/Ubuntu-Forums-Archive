---
title: "menu.lst during upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by azray on 2008-04-28
I made an error while upgrading by incorrectly answering the question whether I wanted to replace menu.lst or keep the original. Since I answered keep the original the new hardy lines are missing. How can I fix this. I need the correct language to put into menu.lst.

Thanks

---

### Post by Pumalite on 2008-04-28
Try this:
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=435151c5-e8ce-4a6f-96eb-6164051106d3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=435151c5-e8ce-4a6f-96eb-6164051106d3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=435151c5-e8ce-4a6f-96eb-6164051106d3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=435151c5-e8ce-4a6f-96eb-6164051106d3 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

But change the UUID's and the 'root' line as it corresponds to you.

---

### Post by azray on 2008-05-02
Thanks, that did the trick

---

### Post by Pumalite on 2008-05-02
You are welcome. Good luck.

---

