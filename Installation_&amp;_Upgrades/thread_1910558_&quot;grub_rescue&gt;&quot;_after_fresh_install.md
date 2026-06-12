---
title: "&quot;grub rescue&gt;&quot; after fresh install"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by guttersnipe on 2012-01-17
Hi,

I'm getting the following error after a fresh install of Ubuntu 11.10 on my eeePC 901 netbook.

```
error: no such device: db46bb7a-31aa-4bab-92b1-a13c31df0aab
grub rescue>
```

Typing `ls` at the "grub rescue>" prompt, I get:
```
(hd0) (hd0,1) (hd1) (hd1,5) (hd1,1)
```

I have 2 solid state drives:

/dev/sda1 = holds my ecryptfs-ed home folder from a previous install. I intentionally did not modify this drive during the install.

/dev/sdb1
/dev/sdb2
/dev/sdb5

The above partitions on the second drive were created by the Ubuntu install wizard, where I configured the install to create a primary root partition (/dev/sdb1) which used up the remaining space and a 512MB swap space (/dev/sdb2 = extended & /dev/sdb5 = swap).

I have tried reinstalling several times. I consistently get this error after reboot from the live USB install.

I was going to just edit /boot/grub/menu.lst to change db46bb7a-31aa-4bab-92b1-a13c31df0aab to /dev/sdb1, but GRUB2 confuses the **** out of me. I followed a few guides on how to rescue a broken GRUB2 install using the live USB by re-running grub-install, but the error persisted on reboot.

TIA

---

### Post by darkod on 2012-01-17
Are you maybe booting from the other disk that doesn't contain the latest grub2 install?

Try booting from the other disk to see what happens.

Also, post the results of:
sudo blkid

That will show the UUIDs of all partitions and you can see if the UUID reported as missing in that message is there or really missing.

I think you have broken grub on one disk, and working grub on the other. Try to switch the boot disk first.

---

### Post by raja.genupula on 2012-01-17
hi you can try boot repair for this . it can fix this.

---

### Post by YannBuntu on 2012-01-17
Yep, please try Boot-Repair's "Recommended repair" : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If no success after reboot, please click "Create BootInfo summary" and indicate here the output.

---

### Post by guttersnipe on 2012-01-17
> **darkod said:**
> Are you maybe booting from the other disk that doesn't contain the latest grub2 install?

Try booting from the other disk to see what happens.

Also, post the results of:
sudo blkid

That will show the UUIDs of all partitions and you can see if the UUID reported as missing in that message is there or really missing.

I think you have broken grub on one disk, and working grub on the other. Try to switch the boot disk first.

Good call! I changed the disk boot order in BIOS, and I'm now in a working install. Thanks! :)

---

### Post by raja.genupula on 2012-01-18
Good news man , please mark your thread as solved from thread tools.

Thank you.

---

