---
title: "can't boot ubuntu 11.04 from  external hard drive"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by blitzkriegg9x on 2011-05-10
I am having trouble booting ubuntu 11.04 from my external hard drive, i did a custom instal using the 11.04 CD.

i made 4 partitions 
/dev/sda1  ext2  /boot    1024mb       (1gb)
/dev/sda5  swap            4096mb        (4gb)
/dev/sda6  ext4  /           10240mb    (10gb)
/dev/sda7  ext4  /home   204800mb  (200gb)

and i put grub on the one what was mounted to /boot.



but my problem is when i restart my computer it just starts up windows.

my external hard drive is on, i have it set to boot from removable storage or something like ehtat first. i forget what i just know that booting from my internal hard drive is set to last so it should boot from the external.

please help.

---

### Post by blitzkriegg9x on 2011-05-10
can someone please help? :[

---

### Post by mörgæs on 2011-05-10
There is plenty of help in your other threads.

---

### Post by LostFarmer on 2011-05-10
Do not have time to say much but you need to have grub installed into the external hdd's MBR.  Or have MS's/generic MBR and the /boot partition marked Active/bootable.  OR if MS is installed on the internal hdd you can use 'grub4dos' or 'eacybcd' from Windows boot loader.

---

