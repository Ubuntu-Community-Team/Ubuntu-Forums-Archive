---
title: "Installed Edbuntu,now i cant install windows."
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by insom234 on 2007-02-16
So i decided to install edbuntu on a system for my niece and nephew,i installed it on one of my machines first to show it to my sister so she could make sure she wanted to do it.
I went to install windows back on my machine,but the gnu grub thing is stopping the xp installation cd from booting.
I have looked through many forum pages and had no luck,the only things i could find where fixes for machines that had dual boot setups,this is not my case, i have nothing installed on the system except for edbuntu and i am completely stuck,
any help would be greatly appreciated.

---

### Post by alyoung on 2007-02-16
If grub is appearing as a boot loader, you are booting from hard drive rather that CD-ROM drive, I think.

Check your BIOS boot order.

---

### Post by insom234 on 2007-02-16
My boot order is cdrom then hdd.

---

### Post by alyoung on 2007-02-16
That's odd.

I sometimes have problems booting from CDs if I insert the disk at just the wrong time.

Trying taking the disk out and putting it back in, as silly as this sounds.

---

### Post by insom234 on 2007-02-16
I have tried and tried,i tried going through the edbuntu setup and deleting all the partitions but it still didnt get rid of the grub,so i reinstalled edbuntu,checked the boot order all of that,still wont run the xp installation disc,when i boot it goes straight from the screen where you can bring up your bios,to the screen where you can hit esc to go into the gnu grub screen with the ubuntu,ubuntu recovery,and ubuntu memtest options.

---

### Post by alyoung on 2007-02-16
Do you have any DOS or similar boot floppies?

---

### Post by insom234 on 2007-02-16
no,i dont,and none of my machines have floppy drives,just cd and dvd.

---

### Post by Snowbat on 2007-02-16
As alyoung points out, if GRUB bootloader is starting, the BIOS in your computer has already decided to boot from the HD.  If your boot order shows the CD drive first, this may be due to a non-bootable CD or an unreadable CD in the drive.

Which computer is it?  On some you can hit an F key during POST to bring up a boot menu where you can select the drive/device to boot from.

Do you see a CD drive activity light and/or hear the CD drive being accessed after POST?

Does the computer boot from your Edubuntu CD?

Have you tried cleaning your Windows CD?

Have you tried to boot another computer with your Windows CD?

---

### Post by insom234 on 2007-02-16
Thanks for everyones help,
i actually fixed it by making a disk[cd] that booted to dos,then using the fdisk utility.
Thanks again to everyone for your help.

---

