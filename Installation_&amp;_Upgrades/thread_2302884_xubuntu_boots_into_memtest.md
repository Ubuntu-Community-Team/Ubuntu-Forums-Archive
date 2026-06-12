---
title: "xubuntu boots into memtest"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by tiar on 2015-11-14
Guys,

I was doing a standard software update. /boot was full, I've tried to clean up and screw up. Now I can boot olny into memtest.

I've tried boot-repaid but it didn't help. It's report is here [http://paste.ubuntu.com/13261434/](http://paste.ubuntu.com/13261434/)

What can I do to fix it?

---

### Post by grahammechanical on 2015-11-14
According to Boot Repair the Grub configuration file grub.cfg has two entries for Memtest but no entries for Ubuntu. I guess that is because the Ubuntu partition (sda5) is encrypted. Not only is Boot Repair unable to access the encrypted partition but running update-grub would also be useless while the Ubuntu partition was still encrypted. 

I can only guess at a solution. From the Ubuntu live session you can try decrypting the Ubuntu partition and then running

```
sudo update-grub
sudo grub-install /dev/sda
```

But for that to have any chance of success there will need to be at least one Linux kernel still left on the machine.

Regards.

---

