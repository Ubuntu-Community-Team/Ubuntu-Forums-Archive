---
title: "Grub error 15 after deleting partition (fixed)"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by nickzeff on 2008-03-07
OK. I fixed this issue, but I want to know *why* what I did I fixed it!

I deleted one of my windows partitions using gparted. When I rebooted, I got an error 15 from Grub (file not found). I spent hours with the super grub disk and trying to boot my Ubuntu root partition. I knew the kernels were there, I could see the Grub menu options on the screen, but I kept getting error 15: file not found,

Finally I found a bug report which showed that I needed to change my entries in /boot/grub/menu.lst from something like:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e5bd869f-5d59-46ae-b0fb-080fb016fc52 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

```

to


```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e5bd869f-5d59-46ae-b0fb-080fb016fc52 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

```

(note root param).

I'm guessing because I deleted a preceding partition, the reference to the boot partition shifted down.

BUT, I don't get how I could know that. Is there a command I can run to find out that the reference to the root partition is now (hd0,5)? The sda? references don't seem to bear any resemblance to the hd0,? references. What's the difference between the two?

Any knowledgeable people out there who can expand my mind?

---

### Post by Pumalite on 2008-03-07
Since Feisty, IDE's are recognized as sda instead of hda. Grub on the other hand knows only (hd0,0), hd0,1) etc.
Post:
sudo fdisk -lu

---

### Post by nickzeff on 2008-03-07
Cheers Pumalite.

I've listed the partitions with sudo fdisk -lu, but am interested to find out how I can translate the sd?? notation into the grub (hd?,?) notation. How can I ascertain how Grub refers to all the different partitions?

Cheers

N

---

### Post by Pumalite on 2008-03-07
Post them here (the output of "sudo fdisk -lu" so I can help you. One thing I can tell you is that Grub starts counting from zero

---

### Post by nickzeff on 2008-03-08
Ah! I think I've worked it out myself now, but thanks so much for your help!

---

### Post by Pumalite on 2008-03-08
You are welcome. Good luck.

---

