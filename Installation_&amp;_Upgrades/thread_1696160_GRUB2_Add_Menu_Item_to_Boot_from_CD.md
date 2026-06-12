---
title: "GRUB2: Add Menu Item to Boot from CD?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by pc_michael on 2011-02-27
Is there a way in Grub2 to add an item to the grub menu to boot from optical media?  So if you didn't get the boot disc inserted in time, once you hit GRUB you can use that to initiate the boot from disc?

I've been Googling for a while, but the only thing I can find is how to boot grub from a CD, which is not what I'm looking for.

---

### Post by rykel on 2011-12-10
I am interested to know how to add a menu entry to grub2 too... I am trying to add PLOP Boot Manager (plpbt.bin) specifically in this case. Is there a GUI to do this simple task?

---

### Post by oldfred on 2011-12-10
I have never tried these entries that I saved. Let us know if any work.

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz

# Of course the set root has to be to your drive & partition, but the drive you set in BIOS to boot is usually hd0.
menuentry "Plop Boot Manager Install"{
set root='(hd0,1)'
linux16 /boot/plpbt.bin
}

I now only loopmount/boot ISO from hard drive partition or USB with grub2. I stopped burning CDs a while ago, as I also would make several emergency disks before a new install and was going thru a lot of CDs.

---

