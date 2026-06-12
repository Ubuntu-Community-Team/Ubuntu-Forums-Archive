---
title: "Error: No such partition, grub rescue&gt; Please help!"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by eoinfen on 2012-04-23
I've been dual booting Windows 7 and Ubuntu for a while, and yesterday I decided to delete my Ubuntu partition. 

Upon restarting my computer, I got the message "No such partition / grub rescue>". 

I've tried booting from DVDs of Windows 7 and Ubuntu, but the DVD drive just works for a minute and then the "No such partition / grub rescue>" line comes onto the screen.

Can anyone help my solve this problem? I want to get Windows 7 working on my computer again, and ideally be able to get my data back.

Many thanks in advance,

Eoin

---

### Post by darkod on 2012-04-23
The data is there (except the data that was on the ubuntu partition you deleted).

The win7 dvd should be able to boot and you can repair the bootloader with it. Make sure CD-ROM is before HDD in the boot device options.

If you can't make the win7 dvd boot, you can install a generic MBR on the hdd from ubuntu live mode. But that would still mean you have to boot with the ubuntu cd into live mode and in terminal do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That might show a warning about the lilo configuration but it's safe to ignore it. Those commands will install a generic mbr on the hdd which will boot your windows installation.

---

### Post by eoinfen on 2012-04-23
Darkod,

Thanks, but it won't boot from a DVD-RW of Ubuntu. I will buy some CDs later and let you know if that works.

---

### Post by 2F4U on 2012-04-23
To me it sounds as if your computer is not attempting to boot from the dvd drive, but instead from disk. I would either try to change the boot order in the BIOS or open the temporary boot menu of the BIOS and select the dvd drive to boot from.

---

### Post by eoinfen on 2012-04-23
2F4U,

That is not the problem. I have set it to boot from the DVD drive first and have tried booting from the DVD drive from the temporary boot menu.

Thanks anyway.

---

### Post by eoinfen on 2012-04-23
Solved,

My computer wouldn't boot from a DVD-RW for some reason. A DVD-R worked perfectly.

---

