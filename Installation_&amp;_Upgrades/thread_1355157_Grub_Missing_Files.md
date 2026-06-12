---
title: "Grub Missing Files"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by vockleya on 2009-12-14
I just installed Ubuntu 9.10 on a new computer, and am having some trouble with it. Grub isn't working, and when I try to run a set up on sda1 through the command line, it tells me that /grub/stage1 doesn't exist. I don't know what is wrong.

My hard drive is set up as follows:

Device        Type    Mount Point    Size
/dev/sda1    ext3    /boot             197 MB
/dev/sda5    ext4    /                   50001 MB
/dev/sda6    swap                       1998 MB
/dev/sda7    ext4    /home           447907 MB

This is exactly the same setup I used on my previous computer, and it worked perfectly.

---

### Post by darkod on 2009-12-14
You mean to set it up on /dev/sda not /dev/sda1? It should go to the MBR of /dev/sda, without using partition number. Also, if you just installed 9.10 (not an upgrade from previous version) you will have grub2 and it doesn't use menu.lst, hence it doesn't exist.
With the setup you specified, to restore grub2 on /dev/sda mbr boot with ubuntu cd, Try Ubuntu option and in terminal do:
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

Note: You have to use only 9.10 which has grub2 inside. 9.04 and previous can only restore grub1.

---

### Post by vockleya on 2009-12-14
It says the installation completed successfully, but when I restart, nothing happens. I get through the bios post screen and then it just sits at a blank screen with a flashing cursor. The grub screen doesn't come up.

---

### Post by darkod on 2009-12-14
You have only one hdd right?

---

### Post by vockleya on 2009-12-14
I have 2

---

### Post by darkod on 2009-12-14
Switch their order in BIOS boot menu. You might be trying to boot the other one.
If that doesn't work, is this a new install of ubuntu or it was working previously? Sometimes blank screen means you need to update the video driver.

---

### Post by vockleya on 2009-12-14
Thanks. That worked.

---

