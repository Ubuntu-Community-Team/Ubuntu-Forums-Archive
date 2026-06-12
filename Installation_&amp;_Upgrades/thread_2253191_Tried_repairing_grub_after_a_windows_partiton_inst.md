---
title: "Tried repairing grub after a windows partiton install and I cannot get it back"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by tikoloshe2 on 2014-11-17
Root drive exists on an LVM volume on the second hard drive 
/boot exists on a basic ext2 volume on the second hard drive

Initiated LVM volume 
>pvscan
>vgscan
>vgchange -a y

>mkdir /mnt/root
> mount /dev/xubuntu-vg/root  /mnt/root
> for i in dev proc sys run;do mount -o bind /$i /mnt/root/$i ;done

>chroot /mnt/root
> mnt /dev/sdb1 /boot
update-grub
grub-install /dev/sda

I also ran boot-repair but that failed too
here is the pastebin
[http://paste.ubuntu.com/90647332](http://paste.ubuntu.com/90647332)

After all of these I still get partition not found on booting. I just don't know what partition  :/


Any help would be great.


Thanks

Michael

---

### Post by ajgreeny on 2014-11-18
Sorry but your pastebin link is dead.  Please let's have the correct one.

---

