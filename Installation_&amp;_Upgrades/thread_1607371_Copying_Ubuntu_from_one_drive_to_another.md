---
title: "Copying Ubuntu from one drive to another"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by tomdabullet on 2010-10-27
Hi

I installed Ubuntu 10.10 64 Bit on a 20GB drive and it is running fine, no problems. But after installing a 10GB Windows XP virtual machine I'm running low on disk space. I want to copy this setup onto my 160GB drive in a 40GB partition so that i have 2 copies and can run a few more VM's if i want to and have more free space. Is there an easy way to do this?

PS : Wasn't sure if this was the right forum to post it on but it seemed close enough

Tom

---

### Post by sikander3786 on 2010-10-27
If you just want to increase the disc space of Ubuntu partition, you can expand it to take some more space on your drive.

If you want to copy it over to a new drive, consider using a cloning software like clonezilla.

[http://clonezilla.org](http://clonezilla.org)

or the terminal command dd. See the man page for details.

```
man dd
```

---

### Post by ronparent on 2010-10-27
Ive used ^c and ^v in gparted on a live cd to copy a partition from one drive to another. Since the copy will have the same UUID as the original it is best to remove the original from the computer after copying (otherwise you may not know which system you are booting to). You would also have to reinstall grub to the new drive to boot to the new install. Have fun.

---

### Post by sikander3786 on 2010-10-27
> Ive used ^c and ^v in gparted on a live cd to copy a partition from one drive to another.

Doesn't the partition size remain the same that way?

---

### Post by Sylslay on 2010-10-27
one step for copy partition
one step for resize partion.


for dd comand use with care: 

copy MBR , just to have backup
dd if=/dev/sda of=/boot/mbr_backup bs=512 count=1

restore MBR
dd if=/boot/mbr_backup of=/dev/sda bs=446 count=1 

How copy all partition with dd, no idea

---

### Post by ronparent on 2010-10-28
Yes, exactly. The grub reinstall is itself a simple two step process.

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by tomdabullet on 2010-10-28
Did it last night using ronparent's method as it looked the more simple. Had to remove the smaller partition afterwards as the UUID was confusing it.

Thanks a lot guys

Tom

---

### Post by ronparent on 2010-10-28
Great to hear you got it worked out. Suggest you mark the thread as solved.

---

