---
title: "custom kernel will not boot!"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2007-03-21
i compiled  and installed 2.6.20.3 for feisty.

im getting this message during boot

/scripts/ext3-add-journal. sh :27 arith : syntax error : "0x"

/sbin/init : 426 arith : synatx error "0x"


what can be done?   sidenote - i have installed many custom kernels on dapper and egdy and this is a first.

my grub entry looks like this

title		Ubuntu, kernel 2.6.20.3
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20.3 root=UUID=500ba0e1-4803-42a5-90c4-737ad7e2780f ro quiet splash
initrd          /boot/initrd.img-2.6.20.3
quiet
savedefault
boot

root is /dev/hda2

---

### Post by raffytaffy on 2007-03-21
great news guys...after some fiddling ..i relized that the new kernels in feisty recognize my harddrive as SDA instead of HDA!!!! so i simply apply the change in the grub conf and bingo!!!!! perhaps this should be an announcement..since i think its big IMO.:popcorn:

---

