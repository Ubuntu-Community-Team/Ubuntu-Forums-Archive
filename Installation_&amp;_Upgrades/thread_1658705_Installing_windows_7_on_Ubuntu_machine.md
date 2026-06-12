---
title: "Installing windows 7 on Ubuntu machine"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by gearhead_318 on 2011-01-03
I currently have Ubuntu 10.04 LTS on my 64bit laptop but I'd like to install Windows 7 on an empty partition as a secondary OS. I have more stuff on my laptop then I have space to back it up, so I was wondering if I could install Win7 on that empty partition or will I have to start from scratch? If I can is there a guide? I searched but didn't find anything that answered my questions.
Thanks

---

### Post by Rubi1200 on 2011-01-03
Hi and welcome to the forums :-)

Have you already created a free partition for Windows to use?

From a terminal on Ubuntu, post the output of:
```
sudo parted -l
```

Also helpful would be the specifications for the computer, especially RAM and graphics card.

Thanks.

To answer the question: yes, you can do it, but you will have to reinstall GRUB afterwards (a simple procedure).

---

