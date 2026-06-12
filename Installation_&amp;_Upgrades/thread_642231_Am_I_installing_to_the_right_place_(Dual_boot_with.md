---
title: "Am I installing to the right place? (Dual boot with Vista bootloader)"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Minchino on 2007-12-16
Hello, I am trying to dual boot Vista and Ubuntu 7.10 whilst still using the Vista Bootloader (as per this guide: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu))

I am however somewhat dubious about whether or not I am actually going to be installing to the right partition, and get the grub on the linux partition.

My lone hard drive is as following

Partition 1 - EISA recovery config
Partition 2 - Vista ~25GB - Basic Partition
Partition 3 - Documents ~75GB Logical Partiton
[10GB empty space] - where I want to install Ubuntu (and the grub)

Following the guide I selected to format 10GB with ReiserFS (and hopefully selected it as the location for Ubuntu to be installed)

As it stands, the setup reads:

The Partition Tables of the following devices are changed:
SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
Partition #4 of SCSI1 (0,0,0) sda as reiserfs

with the device for the bootloader set as (hd0,0) <-- is this right, (how will it know to use partition 4?) (should this not read (hd0,3) or (hd0,4), and if so, should it not be the same above?)

will all three existing partitions and the vista bootloader remain unmodifed?

Also on a side note, I made no partiton for a swap file (I have practically no experience with linux, but am assuming this is like a page file?)  Is this essential/highly recommended, does it effect performance (2GB of RAM), and can it be done at a later date / put on the linux partition.

thanks in advance for any help, sorry if this is blatantly obvious etc.

---

### Post by Pumalite on 2007-12-16
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

You can add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1) Install Ubuntu. On the last screen click on the "advanced" button and replace (hd0) by /dev/sda3. (Here you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Step 4) Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by Minchino on 2007-12-16
I'm afraid using /dev/sda4 as the location to install grub did not work, gave me:

Executing 'grub-install /dev/sda4' failed

This is a fatal error.

I'm guessing it wants the format (hd0,x) instead.

/dev/sda1 is EISA
/dev/sda2 is Vista
/dev/sda5 is Documents
/dev/sda4 is the ubuntu partition.

Any ideas about how I can make sure it does not overwrite vista bootloader?

---

### Post by Pumalite on 2007-12-16
There is no problem with Grug overwriting your Vista MBR. Usually it comes up with both options and if not, it can be chain loaded. In fact Grub is the best boot loader there is. Period.
(make sure you allocated space for Ubuntu with the Vista partitioner in the first place. It also helps when Windows is installed first and Ubuntu last)

---

### Post by talsemgeest on 2007-12-21
Yoy can try overwriting the windows bootloader with the grub, following the instructions of pumalite, and then overwriting the grub with the windows bootloader. That should work.

---

