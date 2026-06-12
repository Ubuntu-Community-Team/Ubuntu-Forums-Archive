---
title: "Remove windows entry from Grub2"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by yahelos on 2010-08-17
Hello again!!

Ive installed a fresh copy of ubuntu onto my laptop, dual boot with 7. Everything runs smoothly except the grub. 

So in grub i have an entry of vista loader. I have removed the ubuntu recovery mode and the memtest entry so now i have 3 entries
Ubuntu
vista loader
7 loader

How i can remove the vista loader? 

PS i have never had installed vista onto my system i bought it brandy new with 7 pre-installed.

---

### Post by TheStroj on 2010-08-17
Vista loader is 7, but in the old days 7 was not recognized and was discribed as Vista loader.

---

### Post by yahelos on 2010-08-17
so what? i need the two of them?

---

### Post by Rubi1200 on 2010-08-17
Does running
```
sudo update-grub
```
from the terminal give a different result?

---

### Post by drs305 on 2010-08-17
One way would be to modify the /etc/grub.d/30_os-prober so that it omits a specific title. Look at Section 4 of my "G2 Title Tweaks" thread. You wont' use the "Recovery" title in the example, but would substitute the Vista loader title found in quotes in /boot/grub/grub.cfg.
[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

It's a bit geeky but if you follow the instructions it shouldn't be too hard to accomplish.

Another option is to just make and use a Custom menu and disable the 30_os-prober script altogether.

---

### Post by yahelos on 2010-08-17
I think that will do the trick.

Ill try it when i ll go home, and i ll post the results.

---

### Post by yahelos on 2010-08-17
it works like a charm!!! thx buddy!!

---

### Post by drs305 on 2010-08-17
> **yahelos said:**
> it works like a charm!!! thx buddy!!

:-)

Did you use the "Title" change method from the Title Tweaks thread?

I've seen others wanting to get rid of the "Vista Bootloader" entry. I can include that specifically in the Title Tweaks section if you would be so kind as to give me the *exact* title as it appeared in grub.cfg or as you have it in your exclusion line in 30_os-prober.

---

### Post by yahelos on 2010-08-18
I used the [SIZE=2]"[/SIZE][SIZE=2]**[COLOR=DarkRed]HIDING THE  WINDOWS RECOVERY PARTITION (Vista)"[/COLOR]**[/SIZE]

the name was exactly as at your guild. 

Windows Vista (loader) and at the same partition (sda1)

The weird part is that when i bought my laptop ive format the disk and erased all of his partition to get rid off the pre-installed software.
So ive believed that i had completely erased the "service partition"

[B][COLOR=DarkRed][COLOR=Red]
[/COLOR][/COLOR][/B]

---

