---
title: "LUKS over LVM"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by canidae on 2008-02-22
Evening.

I'm trying to install what I believe is called "LUKS over LVM".
Here's my scenario:
I've already installed Ubuntu a long time ago, neither on an encrypted partition nor on LVM. The partition I installed on is 20GB and i got another 80GB or so free.
The guides I've read covers installing LVM over LUKS, but I failed to find one that covers LUKS over LVM.

Partitions:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17        9472    75955320   83  Linux
/dev/sda4            9473       12161    21598920   83  Linux
```

sda1 is boot, sda2 is used as a physical volume for LVM, sda4 is my current installation of Ubuntu.
sda2 is used for volume group "lvm_disk". This volume group got 2 logical volumes, "root" and "swap".

So far I've followed this guide: [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
Where i replaced /dev/sda5 with /dev/lvm_disk/root.
It's worth noting that I have copied the system over to an unencrypted LVM logical volume, and that it works flawlessly. It's making the system boot when the logical volume is encrypted and not the partition that's troublesome.

crypttab:
```
# <target name> <source device>         <key file>      <options>
root /dev/lvm_disk/root none luks,retry=1
```

menu.lst:
```
title           Ubuntu 7.10 encrypted, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/lvm_disk/root ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet
```
I've also tried with "root=/dev/mapper/root".

and /etc/initramfs-tools/modules contains:
```
aes-i586
dm-crypt
dm-mod
sha256
```

"update-initramfs -k all -c" won't create the file "../conf/conf.d/cryptroot", and thus neither will the computer boot using an encrypted root partition on a logical volume.

I do it this way because I don't have an external disk I can temporary store my data on, so if I do "LVM over LUKS" I can't add those 20GB to LVM in a "nice" way, afaik.

---

### Post by canidae on 2008-02-25
Well, I'll be damned. It works!

I'm not quite sure what I did wrong on Friday, quite possible the brain started the weekend earlier than the rest of the body.

Posting this in case someone else get into the same problem, and in case someone's trying to figure out what was wrong:

Follow this guide as far as possible: [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)

The "kernel" value in /boot/grub/menu.lst should have ```
root=/dev/mapper/<name of encrypted root partition>
``` and not "root=/dev/<lvm_vg>/<lvm_lv>" as I wrote in my last post. Since I named my encrypted root partition "root" the correct value here is ```
root=/dev/mapper/root
```


/etc/crypttab should have a line something like this:
```
<name of encrypted root partition> /dev/<lvm_vg>/<lvm_lv> none luks,retry=1
```
Which in my case is:
```
root /dev/lvm_disk/root none luks,retry=1
```


/etc/fstab should then have this line
```
/dev/mapper/<name of encrypted partition> / ext3 defaults,errors=remount-ro 0 1
```
Again, in my case this is:
```
/dev/mapper/root / ext3 defaults,errors=remount-ro 0 1
```


Otherwise it really is pretty much straight forward, just keep your tongue in the right mouth when setting paths and check tty1 (ctrl-alt-f1) if the system won't boot as that'll probably tell you what's wrong.

---

