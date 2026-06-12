---
title: "Grub"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by Soebam on 2005-04-24
Hey,

I had installed ubuntu when i had already installed windows on my system. I used GRUB as bootloader to choose between ubuntu and windows and it worked fine. But now i reïnstalled windows, fool as i am, i let windows overwrite my mbr. I cannot reach my ubuntu installation anymore. Is there a way to get it back without having to start over?

I have two harddisks, windows is on 1 and ubuntu on the other.

---

### Post by nad on 2005-04-24
Please search these forums for your answer. This issue comes up several times a day. By starting a new thread it becomes harder to search on topic for an already posted answer and it also causes duplication of effort. Thank you.

---

### Post by alastair on 2005-04-24
If you have the Ubuntu CD, I believe there is a "rescue" mode that should let you reinstall your GRUB bootloader in the MBR.

---

### Post by Xerampelinae on 2005-04-24
There are a few ways to do this.  This way requires a live CD to boot from.

Once you boot from a live cd into linux, open a prompt and mount your ubuntu partition, which I will call /dev/hda2.  Then chroot into it.

```
mkdir /mnt/hda2
mount /dev/hda2 /mnt/hda2
chroot /mnt/hda2

```

At this point you should feel like you're using a terminal on your old ubuntu system (all the old files and stuff should be in /home, etc)  Make sure you have /boot with your linux kernel and other stuff on this partition (it is by default I think).

In the next commands below, the hd0,1 means the first hard disk (0), and the second partition (1), thus the hd0,1  (counting starts at 0).  If your setup is different you would have to change these numbers...

```

grub
grub> setup (hd0,1)
grub> root (hd0)
grub> quit

```

I hope it goes well.  You have to be a bit careful or you'll leave your system in an unbootable (but recoverable) state...

---

### Post by Xerampelinae on 2005-04-24
D'oh.  I spent time writing about that and there are already answers on this forum...

Please search next time.    :\

---

### Post by Soebam on 2005-04-24
Woops sorry guys.. :-#

---

