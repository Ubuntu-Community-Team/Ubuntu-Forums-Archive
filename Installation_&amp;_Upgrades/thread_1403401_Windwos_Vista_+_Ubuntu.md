---
title: "Windwos Vista + Ubuntu"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by thrust on 2010-02-10
Hey

I started out installing Ubuntu 9.10 on an external USB hard drive, I didn't want to modify my windows vista drive. I plugged in the USB drive and inserted the CD, installed it on the drive. all when well until i tried to boot vista without the drive attached to my computer. i forgot that Grub exists on both drives when i install ubuntu. how to i modify grub to allow me to boot windows vista without the ubuntu hard drive attached to my computer.

your help is much appreciated.


Thanks

---

### Post by darkod on 2010-02-10
For multiple drives (also for int + ext combination) it's always best the check where grub will be installed. You can do this during install on the last screen before clicking Install, click on Advanced and it will show you.

In your case, plug in the ext hdd but boot with the 9.10 cd, Try Ubuntu option. That will load the live desktop from the cd.

First run:
sudo fdisk -l

to show you your drives and partitions. If you are unsure how to "read" these reulsts, post them here for confirmation of the exact commands you need to use. Otherwise, if you know what is what, proceed with:

ASSUMING your int hdd is /dev/sda, and your ext hdd is /dev/sdb, and the ubuntu (Linux) partition is /dev/sdb5 (which will be shown by fdisk results) you need to run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore any warnings. That will write generic windows bootloader on your int hdd if it's called /dev/sda. So you can boot vista straight from your int hdd. Then:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That will install grub2 on the MBR of your ext hdd, so you can boot both ubuntu and vista when you boot with the ext hdd as first option. With the ext hdd unplugged, vista just boots straight away from the int hdd.

If confused by any of this just post the fdisk results and I'll modify the commands for your particular case if needed.

---

### Post by shriramrs31 on 2010-02-10
hmmmm, it seems you have installed grub on the usb drives MBR. you have to install it in your vista hard drives MBR. any good GRUB how to will give you the hint on how to achieve it ;-)

Hope it helps.

(sorry did not see the super reply of darkod. ignore)

---

### Post by darkod on 2010-02-10
> **shriramrs31 said:**
> hmmmm, it seems you have installed grub on the usb drives MBR. you have to install it in your vista hard drives MBR. any good GRUB how to will give you the hint on how to achieve it ;-)

Hope it helps.

(sorry did not see the super reply of darkod. ignore)

It's the other way around. If you want to boot without the ext hdd, grub has to be on it, not on the int hdd. Under assumption you have ubuntu on the ext hdd. The grub config files are always in the ubuntu root partition and without the disk grub can't start. So it must not be on the int hdd.

Usually you would keep the windows bootloader on the int hdd MBR to boot windows without the ext hdd, and you would have grub on the ext hdd MBR.

---

### Post by thrust on 2010-02-12
well it took me a few days to try this out, but it did today.... It worked perfectly, thanks, very appreciated. Now i just need to get the proper ubuntu drivers for my laptop. thanks again.

---

