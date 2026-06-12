---
title: "Need help removing grub from second hardrive"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by bf2loser on 2008-03-03
I've seen sort of similar situations but I havent seen an answer to my exact problem, so I thought I would post. I installed windows vista and xp dual booting on my 120 gig hardrive. Then I installed ubuntu 32 and 64 bits dual booting them on my 60 gig hardrive. but when I installed the ubuntus, they put grub on my 120 gig hd. So when I go to boot I have to load grub, then I can choose one of my ubuntu installations or I can tell it to boot hte windows bootloader so I can then select vista or xp. I want to remove the grub bootloader completely from the 120 gig hd, so the only way I get to grub is if I try to boot from the 60 gig hardrive through the bios. Is there an easy way to do this or am I just gonna have to reinstall my windows partitions?

---

### Post by logos34 on 2008-03-03
You don't have to reinstall windows to get the bootloader back--use the vista install DVD repair environment to do it.  But first write grub to the mbr of the ubuntu drive:

**sudo grub-install /dev/hdb** (or sdb, or whatever it is).

Remember to change the root and 'groot' lines in menu.lst from (hd1,x) to (hd0,x) just before you get ready to reboot back into ubuntu via the Bios--whatever hard disk you choose as boot drive becomes (hd0)

gksudo gedit /boot/grub/menu.lst

---

### Post by bf2loser on 2008-03-03
I changed the lines and wrote grub to the sdb hardrive mbr (sda is my vista/xp disk), and put in my vista disk and tried to repair the bootloader but it didnt find any problems. Its weird, its like grub is the master bootloader but it will send me to the vista bootloader. it just gives me two bootloaders in a row.

---

### Post by logos34 on 2008-03-03
Hmm.  You can erase grub from the mbr of the windows disk, but will Vista dvd then recognize that and reinstall the windows bootloader, since it doesn't see a problem currently?  Not sure.  I don't want to leave you with an unbootable windows disk.  But if you want to erase grub and retry the repair environment, either use dd command: 

**dd if=/dev/zero of=/dev/sda bs=446 count=1** (-->erases mbr ONLY on sda, not partition table)

or the 'uninstall' option on the Super Grub Disk

---

### Post by bf2loser on 2008-03-03
Well I googled it a bit more and found that if I did

```

bootrec /fixboot
bootrec /fixmbr

```

from the Vista dvd, in a cmd prompt it deletes whats in the mbr and re writes the vista bootloader, so I tried that and my Windows partitions are fine. But it did sorta ruin my GRUB on my ubuntu drive, which isn't a big deal for me, I'm gonna format and use it for other stuff for the time being, but I'm sure even if I did want to use it it would be an easy fix with a live cd.

---

### Post by logos34 on 2008-03-03
> **bf2loser said:**
> Well I googled it a bit more and found that if I did

**bootrec /fixmbr**

from the Vista dvd, in a cmd prompt it deletes whats in the mbr and re writes the vista bootloader, so I tried that and my Windows partitions are fine. But it did sorta ruin my GRUB on my ubuntu drive, which isn't a big deal for me, I'm gonna format and use it for other stuff for the time being, but I'm sure even if I did want to use it it would be an easy fix with a live cd.

Oh, I assumed you did the fixmbr command the first time. 

Restoring grub from the live cd to the sdb mbr is as easy as:

sudo grub

> find /boot/grub/stage1
(enter output in next command)
> root (hdx,y)
> setup (hdx)
> quit

---

### Post by bf2loser on 2008-03-03
I didnt even know there was a bootrec /fixmbr command at all, when you meant to repair I thought you meant to use the repair startup option lol, but thats alright, I got it all figured out. Thanks for the help

---

