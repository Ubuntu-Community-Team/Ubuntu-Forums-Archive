---
title: "After upgrading to 19.04 Epson tx135 does not print characters only images"
date: 2019-08-09
forum: Installation &amp; Upgrades
---

### Post by xyko on 2019-08-09
Hi all,
I`m facing that problem after upgrading to 19.04. My Epson TX135 only prints images not text. I have excluded the printer, reinstalled the drivers from epson`s support site, added the printer again and not solved the bug. I looked to CUPS error log and saw a command setting fontspath to a directory that does not exist (/usr/share/cups/fonts).
Any help?
Thanks in advance

---

### Post by dino99 on 2019-08-10
I have no skill with that hardware, but you might try first with the > printer-driver-escpr driver from the ubuntu archive to avoid non standard install path and use other custom ubuntu settings. Do purge the previous packages installed from source.

---

### Post by xyko on 2019-08-10
Dino99, thanks for your help. I have already done what you sugest with no success. It is important to say that all was working fine with the previous version, 18.10. Regards.

---

### Post by him610 on 2019-08-11
xyko,
In this file, /usr/share/cups/cups-files.conf.default
there these two commented lines...
```

# Location of fonts used by older print filters...
#FontPath /usr/share/cups/fonts

```
Make sure the FontPath line includes the crunch(#) at the beginning.

---

### Post by xyko on 2019-08-12
Thanks for your help hom610. I had a very busy day, I will check this conf file asap. Regards.

---

### Post by xyko on 2019-08-13
Hi hom610.
Yes, my /usr/share/cups/cups-files.conf.default has those lines as you wrote. FontPath is a commented line.
Regards,

---

