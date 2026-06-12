---
title: "GRUB Malfunction (Can't boot anymore)"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by alex.de on 2007-08-04
I had 2 hard drives: Primary was Ubuntu 7.04 and secondary was Windows Vista. Now I formatted Windows Vista by using the Windows XP CD (I wanna go back to XP, since Vista can't run half on my things). After I formatted my Windows drive, GRUB won't boot.

If I plug in the Windows Hard Drive (waiting to be installed because it's a fresh copy of XP), it gives me all sorts of colored signs all over the screen.

If I plug only my Ubuntu Hard Drive, it stucks at "GRUB 1.5 Loading".

I had very important files on the Linux hard drive. I know I can just plug it in another computer but there's gigs and gigs of data.


Thanks. By the way, I'm typing this on my backup computer.

---

### Post by hamstersquasher on 2007-08-04
With only your ubuntu drive attached, you should boot to a linux live CD (like perhaps your ubuntu install disk - some let you 'test drive' ubuntu first before actually installing) open up a terminal window and at the prompt type **grub-install**.  this should reinstall the GRUB loader on the first sector of the drive.  then try to boot from the disk.  when GRUB loads hit the **c** key to bring up the command line editor for GRUB.  Try typing **configfile (hd0,0)/boot/grub/menu.lst**.  (hd,0,0) defines the first drive and the first partition.  this should get ubuntu booting again.  Finally, if all goes well, bring up another terminal window and type **grub-install**  one more time to write back to GRUB.

---

### Post by alex.de on 2007-08-04
Alright, I tried using the Super GRUB disk, but it's complicated and nothing works.

I'm typing this on the live cd right now but when I type in grub-install it prompts me to enter some attributes or whatever. I'm a beginner on Linux/Ubuntu and I need help on what to type exactly.


```

ubuntu@ubuntu:~$ grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```

Thanks.

---

### Post by hamstersquasher on 2007-08-04
It looks like **grub-install** is wanting you to specify the hard disk.  This will either by /dev/hda or /dev/sda.  you might want to try **grub-install /dev/hda** or **grub-install /dev/sda**.  When you write to a disk or other devices in linux, you do so by specifying a device file.  in the same way you can write to a regular file on your system, you can write to the device file /dev/fd0 for example to write to the floppy drive.

---

