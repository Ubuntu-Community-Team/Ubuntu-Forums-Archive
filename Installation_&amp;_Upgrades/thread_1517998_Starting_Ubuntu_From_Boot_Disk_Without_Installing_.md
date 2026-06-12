---
title: "Starting Ubuntu From Boot Disk Without Installing Grub"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by chopsuwe on 2010-06-25
I have Ubuntu 9 installed and was using the Vista boot loader to start it by following the instructions [here]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx"). Some time during the last two years I lost the Grub entry from the Vista boot loader so can no longer start Grub and Ubuntu. 

I still have the linux.bin file but the method in that link no longer works. Is it possible to start the installed copy of Ubuntu using a boot disk, either a live disk or from a USB stick since there is no floppy drive

Hard Drive setup:
Partition 1: Hidden recovery 
Partition 2: Vista (and Vista boot loader) NTFS
Partition 3: Files and stuff NTFS
Partition 4: Extended partition containing Partition 5 and 6
Partition 5: Empty
Partition 6: Ubuntu 9 EXT (3?)

---

### Post by chopsuwe on 2010-07-01
Does any one know?

---

### Post by dino99 on 2010-07-01
install grub-pc on your ubuntu partition

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-07-01
You should be able to install grub or grub2 to your USB if you can boot from USB and then manually create a boot stanza for your existing Ubuntu install.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

If grub2:
menuentry "Latest Kernel" {
insmod ext2
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
}

---

### Post by chopsuwe on 2010-07-16
What a gold mine of information you have there oldfred!

I've come up with a new plan. Ubuntu is gone. The Vista recovery partition (accessed by hitting F9 just after boot) will be modified to boot into Puppy Linux instead. That should eliminate all the messy boot loaders!

It'll be some months before I have time so will tag this as solved.

---

