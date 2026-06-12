---
title: "MBR rewritten- no linux entry"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2010-02-20
I updated my lucid alpha testing (64 bit)install after which I am unable to boot into any of my Ubuntu installs(sda11 has a dedicated Burg partition and sda10 has the stable karmic (32 bit)install and sda9 has the testing lucid install)
Now I am trying to recover (rewrite Burg or at least grub2 on the MBR) my installs

This is what happens
custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount -o bind /dev /mnt/dev
custom@custom:~$ chroot/mnt
bash: chroot/mnt: No such file or directory
custom@custom:~$ chroot /mnt
chroot: cannot change root directory to /mnt: Operation not permitted
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$

i tried a slightly different code
with little sucess

custom@custom:~$ sudo mount /dev/sda10 /mnt
mount: /dev/sda10 already mounted or /mnt busy
mount: according to mtab, /dev/sda10 is already mounted on /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$


custom@custom:~$ whereis sh
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
custom@custom:~$ whereis chroot
chroot: /usr/sbin/chroot /usr/share/man/man8/chroot.8.gz
custom@custom:~$ whereis dash
dash: /bin/dash /usr/share/man/man1/dash.1.gz

I also ran a whereis for bash and it also is there

---

### Post by richlyn9 on 2010-02-20
i ran a fdisk

custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64ca64c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 5099 20474842+ 7 HPFS/NTFS
/dev/sda3 5100 19457 115330635 f W95 Ext'd (LBA)
/dev/sda5 5100 8953 30957223+ 7 HPFS/NTFS
/dev/sda6 8954 12809 30973288+ 7 HPFS/NTFS
/dev/sda7 12810 16633 30716248+ 7 HPFS/NTFS
/dev/sda8 16634 16764 1052226 82 Linux swap / Solaris
/dev/sda9 16765 18110 10811713+ 83 Linux
/dev/sda10 18111 19325 9759456 83 Linux
/dev/sda11 19326 19457 1060258+ 83 Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae1f8566

---

### Post by darkod on 2010-02-20
If /dev/sda10 is Karmic all you need to do is boot into karmic live desktop and do:

sudo mount /dev/sda10 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That's it. That will install grub2 on the MBR of /dev/sda using /dev/sda10 as root partition.

And for your information, before you can chroot into an install you need few more steps. It would be:

sudo mount /dev/sda10 /mnt
sudo --bind /proc /mnt/proc
sudo --bind /dev /mnt/dev
sudo --bind /sys /mnt/sys
sudo chroot /mnt

After finishing what you want to do:

umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

---

### Post by richlyn9 on 2010-02-20
> **darkod said:**
> If /dev/sda10 is Karmic all you need to do is boot into karmic live desktop and do:

sudo mount /dev/sda10 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That's it. That will install grub2 on the MBR of /dev/sda using /dev/sda10 as root partition.

And for your information, before you can chroot into an install you need few more steps. It would be:

sudo mount /dev/sda10 /mnt
sudo --bind /proc /mnt/proc
sudo --bind /dev /mnt/dev
sudo --bind /sys /mnt/sys
sudo chroot /mnt

After finishing what you want to do:

umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

thanks...
i will try that
i was kinda loosing hope after 2 weeks of trying to chroot

---

### Post by richlyn9 on 2010-02-20
Apparently i am trying to install Burg which has a dedicated partiton sda11
nevertheless i can still go with grub2 though this will be my last resort

I tried the above codes to chroot

custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo burg-install --root-directory=/mnt/ /dev/sda11
sudo: burg-install: command not found
custom@custom:~$ sudo mount /dev/sda10
mount: /dev/sda10 already mounted or /mnt busy
mount: according to mtab, /dev/sda10 is already mounted on /mnt
custom@custom:~$ udo --bind /proc /mnt/proc
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
bash: udo: command not found
custom@custom:~$ sudo --bind /proc /mnt/proc
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
custom@custom:~$ sudo --bind /dev /mnt/dev
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
custom@custom:~$ sudo --bind /sys /mnt/sys sudo chroot /mnt
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
custom@custom:~$ 

it gave me this error

anything that i typed wrong?

---

### Post by darkod on 2010-02-20
I don't know why it's giving you those errors, the commands are correct. Unless it got confused by trying the burg-install command and trying to mount /dev/sda10 twice.

But for a simple grub2 reinstall to the MBR of /dev/sda you DON'T need chroot at all, so why are you insisting on it?

Just boot the karmic live desktop and do:

sudo mount /dev/sda10 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 with /dev/sda10 as root partition.

If you want to keep using burg and that's what you are trying to install, I have no idea about burg commands. I'm talking about reinstalling grub2 from karmic.

