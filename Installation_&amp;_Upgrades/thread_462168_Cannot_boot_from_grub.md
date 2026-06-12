---
title: "Cannot boot from grub"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by HolyJoe on 2007-06-02
I'd made a multi boot , one for windows 2000 and another is ubuntu 7.04. There is a > Failed on Disk1  when boot from disk. I'd do nothing, just reboot my ubuntu, how can I fix this 'error'???

---

### Post by HolyJoe on 2007-06-02
this is my ```
sudo fdisk -l
``` output:
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710        7752    38125049    f  W95 Ext'd (LBA)
/dev/sda5            2710        5827    23572048+   7  HPFS/NTFS
/dev/sda6            5828        7636    13663251   83  Linux
/dev/sda7            7636        7752      883543+  82  Linux swap / Solaris


---

### Post by bulldog on 2007-06-02
Do you get the GRUB menu,where you can select which OS to boot?

---

### Post by HolyJoe on 2007-06-02
I cannot get grub boot-menu, my computer is T43, there has a message > Failed on Disk1 after power on. Today, I upgrade to 2.6.20. *           1        2709    20480008+   7  HPFS/NTFS

---

### Post by bulldog on 2007-06-02
I think this is a message from the BIOS,not from any OS.
I'm sorry but T43 means nothing to me:(

I should check your hardware,and look in the BIOS if your hdd is recognized and listed in the BIOS.

---

### Post by HolyJoe on 2007-06-02
Thank you for your help.
I boot with ubuntu 7.04 live cd, then use grub rewrite my mbr, that solved my problem. But don't know what's wrong???

---

### Post by bulldog on 2007-06-02
Well,if it works for now,there's nothing wrong I suppose........

---

### Post by HolyJoe on 2007-06-02
My means what cause it? May be the 2.6.20 ubuntu upgrade?

---

### Post by bulldog on 2007-06-02
You tell me :D I didn't touch your computer.

It can be several things,maybe a malfunction when you installed GRUB,who knows.
It works that's the main thing.

---

### Post by HolyJoe on 2007-06-03
> It works that's the main thing.
You are right. Thank you for you help.:p

---

