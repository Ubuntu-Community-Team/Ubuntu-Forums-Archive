---
title: "howto: restore grub in ubuntu edgy 6.10"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by desheikh on 2007-01-05
I just installed vista and as expected it wiped out my grub loader :p
It took me a while to figure out how to restore grub from the ubuntu edgy live cd so im posting my solution here 

First mount your boot partition

# sudo mount /dev/hdx /boot

where hdx is your /boot partition

If you dont have a seperate /boot partition then youll probably have to mount your ubuntu drive and mount /boot from there, something like

# mkdir /mnt/ubuntu
# sudo mount /dev/hdx /mnt/ubuntu
and then:
# sudo mount /boot /mnt/ubuntu/boot

then do 
# sudo grub-install hda

This is only if you installed you grub loader in the mbr in the first place which is the default ubuntu install.

---

### Post by pldobs on 2007-02-11
I just tried this. . . I got "Cannot create directory '/boot/grub' : Read Only File System."   Any ideas how to get past this one?

---

### Post by desheikh on 2007-05-20
Hmm that last line line should be sudo grub-install /dev/hda ...

---

