---
title: "get out of initramfs"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by spookywooky5 on 2019-02-22
I have sent the following email to [email]boot.repair@gmail.com[/email] and also posting here.

Hello,



**PASTEBIN** : [http://paste.ubuntu.com/p/c36K9j38Br/](http://paste.ubuntu.com/p/c36K9j38Br/)



After a few months of using** Ubuntu(18.04)**, there were a lot of applications and programs installed on my system so I decided to reset it with **Resetter**
(**[https://github.com/gaining/Resetter](https://github.com/gaining/Resetter)**).
It worked and my system was reset but it kept popping up "**System Problem Detected**" messages at seemingly random times.
So  today I used boot repair on my system and I put in commands given to me  by the program. But when I entered the commands, I kept getting errors
like **grub-efi-amd64-signed requires** grub-efi-amd64-bin and grub-commons.
So I manually installed the specific versions it asked me for and decided to reboot.


After rebooting I saw grub console screen which wasn't a new thing to me. To get out of it I tried to follow -
**[https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot?rq=1](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot?rq=1)**
which had worked for me before but didn't work this time. So i followed -
**[https://www.linux.com/learn/how-rescue-non-booting-grub-2-LINUX](https://www.linux.com/learn/how-rescue-non-booting-grub-2-LINUX)**
This method worked for me,  but when i entered boot in grub-console, it gave an error something like "Video error, booting in **blind mode**."
and booted me to **initramfs(BusyBox).**


When I tried to exit, it gave me long output and the last line was something like "<trace 0fmnafdjalsjfa>"
Please suggest what steps I should take next.


'''
grub-efi-amd64-signed purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

''''



**/mnt/ubuntu/etc/fstab**

===========

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=6152f85c-6a70-4534-a17e-b8ada666afd9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=af752c7b-44c7-4d65-82e4-fe130f66cea8 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=51389824-ef47-47f5-b2e5-dc88c6051d10 none            swap    sw              0       0
UUID=0491-8E62    /boot/efi    vfat    defaults    0    1

=====


***I have a dual-boot system with Windows 10 and Ubuntu.***
I have backups of ubuntu so i am ready to delete it if I have to but I cannot lose the data on Windows 10.

Thanks in advance,
Aditya

---

### Post by spookywooky5 on 2019-02-22
I have access to a live USB.
To get Windows can I just delete Ubuntu partitions and boot normally into windows?

---

### Post by spookywooky5 on 2019-02-24
I solved the problem.

If anyone is interested, I used the liveUSB to mount my /home directory  and take backups of all the files I needed.
Then I deleted the Ubuntu partitions entirely.
I found a way to boot into windows by pressing <ESC> key on my keyboard while booting then, 

Run UEFI application... > Select HDD > Select EFI partition > /Microsoft/Boot/bootmgmf.efi
and I booted into windows.
But my grub rescue problem was still present so then I reinstalled Ubuntu and it was fixed.

---

