---
title: "Can't install GRUB on lubuntu 18.04.4 32 bit EeePC"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by gnyav on 2020-04-03
So I have this EeePC and i used Lubuntu on it for some time, but then i had to format the drives as i started experimenting with different things on it. 
Long story short, I started installing Lubuntu again. On the live cd i opened Disk and formatted the two ssd that it has, with erase option enabled, and proceeded with the installation (on /dev/sdb, 16GB, as /dev/sda is only 4GB)

Everything went fine until the very end when it said it can't install grub on /dev/sda. i tried to change it to /dev/sdb, /dev/sdb1 or /dev/sda1 but every time it failed.
I'm not sure what is the problem, i searched different sites, tried to install it manually with boot-repair app from the live usb, but nothing helped.

The only thing different now is that i tried installing 18.04.4 desktop version, while the last time i had 18.04 alternative version, but i don't see why this should be an issue.
I see in some places people say to disable secure boot from bios, but i'm not even sure if this EeePC have that option to begin with. there is an option to set password in the bios, but it's disable. not sure if that is it.

as a side note i tried installing batocera on the /dev/sda and it went fine and is booting. then tried installing lubuntu again on /dev/sdb with batocera still on, and with batocera removed by format (with erase) but nothing changed

---

### Post by dmnur on 2020-04-03
Boot the installation media, open a terminal window and type the following command:
```
sudo fdisk -l
```

Then show the output of the command.

---

### Post by gnyav on 2020-04-03
Here it is
for some reason there is loop0 and zram0; zram1. i didn't have those before.
maybe it's because i had tried debian lxqt or zorin lite?


/dev/sdc is the live usb 
```
Disk /dev/loop0: 1 GiB, 1115181056 bytes, 2178088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.8 GiB, 4034838528 bytes, 7880544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 29CA3425-0840-40C4-8A88-33FA6E41D9FE

Device     Start     End Sectors  Size Type
/dev/sda1   2048 7876607 7874560  3.8G Linux filesystem


Disk /dev/sdb: 15 GiB, 16139354112 bytes, 31522176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6c0707d7

Device     Boot Start      End  Sectors Size Id Type
/dev/sdb1        2048 31520767 31518720  15G 83 Linux


Disk /dev/sdc: 28.9 GiB, 31009800192 bytes, 60566016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1666820e

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 60566015 60563968 28.9G  c W95 FAT32 (LBA)


Disk /dev/zram0: 483.3 MiB, 506806272 bytes, 123732 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 483.3 MiB, 506806272 bytes, 123732 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

---

### Post by dmnur on 2020-04-03
Loop and zram devices here are created by the live environment, ignore them.

Let's try to install GRUB manually from chroot and see if there will be any errors:
```
sudo -i
mount /dev/sdb1 /mnt
mount -t proc /proc /mnt/proc
mount --rbind /sys /mnt/sys
mount --rbind /dev /mnt/dev
mount --rbind /run /mnt/run
chroot /mnt /bin/bash
grub-install /dev/sdb
update-grub
```

---

### Post by gnyav on 2020-04-03
It worked! no errors shown.
should i try booting now, or there is more work to do here? 

```
[COLOR=#000000][FONT=&quot]lubuntu@lubuntu:~$ sudo -i[/FONT][/COLOR]root@lubuntu:~# mount /dev/sdb1 /mnt
root@lubuntu:~# mount -t proc /proc /mnt/proc
root@lubuntu:~# mount --rbind /sys /mnt/sys
root@lubuntu:~# mount --rbind /dev /mnt/dev
root@lubuntu:~# mount --rbind /run /mnt/run
root@lubuntu:~# chroot /mnt /bin/bash
root@lubuntu:/# grub-install /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
root@lubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-28-generic
Found initrd image: /boot/initrd.img-5.3.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done [COLOR=#000000][FONT=&quot]root@lubuntu:/# [/FONT][/COLOR]
```

---

### Post by oldfred on 2020-04-03
Default install of grub would be to sda and it is gpt partitioned.
For grub in BIOS mode to install to gpt partitioned drive, you must have a 1 or 2MB unformatted partition with bios_grub flag.

Your sdb drive is MBR(msdos) partitioned and grub will install without added partition as there is some extra space in the sectors just after the MBR for grub2's core.img file which we do not see, but included the code to find the full Ubuntu/grub in the / (root) partition. MBR is too tiny for grub2's boot code.

---

### Post by gnyav on 2020-04-03
i went ahead and tried to boot, and it booted, but new problems occurred. it loads only the wallpaper.
after a minute or so, a window shows saying there is an error, but when i click show details, it dissappears. i can't open terminal as well (with ctrl alt T)
Maybe it just got corrupted? or we are not finished with the instructions above alone?

---

### Post by dmnur on 2020-04-03
Open a virtual console by pressing Ctrl+Alt+F3, log in there and type the following:
```
sudo apt update
sudo apt -f install
sudo apt upgrade
```

Then reboot (just press Ctrl+Alt+Delete). This should fix things.

Also, to prevent any issues when GRUB gets updated, it would be better to run this command:
```
sudo dpkg-reconfigure grub-pc
```

Just keep pressing Enter until you get to a list of devices. There select only /dev/sdb, unselecting everything else (press Space to select/unselect, Enter to confirm).

---

### Post by gnyav on 2020-04-03
i did those, but with no effect. 
it now boots in lubuntu, but only loads the wallpaper, i opened a virtual console and connected to wifi, then did the commands from above, but sill boots only with wallpaper.
maybe the lxqt doesn't start or something? 
i'm starting to think it would be better to just reinstall everything, but do it properly. but i'm not sure how to make the grub install successful during instalation

---

### Post by oldfred on 2020-04-03
With BIOS mode, you can use Something Else and the combo box at the bottom of the partitioning screen where you select or create the partition for ext4 & / (root) works. 
It normally default to sda. If sda is gpt, then it has to have a bios_grub for BIOS install or an ESP for UEFI install.

But if you just select sdb drive, then grub should install to sdb.

---

### Post by gnyav on 2020-04-04
Ok, I fixed it. 
Reinstalled it, and using gparted i switched the sdb table to gpt and created a partition that is "boot", "esp". and with the "something else" option chose to install it directly in sdb.


I guess technically both solution worked, but at the start the installation itself was bugged or something to not show the desktop environment properly.

---

