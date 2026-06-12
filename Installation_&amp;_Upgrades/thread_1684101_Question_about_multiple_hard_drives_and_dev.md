---
title: "Question about multiple hard drives and /dev"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by pontifor on 2011-02-08
Hi,

I have 5 hard drives in my machine.  Each time the machine boots, it is possible for the logical names to be different..?  I don't understand this, I reference those logical drives ( i.e. /dev/sdb ) in my fstab file and that works until I reboot..  I think there is something basic I am missing..

thanks,
Stefan

---

### Post by Morbius1 on 2011-02-08
Yes they can. That's why the default way is to use UUID's.

If you want to see what the UUID's are for your partitions then run the following command:
```
sudo blkid -c /dev/null
```You'll get an output that looks something like this:
> /dev/sda1: LABEL="WinXP" UUID="[COLOR=Blue]DA9056C19056A3B3[/COLOR]" TYPE="ntfs" 
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat" 
/dev/sdb2: UUID="a6c223bf-f9dc-49a7-9b86-ac8729e95369"  
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a" TYPE="ext3" 
/dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" 
So if you have an fstab entry that starts with say:
> /dev/sda1 /some-mount-pointYou would change it to:
> UUID=[COLOR=Blue]DA9056C19056A3B3[/COLOR] /some-mount-point

---

### Post by pontifor on 2011-02-08
Thanks!!!

---

