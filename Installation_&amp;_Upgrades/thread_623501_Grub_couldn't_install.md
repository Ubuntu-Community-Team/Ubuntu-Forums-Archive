---
title: "Grub couldn't install"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by mthalis on 2007-11-25
I'm using Ubuntu 7.04. I install Xp then my grub disappear.  I used this command take it again it not work.
This was my command,

grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

grub>

How can install only grub.

---

### Post by jmedina on 2007-11-25
What happened was you are supposed to install Windows First, Then install Ubuntu. Because what happens is Windows overwrites it.

---

### Post by mthalis on 2007-11-25
First I installed Xp first then install Ubuntu next. while using Xp, Xp error happened then I formated Xp partition and installed it again. Then grub disapper. I want to take Ubuntu previous installation.

---

### Post by meierfra on 2007-11-25
Your method really should have worked, and I don't know why it failed. 

Try this instead:

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda7 /ubuntu
sudo grub-install --root-directory=/ubuntu /dev/sda
```


(You might have to use hda7 instead of sda7, and hda instead of sda. You should be able to tell by looking at the output of "sudo fdisk -l")

If this fails,  post the output of  "sudo fdisk -l" and "cat /ubuntu/boot/grub/menu.lst"

---

