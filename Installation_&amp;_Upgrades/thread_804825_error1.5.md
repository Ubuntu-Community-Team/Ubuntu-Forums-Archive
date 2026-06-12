---
title: "error1.5"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by xeliosone on 2008-05-23
i installed ubuntu 8.04 on my pc which also had WINDows xp. it works ok.

until i shut down the computer then turn it on again.

firs my computer gets stuck at the bios screen
then it says grub loading error 1.5

i am only able to use it by using the live session cd.
using the try ubuntu option, i restart my computer then the boot loader does fine.,.. help please :(

---

### Post by logos34 on 2008-05-23
Go into the Bios (if you can) at startup and check that the hard disk detect is set for [Auto] or [LBA] mode.

Do a filesystem check on the ubuntu partition from the live cd:

sudo fsck /dev/sda1

(replace sda1 with your actual root partition)

Boot into ubuntu using the livecd like you have been doing, then run

sudo grub-install /dev/sda1

It's all [here]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_Loading_stage1.5_Read_Error.").

---

### Post by meierfra. on 2008-05-23
> sudo grub-install /dev/sda1

Did you mean "sudo grub-install /dev/sda"?



Edit: Ignore the rest. I didn't  realize you are able to boot into Ubuntu.

Also, as far as I  know, this does not work from the LiveCD. You need to tell grub-install the location of your ubuntu partition. Say Ubuntu's  root partition is on /dev/sda1


```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
sudo grub-install --root-directory=/ubuntu /dev/sda
```

---

### Post by logos34 on 2008-05-23
> **meierfra. said:**
> Did you mean "sudo grub-install /dev/sda"?

yep, typo.  meant sda (--> mbr)
> 
Also, as far as I  know, this does not work from the LiveCD. 

I thought he was able to get grub to come up and boot into ubuntu from the livecd ("boot from first hard disk" ?)
> using the try ubuntu option, i restart my computer then the boot loader does fine.(

maybe I misunderstood

---

### Post by meierfra. on 2008-05-23
> maybe I misunderstood 

No, it was me who misunderstood. Sorry for the confusion.

---

