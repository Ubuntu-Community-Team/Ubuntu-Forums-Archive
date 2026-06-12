---
title: "&quot;Windows did not start successfully&quot;"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-06-02
I just finished installing Feisty on a dual boot system (where XP was already installed in a previous step.)

The Live CD worked fine, all the partitions are legitimate (1 NTFS, 1 Swap, 2 ext3 for / and /home), and the install process appeared to go flawlessly. However, after restarting my PC (and removing the Live CD), I was confronted with a black screen + the message: "We apologize for the inconvenience, but Windows did not start successfully. A recent hardware or software change might have caused this."  I can then choose to start XP in safe mode, or start it normally, but I have no access my Linux partitions. It's almost as if GRUB isn't even present - but that's just speculation.

So I'm not sure what's wrong with the boot process. Any ideas on things I could try, or let me know if more info is needed.

Thank you in advance.

---

### Post by merlinus on 2007-06-02
Is the grub menu appearing?

Or is your computer trying to boot windows only?

-merlin

---

### Post by Pai on 2007-06-02
GRUB never appears. The message appears immediately after the POST process.

---

### Post by merlinus on 2007-06-02
It would seem that for some reason, grub did not get installed, or was installed incorrectly.

Boot from the live cd, go to a terminal and enter:

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute the find results for root and setup.

Also, you might post /boot/grub/menu.lst

You can get this in a terminal:
```

cat /boot/grub/menu.lst

```
-merlin

---

