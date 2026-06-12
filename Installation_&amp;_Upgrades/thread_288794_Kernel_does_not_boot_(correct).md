---
title: "Kernel does not boot (correct)"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by BAzfH on 2006-10-30
Hi there,

i'm not sure if my problems are really related to the update cause i had similar (but _not_ equal) problems with my dapper installation i had not resolved yet. Well: 

The symptom first: My kernel does not boot by itself. The details:

Running update-grub leads into this output:
schoenfeld@teekanne:~$ sudo update-grub
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.17-10-386
Found kernel: /vmlinuz-2.6.15-27-386
Found kernel: /vmlinuz-2.6.15-23-386
Found kernel: /vmlinuz-2.6.12-9-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

... which is obviously wrong, because the kernels under / does not even exist, but they exist under /boot. So kernel says 'File not found' when trying to boot. But it does not make a difference if i change / to /boot it won't boot either. The only solution to get it to boot is to change /vmlinuz-<version> to /vmlinuz and the same for initrd. Interesting is: This is a symlink on the current kernel, as ls proves:
   
lrwxrwxrwx   1 root root    29 2006-10-30 10:30 initrd.img -> boot/initrd.img-2.6.17-10-386
lrwxrwxrwx   1 root root    26 2006-10-30 10:30 vmlinuz -> boot/vmlinuz-2.6.17-10-386

Well so far so good. But the result is really strange. Cause if i now do 'uname -a' on a console it does show up the following:

Linux teekanne 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Which is bad in my opinion. Because it seems that grub is booting the wrong kernel even though the image seems to be the right one. Another strange behaviour: Shouldn't edgy result in upstart as a replacement for init? As far as i heard there should be a difference between them (visual and 'felt' cause it should boot faster) but i don't see a difference. Even the theme is the same. Okay for better help here is the relevant menu.lst entry for the kernel it should boot (and the one it seems to boot):

title           Ubuntu, kernel 2.6.17-10-386
root            (hd1,0)
kernel          /vmlinuz-2.6.17-10-386 root=UUID=8c0d9e47-4f4e-4e5c-928a-786204661113 ro quiet splash
initrd          /initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.17-10-386 root=UUID=8c0d9e47-4f4e-4e5c-928a-786204661113 ro single
initrd          /initrd.img-2.6.17-10-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel          /vmlinuz-2.6.15-27-386 root=UUID=8c0d9e47-4f4e-4e5c-928a-786204661113 ro quiet splash
initrd          /initrd.img-2.6.15-27-386

Infos about disk layout / partitioning:

schoenfeld@teekanne:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  83  Linux
/dev/sda2   *           7        5106    40965750   83  Linux
/dev/sda3            5107        9568    35841015   83  Linux
/dev/sda4            9569        9729     1293232+  82  Linux swap / Solaris

Mounting as follows:
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
/dev/sda1 on /boot type ext3 (rw)
/dev/sda3 on /home type ext3 (rw)

Fstab:
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=8c0d9e47-4f4e-4e5c-928a-786204661113 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=f01db327-a9b0-4770-bcea-8ca2e05ed170 /boot ext3 defaults 0 2
# /dev/sda3 -- converted during upgrade to edgy
UUID=d2e24fa8-07a0-4576-a522-64b910a848e8 /home ext3 defaults 0 2
#/dev/hda1       /media/hda1     ext3    defaults        0       2
ä/dev/hda5       none            swap    sw              0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=fcfcb9c9-9582-44fd-8c2b-6b01b25c9dad none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Oh well another strange thing:
swap isn't mounted since update anymore. :o)

Any help appreciated. if you need further information feel free to ask for it.

Thanks in advance

Patrick

---

### Post by BAzfH on 2006-11-02
None around who can help me?

---

