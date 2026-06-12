---
title: "A really quick question"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by werg on 2008-01-14
Ok, so I've got Ubuntu installed on a partition. Now it's just a matter of making my machine give me the choice to boot from either the Windows partition or the Ubuntu partition. How do I go on about this?

Thanks.

---

### Post by meindian523 on 2008-01-15
The inbuilt Grub(Grand Unified Bootloader) would automatically do that.

---

### Post by werg on 2008-01-15
Inbuilt as in it is within the Ubuntu package? If so, how to make it operational and how to reboot into Ubuntu to start with?

---

### Post by meindian523 on 2008-01-15
It's automatically installed to your MBR(first 512 sectors of your HDD,IIRC) unless you went to advanced options or some such and configured it to install somewhere else.It becomes active immediately after install.

---

### Post by werg on 2008-01-15
Doesn't look like it... I don't get the option to boot from either partitions.

---

### Post by meindian523 on 2008-01-15
Where are you posting from?Live CD?

---

### Post by Partyboi2 on 2008-01-15
try reinstalling grub. You can do that by following this [guide]("http://ubuntuforums.org/showthread.php?t=224351")

---

