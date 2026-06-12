---
title: "boot-repair did not helps to make system bootable with lvm2"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by kapusy on 2012-11-25
hi!

Some time ago i think how to make my home server (running ubuntu server 12.04.1 lts) stable and install mdadm (just install, without configuring or doing something).

Today, when i reboot my home server i see following message:
Loading Operating System ...
error: no such partition.
grub rescue>

I've search a while and try to repair my system via boot-repair from live cd.
But have no success (repair told me that everything all right, but won't boot).
Also, during repair with 'boot-repair' i see message 'RAID detected', but i have no raid (only one HDD) and dmraid -E -r /dev/sda show me same (no raid devices).

My log: [http://paste.ubuntu.com/1385912/](http://paste.ubuntu.com/1385912/)

Thanks in advance for any help!

---

### Post by darkod on 2012-11-25
Instead of boot-repair, I would use a 12.04 live cd, boot into a live session and try to reinstall grub2 to the MBR of the disk with:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/srv/root /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

That should detect the LVM and install grub2 on the MBR.

Reboot and see if it worked.

---

### Post by kapusy on 2012-11-25
Thanks for reply.
I try to reinstall grub as you said, but this did not helps... :-(
Still 'no such partition'.

And when i type 'ls' at grub prompt i see no disks in list...

---

### Post by darkod on 2012-11-25
In that case double check if the disk is recognized correctly in BIOS, etc. If at the grub prompt ls doesn't show anything, it looks like it might be a hardware issue.

Also make sure you don't have RAID enabled in the bios, if you are not using it.

---

### Post by kapusy on 2012-11-25
you are absolutely right!
i've installed additional memory to my server and during bios check set usually safe option 'Allow quick boot' to 'On'.
after setting this option off again - grub allow me to boot.

thanks!!!

---

### Post by YannBuntu on 2012-11-26
Hi
Please use the Thread tools to mark it [SOLVED]

---