---

### Post by darkod on 2010-02-20
I figured it out, I made a typo in my instructions, sorry:

sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys

---

### Post by richlyn9 on 2010-02-21
i will just install grub2
however i am intrigued bu the chroot and want to see it through

i tried that and got the same error  "**/bin/bash': Exec format error**" that has been bugging me for a week


custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount --bind /proc /mnt/proc
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo mount --bind /sys /mnt/sys
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$ sudo chroot/mnt
sudo: chroot/mnt: command not found
custom@custom:~$

---

### Post by kansasnoob on 2010-02-21
> i am intrigued bu the chroot and want to see it through

Not sure, but this might be helpful:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by richlyn9 on 2010-02-22
[B][I][COLOR="Purple"][SIZE="4"]wwwwwwwwwwwwwwooooooooooooooooohhhhhhhoooooooooooooooooooo:D:o:P
i Have done  it.......
i have at last been able to chroot !!!!!![/SIZE][/COLOR][/I][/B]

---

### Post by richlyn9 on 2010-02-22
> **richlyn9 said:**
> [B][I][COLOR="Purple"][SIZE="4"]wwwwwwwwwwwwwwooooooooooooooooohhhhhhhoooooooooooooooooooo:D:o:P
i Have done  it.......
i have atlast been able to chroot !!!!!![/SIZE][/COLOR][/I][/B]
[I]
i was mounting  a different partition altogether
such an *** of me....[/I]

---

### Post by richlyn9 on 2010-02-22
heres what i did............


custom@custom:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919828+   b  W95 FAT32
custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64ca64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5099    20474842+   7  HPFS/NTFS
/dev/sda3            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100        8953    30957223+   7  HPFS/NTFS
/dev/sda6            8954       12809    30973288+   7  HPFS/NTFS
/dev/sda7           12810       16633    30716248+   7  HPFS/NTFS
/dev/sda8           16634       16764     1052226   82  Linux swap / Solaris
/dev/sda9           16765       18110    10811713+  83  Linux
/dev/sda10          18111       19325     9759456   83  Linux
/dev/sda11          19326       19457     1060258+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae1f8566

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31871   256003776   83  Linux
/dev/sdb2           31872       60801   232380225   83  Linux

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919828+   b  W95 FAT32
custom@custom:~$ sudo mount /dev/sda9 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl 
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
[COLOR="Navy"]"I manually mounted the dedicated Burg partition "[/COLOR]
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
root@custom:/# update-burg
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
done
root@custom:/# lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
root@custom:/# uname -m
i686
root@custom:/# sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
sudo: unable to resolve host custom
umount: /mnt/dev/pts: not found
root@custom:/# exit
exit
custom@custom:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
custom@custom:~$

---

### Post by richlyn9 on 2010-02-22
[I][COLOR="Navy"]i am able to chroot to karmic existing install
however i am not able to install Burg on the MBR or the dedicated partition
or rather the update-burg does not find my existing ubuntu installs
what can the matter be?

what am i doing wrong[/COLOR][/I]

root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
"I manually mounted the dedicated Burg partition "
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
root@custom:/# update-burg
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
done

---

### Post by richlyn9 on 2010-02-24
i tried that again
it gave me another error this time

root@custom:/# burg-install --root-directory=/mnt/ /dev/sda11
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sda11
sudo: unable to resolve host custom
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# burg-install --root-directory=/mnt/ /dev/sda11
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# sudo burg-install "(sda11)"
sudo: unable to resolve host custom
/usr/sbin/burg-setup: error: no mapping exists for `sda11'.

---

### Post by darkod on 2010-02-24
Any particular reason you insist on BURG instead of GRUB? As I already said, reinstalling grub2 should be no problem, if you know which is your ubuntu partition. If not, the boot info script will show you.
After that reinstalling grub2 to the MBR takes only two commands.
Not sure why burg is giving you these errors, it might not like installation to a partition as grub2 doesn't like also.
And even if you install burg to /dev/sda11, what bootloader will you use to chainload to it?

---

### Post by richlyn9 on 2010-02-25
its done.....


root@custom:/# burg-install --force --root-directory=/mnt/ /dev/sda11


root@custom:/# sudo update-burg
sudo: unable to resolve host custom
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
root@custom:/#


though i didnt find the karmic install...
after rebooting it did show up the karmic kernels and was able to boot in to Karmic install.
Now everything is working fine as before 



i admit i was a bit adamant on installing Burg and that to a dedicated partition by chroot, but its a good experience  learning  chroot and worth the wait!!!

Thanks Darkod and kansasnoob

---

