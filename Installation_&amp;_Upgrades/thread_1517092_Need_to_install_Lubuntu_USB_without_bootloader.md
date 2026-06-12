---
title: "Need to install Lubuntu USB without bootloader"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by Fireclown on 2010-06-24
Hi, I recently installed Lubuntu to a USB. It was up and running and worked fine, however, upon exiting and going to boot into windows, I noticed it had installed a GRUB bootloader. I use whole disk encryption on windows, which has its own bootloader, so I can't be having some other bootloader on the PC interfering with this. I used my rescue disk to restore my WDE bootloader, but the USB stick will not boot now. 

I also tried using pendrivelinux but this copies the live cd version onto the USB stick and nothing saves when you log off.

Any ideas for installing Lubuntu to USB without a boot loader?

---

### Post by kalistona on 2010-06-24
instal grub on your desk in windows ? no.
on usb, 'bootloader" is on usb, anyway you should create it with a tool less 'nervous' so you must  look what is the difference between all the softs and choose one :
multiboot (this one seems be the right)
usb live creator
universal installer
ubuntu creator

---

### Post by Fireclown on 2010-06-24
bump

---

### Post by jards on 2010-06-25
Hey, man.

When you make a initiable usb in ubuntu, you can choose to save data in this media or do not save, only if you use a hard disk in your computer.

If you choose to save, it works fine, saves preferences, archives, etc.

I have one USB like that with Lucid Lynx, and I use it on my sister´s laptop and in the computer of my job.
Works fine, just get to much time to begin.

The usability depends on the size of your USB.

Hope it helps.

---

### Post by C.S.Cameron on 2010-06-25
You can use usb-creator from the live CD to make a persistent flash drive that saves changes.
Or you can do another Full install but after partitioning click the Advanced button and select to install grub to the flash drive root, ie sdb not sdb1.
Or you can disable your hard drive before creating the flash drive which is fool proof.

---

