---
title: "Booting to Ubuntu"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2007-11-01
[FONT="Georgia"][SIZE="2"][FONT="Georgia"]
[[SIZE="3"]SIZE="3"]Hey guys...[/SIZE]

I am unfamiliar with linux so this honestly maybe a dumb question..The install worked flawlessly [/SIZE] but im wondering what must I do, change or the like to only boot to ubuntu on startup.  I havent yet taken xp off but from the cd it said it would replace it with ubuntu..is this true and what are the necessacary steps to boot ubuntu only?  Running ubuntu 710..

Thanks, Matt[/FONT][/SIZE][/FONT]

---

### Post by mikewhatever on 2007-11-01
Removing XP and formatting you hard disk is an option, but you do not have to do it. One reason not to is, you'll loose all your files through formatting. Dual boot instead, use this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing).

---

### Post by Pumalite on 2007-11-01
If the install went flawlessly and you used the entire disk, then now you have only Ubuntu and you just have to let it boot. If you partitioned and are dual booting, get in Ubuntu and post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by mikewhatever on 2007-11-01
> **Pumalite said:**
> If the install went flawlessly and you used the entire disk, then now you have only Ubuntu and you just have to let it boot. If you partitioned and are dual booting, get in Ubuntu and post:
sudo fdisk -lu
cat /boot/grub/menu.lst

OMG!

---

### Post by sports fan Matt on 2007-11-01
All went well..:) im a happy happy ubuntu user!!! Thanks to all that helped..:) Matt

---

