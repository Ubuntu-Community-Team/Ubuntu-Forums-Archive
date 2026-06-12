---
title: "Ubuntu &amp; Window in two HDD booting issue"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by bbaskii on 2011-05-23
Hi,

I am using Ubuntu for more than 2 year. Now i have second hard disk installed windows XP. After second HDD connected, Ubuntu is not booting. Once i installed Windows XP on second HDD, i couldn't able to see where is ubuntu. Now i removed SATA cable of the second HDD, i could able to work in ubuntu. How do i automatically select this. Can someone help me in this.

Thank you,

Regards,
Baski

---

### Post by sanderd17 on 2011-05-23
the best thing would be to go in the bios and set the ubuntu HDD as the first to boot from (after the CD off coarse).

You may also need to update your grub if you can't boot xp anymore.

---

### Post by fooman on 2011-05-23
i have done this a few times with method # *2) using ubuntu 9.10 live cd or higher) *from here:

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by Hedgehog1 on 2011-05-23
If you would set your drives to where 'Ubuntu' boots, then do this:

```
sudo update-grub
```

You should see XP in the GRUB menu on the next boot.


***The Hedge***

:KS

---

