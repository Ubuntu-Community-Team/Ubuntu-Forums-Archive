---
title: "Dual boot: install XP after 7.04..."
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by freddo on 2007-05-30
Made the mistake not to install XP first, thought i could solve everything thruogh my virtual XP.. but  not. I have 8 GB unpartitioned space and would like to put an XP installation there, also the choice of OS in GRUB.

Since XP will make a new MBR this could be tricky.. anyone have a good howto for this? Gotta be 100% so I don't mess up my Ubuntu...

Very TIA!

/Freddo

---

### Post by hellmet on 2007-05-30
Just install XP without worries. It will install bootloader onto MBR. Then just pop your LiveCD. Open a terminal and type the following commands::

```
 
#grub
#find /boot/grub/stage1

```
Type what you get above in the root command below.
```

#root (hdx,x)
#setup (hdx)
 
```
If you are OK installing Grub onto root partition, just say
```

root (hd0,0)
setup (hd0)

```

---

### Post by ssican on 2007-05-30
There is a HOW TO dual boot Windows XP and Linux (Ubuntu) ( XP installed first)  on  [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by freddo on 2007-05-30
Thanks, do I have to edit something to get Grub to locate the XP installation?

/Freddo

---

### Post by hellmet on 2007-05-30
NO.. GRUB will detect XP in most of cases!!

---

