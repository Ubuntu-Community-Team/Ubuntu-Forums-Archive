---
title: "multiboot startup problem grub or kernel - no chroot possible"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by unrouted. on 2017-02-14
Hello,

i have a problem with chroot (for repair) into an defective multiboot system.

The System was:
sda1 Win 7, NTFS
sda2 linux swap
sda3 Xubuntu 16.04, ext4
sda4 data

The system works before. It was damaged by gparted and partition tools (resize partition)

The current state is that grub is available and i can boot into Windows 7.
But if i want to boot into Xubuntu there are two kernels available
4.4.0-31-generic --> brings me to a reboot only
4.4.0-47-generic --> brings me to an error message "... have to load kernel fist..."

So i read much posts about chroot into system via live cd and repair grub and/or kernel.
As grub was available i think the main problem is the kernel?
(another thing is, that the folder /boot/ has no file vmlinuz-4.4.0-47-generic only the file vmlinuz-31-generic)

I have done the following:
1. boot with xubuntu cd in live mode
2. open the terminal
3. xubuntu@xubuntu: ~$  sudo su
4. root@xubuntu: / home/xubuntu# cd ..
5. root@xubuntu: / home# cd ..
6. root@xubuntu: /# mount -o rw,exec /dev/sda3 /mnt
--> files are available on /mnt

7. root@xubuntu: /# for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"; done
8a. root@xubuntu: /# sudo chroot /mnt
--> Error -> chroot: failed to run command '/bin/bash': No such file or directory
--> After check of directory -> Yes it's correct, there is no bash shell.
Maybe Xubuntu has an other shell? Test some other things...

8b. root@xubuntu: /# sudo chroot /mnt /usr/bin/xfce4-terminal
--> Error -> chroot: failed to run command '/usr/bin/xfce4-terminal': Permission denied

8c. root@xubuntu: /# sudo chroot /mnt /bin/dash
--> Error -> chroot: failed to run command '/bin/dash': Permission denied

8d. root@xubuntu: /# /usr/bin/xfce4-terminal
--> A terminal starts, but no chroot in target system :-(
--> This means it was mounted executable?

--> for example ls -l gives me root:root with -rwxr-xr-x on xfce4-terminal

So what's the failure??

Thanks!!

---

### Post by oldfred on 2017-02-15
Can you boot into recovery mode from your older kernel?

I have not seen " around the chroot mount. Do not know bash well enough to know if also correct or not.

[https://ubuntuforums.org/showthread.php?t=1581099](https://ubuntuforums.org/showthread.php?t=1581099)
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

Boot-Repair often a bit easier. Use advanced mode and total uninstall/reinstall of grub and check add new kernel.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

