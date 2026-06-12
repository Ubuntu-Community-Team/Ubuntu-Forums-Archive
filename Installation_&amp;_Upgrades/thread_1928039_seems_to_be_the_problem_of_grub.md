---
title: "seems to be the problem of grub"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by nullne on 2012-02-19
when booting it appears :
error:invalid arch independent elf magic
grub rescue<

apparently,i don't have any idea of it .
then i try some methods found online
1)
type followings behind rescue:
set root=(hd0,2)
set prefix=(hd0,2)/root/grub
insmod normal

then appears invalid arch independent elf magic

2)ls (hd0,2)
appeared     bad filenames
ls (hd0,*)  [*stands for 1,3,4,5,]
appeared     unknown filesystem


3)  then i try  


start ubuntu using usb system

mount /dev/sda1 /mnt/
grub-install --root-directory=/mnt /dev/sda 

appeared 
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.


certainly i don't understand it

go on trying

mount /dev/sda /mnt
mount --bind /dev /mnt/dev
sudo chroot /mnt

apeared:chroot: failed to run command `/bin/bash': No such file or directory



finally, i really almost die.[/QUOTE]

---

### Post by darkod on 2012-02-19
You seem to be using a GPT partition table. For grub2 to work correctly it needs to have a small partition which has the biosgrub flag set.

Are you dual booting with windows or not?

---

### Post by nullne on 2012-02-20
> **darkod said:**
> You seem to be using a GPT partition table. For grub2 to work correctly it needs to have a small partition which has the biosgrub flag set.

Are you dual booting with windows or not?


sorry to answer so late ,because i used usb to boot,which couldn't last very long.

it seems that i use GPT ,i have seen it somewhere in my machine 
i am trying to install dual booting  but not secceed until now

how can i go back to my system?

---

