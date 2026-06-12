---
title: "No bootloader in installation"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by mahy on 2006-11-02
Hi there people,

a friend of mine is considering installing Ubuntu on his laptop, but he REALLY wants to stick with the default windows bootloader. And he can't just remove the GRUB afterwards (the FIXMBR command in windows ASR), coz he only has a windows image recovery cd and not a proper installation CD. I've heard some rumors about being allowed to customize grub installation using 'alternate' cd. However, i ran the alternate installation myself, but haven't noticed any such option. Please tell me there's a way to leave MBR untouched and how to do it.

---

### Post by gushie on 2006-11-02
Same here, I got the same problem like your friend does. The Grub doesnt allow me to boot to my windows...](*,)
Heeeeeeeeeeeeeeeelllllp......

---

### Post by mahy on 2006-11-02
> **gushie said:**
> Same here, I got the same problem like your friend does. The Grub doesnt allow me to boot to my windows...](*,)
Heeeeeeeeeeeeeeeelllllp......

Hehe, that's an entirely different problem. Just add windows option to your /boot/grub/menu.lst

Like this:

```
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```

adjust as needed...

---

### Post by galileon on 2006-11-02
edgy has an option where to install grub, so you could simply try to put it in the ubuntu partition itself...

to boot ubuntu from the doze bootmenu is another thing, try googling it...

---

### Post by SaltyMcCracker on 2006-11-02
I have a different problem,

I'm trying to install Dapper with a live CD and it doesn't give me the option to install grub at the end.  Help?

---

### Post by galileon on 2006-11-02
dapper doesnt have this option in the gui (regular) cd, but i believe it has it in the alternate cd, though you should check this first before downloading it...the regular dapper behaves somewhat like what i call the WIndozeXPBootloader Trojan, because it trashes the bootloader and installs its own without warning.

this has been fixed in edgy, so you might want to try it out...

---

### Post by MrBbDD_OK on 2006-11-02
> **mahy said:**
> Hi there people,

a friend of mine is considering installing Ubuntu on his laptop, but he REALLY wants to stick with the default windows bootloader. And he can't just remove the GRUB afterwards (the FIXMBR command in windows ASR), coz he only has a windows image recovery cd and not a proper installation CD. I've heard some rumors about being allowed to customize grub installation using 'alternate' cd. However, i ran the alternate installation myself, but haven't noticed any such option. Please tell me there's a way to leave MBR untouched and how to do it.

Using the alternate CD gives you a choice of where to put the bootloader, somewhere in the partition / mount point setup. (I just did the install a week ago, but don't remember the exact step.) One used to enter 'expert' at the Linux CD boot to be sure of getting this option, but that convention is going away. ](*,)

---

