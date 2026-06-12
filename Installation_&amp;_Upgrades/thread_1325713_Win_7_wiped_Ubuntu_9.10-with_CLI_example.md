---
title: "Win 7 wiped Ubuntu 9.10-with CLI example"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Marti68 on 2009-11-13
Hi clever folks ;)
 
Thought I'd got the the hang of this; may even find this in the recuring issues forum
 
Laptop was an XP and 9.04 duel. Upped to 9.10 which prevented access to XP. Upped the XP partition to Win 7 thinking I'd got the hang of dueling Win** and Ubuntu. Result no grub/Ubuntu.
 
Found an excellent doc called Recovering Ubuntu after Installing Windows. Printed and followed carefully without success.
 
The Terminal commands and results are copied here. Are you able to spot what went wrong? Could I rescue a duel boot from this or should I just format and restart?
 
There are 11 emails in 9.10 Evolution Email I need. After that I'll happily wipe the HDD if necessary to get a reliable duelB.
 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74bd74bd
Device Boot Start End Blocks Id System
/dev/sda1 * 1 6374 51199123+ 7 HPFS/NTFS
/dev/sda2 8220 14593 51199155 5 Extended
/dev/sda5 10748 14571 30716280 83 Linux
/dev/sda6 14572 14593 176683+ 82 Linux swap / Solaris
root@ubuntu:~# mkdir /media/root
root@ubuntu:~# mount /dev//sda5 /media/root
root@ubuntu:~# ls /media/root
bin cdrom etc initrd.img lib media opt root selinux sys usr vmlinuz
boot dev home initrd.img.old lost+found mnt proc sbin srv tmp var vmlinuz.old
root@ubuntu:~# ls /media/root/boot
abi-2.6.28-11-generic config-2.6.28-14-generic initrd.img-2.6.28-15-generic System.map-2.6.28-16-generic vmlinuz-2.6.28-13-generic
abi-2.6.28-13-generic config-2.6.28-15-generic initrd.img-2.6.28-16-generic vmcoreinfo-2.6.28-11-generic vmlinuz-2.6.28-14-generic
abi-2.6.28-14-generic config-2.6.28-16-generic memtest86+.bin vmcoreinfo-2.6.28-13-generic vmlinuz-2.6.28-15-generic
abi-2.6.28-15-generic grub System.map-2.6.28-11-generic vmcoreinfo-2.6.28-14-generic vmlinuz-2.6.28-16-generic
abi-2.6.28-16-generic initrd.img-2.6.28-11-generic System.map-2.6.28-13-generic vmcoreinfo-2.6.28-15-generic
config-2.6.28-11-generic initrd.img-2.6.28-13-generic System.map-2.6.28-14-generic vmcoreinfo-2.6.28-16-generic
config-2.6.28-13-generic initrd.img-2.6.28-14-generic System.map-2.6.28-15-generic vmlinuz-2.6.28-11-generic
root@ubuntu:~# sudo grub-install --root-directory=/media/root dev/sda5
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.
-h, --help print this message and exit
-v, --version print the version information and exit
--root-directory=DIR install GRUB images under the directory DIR
instead of the root directory
--grub-shell=FILE use FILE as the grub shell
--no-floppy do not probe any floppy drive
--force-lba force GRUB to use LBA mode even for a buggy
BIOS
 
Thank for your guidance. First attempt at serious use of the CLI.

---

### Post by Irihapeti on 2009-11-13
I'd suggest booting off a liveCD and copying your Evolution .mbox files off manually. I don't use Evolution, so I don't remember where it keeps the .mbox files, except that they are in a hidden folder in your home directory, probably .evolution.

Now that 9.10 is using grub 2, you'll probably need a grub 2 recovery disk. This gentleman [http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html) may be able to help.

---

### Post by eakinc on 2009-11-13
Marti68,
You used sda5 which is a partition, you want sda the MBR "master boot record" 
Change 
root@ubuntu:~# sudo grub-install --root-directory=/media/root dev/sda5
to
root@ubuntu:~# sudo grub-install --root-directory=/media/root dev/sda
Erik

---

### Post by wilee-nilee on 2009-11-13
If your W7 is a upgrade version the key for it will not be accepted on-line with a wiped computer, but you can call the W7 team to get it verified with their help. 

I don't use evolution but I think like Thunderbird it accesses outside email accounts, so I assume that you have them saved and removed from the original email accounts.

---

### Post by eakinc on 2009-11-13
Marti68,
Upped to 9.10 which prevented access to XP.    
>>Upped to 9.10 which prevented access to XP.  
Did you upgrade or reinstall from CD?  Most likely just overwrote the /boot/grub/menu.list preventing XP boot.  Upgrade keeps the old grub, disk install moves to a whole new grub, which is longer configured from /boot/grub/menu.list.

>>Upped the XP partition to Win 7
Win just overwrote the MBR with grub on it.

You can have everything working and dual booting. ;)  You may find yourself using linux more than Win.

---

