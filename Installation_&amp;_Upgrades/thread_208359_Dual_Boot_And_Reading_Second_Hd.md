---
title: "Dual Boot And Reading Second Hd"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by hacker on 2006-07-03
Neather one of my dual boot programs will work. Ubuntu has grub installed but it does not show my windows HD on boot up and my Boot Manager OSl2000 that I am running on my windows HD does not show the ubuntu hard drive on boot up.
Ubuntu shows all my HD'S; I can read the USB drives ok  but the secondary master HD it will not open so I can read the files. What did I do wrong??

          HACKER

---

### Post by FenrisAbraxas on 2006-07-03
You have to manually add the entries to grub using this values:

```

sudo vi /boot/grub/menu.lst
title Window$ Partition
rootnoverify (hdx,x) //this should be the partition where the ntldr and boot.ini are actually placed
chainloader +1

title Ubuntu
root (hd0,1) //<--- this should point your root partition :D
kernel /vmlinuz-2.4.7-10 ro root=/dev/hda3 hdc=ide-scsi //this part should be already into your menu.lst
initrd /initrd-2.4.7-10.img // this must be there as well :P

```

This will let you choose between Ubuntu and Windows partitions at boot.

Now if your problem is that you can't see the windows partitions in Ubuntu do this:

```

sudo vi /etc/fstab

```

Then you should add the partitions like this:

```

# Device  Dir/Mountpoint     FS       Options

/dev/hda1      /              ext2     defaults    1 1
/dev/hda2      /home          ext2     defaults    1 2
/dev/hda3      /tmp           ext2     defaults,noexec
/dev/hda4      none           swap     defaults

none           /proc          proc     defaults

/dev/hda8     /mnt/windows/c   vfat     auto,user,noexec,rw 0 0
/dev/hda9     /mnt/windows/d   ntfs     auto,user,exec,ro 0 0

```

This will allow you to see the windows partitions inside Ubuntu.

And AFAIK theres no way to see the Linux partitions from windows, and if there's a way you have to download something because Windows just can see vfat and ntfs partitions :P

I hope this helps you, because i didn't got quite well your question.

Good luck

---

