---
title: "Changing GRUB boot partition problems"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by ianhaycox on 2008-06-02
I having problems changing Grub to use the new partition for a fresh Hardy install.

I've got,
    /dev/sdb1  (New Hardy install)
    /dev/sdb2  (Old Gutsy upgraded from Dapper over the years)

After the Hardy install there was no /boot/grub/menu.lst in /dev/sdb1 and the stanzas for Hardy had been added to the menu.lst on /dev/sdb2. Hardy boots OK but I want to free up /dev/sdb2 for extra data.

I tried a $ sudo grub-install and that created a /boot/grub/stage1 etc on /dev/sdb1. I added menu.lst but on a reboot it still used the old menu.lst.

Tried the following:-

$ sudo grub

grub> find /boot/grub/stage1

(hd1,0)
(hd1,1)

grub> root (hd1,0)

grub> setup (hd1)


but it boots showing the old menu.lst from (hd1,1) not (hd1,0)

I also tried the same from a Live CD, but no joy.

How do I fixup the MBR to make Grub use the correct partition so I can format the old Gutsy install ?

Thanks.

---

### Post by Pumalite on 2008-06-02
Just install on top of the old Gutsy. Go Manual and choose the partitions. You will have a new Grub and things will take care of themselves.

---

### Post by ianhaycox on 2008-06-02
I was hoping not to re-install as Hardy's been installed and working fine for a while and I've installed loads of stuff, fiddled, customized etc.

The only reason I noticed that Grub was wrong was because the recent Hardy (-17 ?) kernel update was not automagically added to my menu.lst file.

I'd prefer to fix one problem with Grub and keep my working installation rather than go through the hassle of a re-install.

---

### Post by fsmithred on 2008-06-02
Boot into Hardy, make sure you have all the needed files in /boot/grub, and then:

sudo grub-install /dev/sdb

That should make it so that hardy is in charge of booting.

---

### Post by meierfra. on 2008-06-03
> sudo grub-install /dev/sdb

But it looks like the OP is booting from /dev/sda.

So  I suggest
```

sudo grub-install /dev/sda
```

(from  a terminal  in the Hardy partition)

---

### Post by ianhaycox on 2008-06-03
Ran

```
$ sudo grub-install /dev/sdb
```

and it completed without error and reported the correct devices and hd/fd numbers.

After a reboot it still booted off the wrong partition. I'm sure it's still incorrect because I changed the title in each menu.lst file to be different and after a reboot the menu from /dev/sdb2 is shown and not /dev/sdb1.

Is there anyway to examine/print the MBR to see whats going on ?

/dev/sda just has data on it and no OS at all.

Any other ideas ?

---

### Post by meierfra. on 2008-06-03
You are booting from /dev/sda . So you need to use "sudo grub-install /dev/sda". This install grub to the first few sectors of /dev/sda. These few sectors come before any of the partition on /dev/sda. So none of the data will be touched.

If you really don't want to install grub to /dev/sda, you need to change the boot order in the bios. To make this work, you would also have to edit "menu.lst". If this is the way you want to go, let me know, and I can tell you exactly what to do.

---

### Post by ianhaycox on 2008-06-03
Bingo, using /dev/sda worked.

Makes sense now. I can see why I was confused.

If i did change the boot order in the BIOS, I'm assuming that sda and sdb would transpose and then I'd also have to make changes to /etc/fstab and possibly other files to swap a for b and vice-versa. Also hd0/1 in menu.lst Is this a correct assumption ?

Until sda fails I'm OK with it as it is.

Thanks.

---

### Post by meierfra. on 2008-06-03
> I'm assuming that sda and sdb would transpose 

No, ubuntu actually does not seem to know which drive its  was booting from. So this will not change.


> Also hd0/1 in menu.lst Is this a correct assumption ?

This one is correct, and should be all you need to do.

---

