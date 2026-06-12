---
title: "boot crash grub rescue, initramfs pronpt"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by inskcami on 2009-12-06
hello everybody

mistakenly i´ve deleted a partition and then when the grub load
it throw me in the grub rescue mode it goes like this

GRUB loading.
error : unknown filesystem
grub rescue>

i´ve find out in the ubuntu help comunity this, that seems to work until some part

1 set root=(hd0,6)  (6 is where i have the file system)
2 set
3 set prefix=(hd0,6)/boot/grub
4 insmod /boot/grub/linux.mod
5 linux /vmlinuz root=/dev/sd06 ro
6 initrd /initrd.img
8 boot

then i go to this pronpt:

(initramfs)

and from that nothing works ive tryed few comands but i cannot restore or reinstall grub from that

does anybody know what can i do? 

im freaking out im out of ideas
i even thought about change the bios startup and reinstall everything but to help a bit more i cannot remember the password, im going crazy right now :p

I apreciate any help

thanks alot if you at least reading this


best regards
inscami

---

### Post by inskcami on 2009-12-07
any sugestion?

thanks

---

### Post by presence1960 on 2009-12-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

