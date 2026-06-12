---
title: "Formatted Windows in dual-boot setup... need to get back ubuntu..."
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by majorkonig1337 on 2008-06-28
Hey, I need to get back grub so that I can get back into ubuntu.
I tired the following but to no avail..
> Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.
When I do this.. after choosing the partitions.. It wont let me proceed unless I select format. I selected my existing ubuntu partition as "/" and swap as "swap".
AND
> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
In this, no matter what sequence of partition number I try, I cant get through, I've tired the most obvious and most extreme...

> 1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/hda4 /mnt/ubuntu (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/hda
8. Exit the shell
9. Reboot
When performing the "mkdir /mnt/ubuntu" command, it says access denied!


Can anyone recommend a simple and easy way.
Thanks a lot!

---

### Post by Miljet on 2008-06-28
Hate to tell you this, but if you formatted your Windows partition, you probably trashed your entire hard drive. Windows formatting tools don't recognize Linux partitions and try to include them in the Windows partition.

---

### Post by majorkonig1337 on 2008-06-28
> Hate to tell you this, but if you formatted your Windows partition, you probably trashed your entire hard drive. Windows formatting tools don't recognize Linux partitions and try to include them in the Windows partition.
I have 3 HDD's my old original 80GB WD, a WD500 for storage and a new 500GB 7200.11. I used to have XP and Ubuntu on on the 80GB one. I wanted to install XP on the 7200.11, so I deleted the "C" partition on the 80GB one and made a new one on the 7200.11.
In the partition maker during XP setup, I could see the Ubuntu and Swap partition listed as "unknown".
I just want to getback ubuntu so I can finish my downloads and then.. format the whole 80GB HDD and use the whole thing for ubuntu.

Thanks.

---

### Post by Pumalite on 2008-06-28
Post:
sudo fdisk -lu
(booting your Live CD)

---

