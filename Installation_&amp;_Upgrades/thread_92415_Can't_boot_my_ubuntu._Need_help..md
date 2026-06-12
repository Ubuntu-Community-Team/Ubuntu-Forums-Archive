---
title: "Can't boot my ubuntu. Need help."
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by zeka on 2005-11-19
Something happend and i can't boot ubuntu agin, My machine allways boot windows xp. 
Boot loeader is missing :(
Right now im with live cd and i don't know what to do.. Can i install somehow the boot loader agin?

---

### Post by campusloop on 2005-11-19
If you know the root partition of ubuntu, from within livecd you can do something like this..

as root - 

mount the partition containing ubuntu - assume it is mounted to /mnt/hda3 and you want to install grub to ide master hard disk /dev/hda 
you can execute - "grub-install --root-directory=/mnt/hda3 /dev/hda" this will install grub onto the mbr of /dev/hda

---

### Post by zeka on 2005-11-19
[QUOTE=campusloop]If you know the root partition of ubuntu, from within livecd you can do something like this..

as root - 

mount the partition containing ubuntu - assume it is mounted to /mnt/hda3 and you want to install grub to ide master hard disk /dev/hda 
you can execute - "grub-install --root-directory=/mnt/hda3 /dev/hda" this will install grub onto the mbr of /dev/hda[/QUOTE]

Can u plz explain that step by step, because i'm rightnow too confused to understand anyting :s

---

### Post by campusloop on 2005-11-19
It is some time since i have used the ubuntu live cd but the basic steps are

1. mount the partition which contains ubuntu root partition. i think you can mount the disks in the live cd by using nautilus. it should list the drives. Or after you have booted into the live cd start 'gnome-terminal' become root by using 'su'. type 'cat /etc/fstab' and it will print out a list of all the partitions which can be mounted. For example if /etc/fstab contains something like 
          /dev/hda3       /mnt/hda3          reiserfs defaults        0       2

which corresponds to the ubuntu root partition, you can then mount the partition using 'mount /mnt/hda3'

2. Now you can reinstall grub to the MBR of hard disk using "grub-install --root-directory=/mnt/hda3 /dev/hda".

if you still are not sure, post the '/etc/fstab' file taken after booting into live cd and i can give you exact commands to restore grub to MBR.

---

### Post by zeka on 2005-11-20
```
root@ubuntu:/home/ubuntu # cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
root@ubuntu:/home/ubuntu #

```

Only swap.. can't mount it

```
root@ubuntu:/home/ubuntu # mount /dev/hda5 /mnt/hda5
/dev/hda5 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

---

### Post by theBuggane on 2005-11-20
I think that this is the same solution posted earlier, but perhaps more simply. This is from another site ([http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)) and so thanks to the original poster (Michael Manning), who saved me a lot of grief!

[I]If you are going to need to use a Live CD to recover the backup MBR then you could have booted into rescue mode from the install CD (of any linux distro you choose) and mounted the linux partition, chrooted to the root partition and typed grub-install /dev/hdx.

[B]mkdir /mnt/temp
mount /dev/hda3 /mnt/temp ## if hda3 was the linux partition
chroot /mnt/temp
grub-install /dev/hda[/B]

That would install the grub first stage boot loader to you the MBR of the hard disk and presented you with the same options you had before the Windows reinstall. no need for backup MBR records![/I]

---

