---
title: "error message: symbol 'grub_puts_' not found"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Idun on 2010-05-03
[LEFT]Hi!
Today I installed the netbook edition of lucid on my asus 901. I got no error messages during the installation, everything seemed fine until I tried to boot into the new system. Grub gave an error message: symbol 'grub_puts_' not found.

I began looking for a way to solve this, and tried this guide:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

Unfortunately it didn't help me at all, I still get the same error message.

I would be very grateful if someone helped me.

Thanks!
[/LEFT]

---

### Post by willbradley on 2010-06-02
I just had the same exact problem and found a solution. Please leave your feedback!


[SIZE="4"]HUGE WARNING: I am a Linux noob! Following the below instructions could very well make your computer explode and cause 1000 years of highly-prized award-winning photos to vanish from your computer, never to be recovered again. You do this at your own risk.[/SIZE]

That said, this is how I managed to fix this problem without doing the things mentioned on this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) -- my setup was Windows 7 with Ubuntu Netbook Remix 9.10, installed in that order, with all defaults, on an Acer Aspire netbook. During the automatic upgrade to UNR 10.04 it asked me details about my partitions and GRUB configuration, but I guess I answered wrong and got this grub_puts_ error on the next reboot.


Download Ubuntu 10.04 Netbook Remix and put it on a CD or USB drive. Boot to it (it should boot into Ubuntu itself like a Live CD) and open up a Terminal window and type the commands below (ignore # as it represents the console.)

Based on [http://readlist.com/lists/lists.ubuntu.com/ubuntu-users/29/149961.html](http://readlist.com/lists/lists.ubuntu.com/ubuntu-users/29/149961.html) --

# **sudo fdisk -l**
*Here you will see a list of partitions. This will be similar to the blkid command below. With these two commands, try to determine which hard drive contains Linux (and thus GRUB) -- it will probably be /dev/sda but possibly something else. (sda1, sda2, etc are partitions. sda is the disk.)*

# **sudo blkid**
[I]You'll see something like this:
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="D658AED058AEAEA5" TYPE="ntfs" 
/dev/sda2: LABEL="COMPAQ" UUID="F6B054EDB054B5B9" TYPE="ntfs" 
/dev/sda3: LABEL="FACTORY_IMAGE" UUID="1E28AA6F28AA459D" TYPE="ntfs" 
/dev/sdb1: UUID="8d3e648a-983d-4d69-aa3c-83798ec4683f" TYPE="ext3" **This is the only 'ext3' partition on this example system, and so is the only logical place where Linux and /boot would be.**
/dev/sdb3: UUID="309896A798966ADC" TYPE="ntfs" 
/dev/sdb5: UUID="8dc30fea-2893-414f-a42c-3de06e2c8a95" TYPE="crypto_LUKS" 
/dev/sdc1: SEC_TYPE="msdos" UUID="4870-FD6B" TYPE="vfat" [/I]

# **sudo mount /dev/sdb1 /mnt** *NOTE: use this if, like me, Ubuntu was installed all on one partition. Otherwise you need to mount your /boot partition in /mnt/boot and your / partition in /mnt -- also, make sure you're using the partition you identified as being Linux in the above steps, not necessarily /dev/sdb1 as in this example.*

# **sudo mount -t proc none /mnt/proc** *I believe this command and the below command mount various system directories between your USB/CD Ubuntu and your mounted HDD Ubuntu. Without this, I'm guessing chroot or grub-install won't work.*

# **sudo mount -o bind /dev /mnt/dev**

# **sudo chroot /mnt /bin/bash** *I believe this command puts your terminal inside of your HDD Ubuntu.*

# **grub-install /dev/sdb1** *Remember to change /dev/sdb1 to the partition you identified as likely being /boot*
If you get an error here, especially one about how installing to a partition is a bad idea, continue on to the next command.

# **grub-install /dev/sdb** *Remember to change /dev/sdb to the hard drive you believe Linux is on.*
This command should work cheerfully (if not try typing sudo before it) and upon reboot GRUB should come up properly (at least it did on mine, yay!) If not, sorry chap, keep Googling.

---

