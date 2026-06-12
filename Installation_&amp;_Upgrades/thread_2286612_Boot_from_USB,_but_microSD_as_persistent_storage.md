---
title: "Boot from USB, but microSD as persistent storage?"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by TheZeusJuice on 2015-07-13
A little background: My laptop's (Asus Transformer T100TA) emmc drive died. Since it's soldered on and can't be replaced, I would like to run Ubuntu from a microSD card. The problem is that the machine's UEFI doesn't initialize the microSD reader, so it's not possible to boot from a microSD card (only boot option is USB storage).

Question: How would I go about making an Ubuntu installation that uses a USB stick as the boot medium and a microSD card as the persistent storage? My goal is that once the machine has booted I could use it without the USB stick attached (using suspend-to-ram and resume), at least until next time I have to reboot.

---

### Post by sudodus on 2015-07-13
You can create a partition with an ext2 ext3 or ext4 file system and the label **casper-rw** on the microSD card. I think it will be found automatically by a live Ubuntu flavour system (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu, ...).

It is also possible to make a full installed system in a fast USB 3 pendrive (which is faster also in a USB 2 port). See the following links (and links from them).

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Pendrive speed test](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)

[One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by TheZeusJuice on 2015-07-13
Thank you for the answer, it's half of the solution, but it doesn't fully resolve my question. Basically, what I want is to only have /boot on the USB stick, and have the rest of the Ubuntu installation on the microSD card. Such that I can remove the USB stick from the machine after it's done booting.

---

### Post by sudodus on 2015-07-13
I think a grub-n-iso system according to the link [One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682) works if you remove the pendrive after it has booted, if you use a ramdrive, the [boot option](https://help.ubuntu.com/community/BootOptions) **toram** and have the persistence in the microSD card.

You can also make an installed system with /boot on the USB stick and the root partition (and maybe a swap partition) on the microSD card. Select ***Something else*** at the partitioning window of the installer.

In this case there is a risk that you will wear the microSD card excessively. The situation is improved if you add the mount option **noatime** to the file **/etc/fstab** (in the line for the root partition). See ```
man fstab
```

You can also turn off journaling. See ```
man tune2fs
```

And finally you avoid swapping by keeping very few applications (or tabs) open at the same time. You notice swapping, it makes the computer very slow.

I think running a live system with persistence will wear less on the microSD card. Anyway, backup the system often, because the microSD card might wear faster than you think and stop working suddenly. See [this link](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by C.S.Cameron on 2015-07-13
If you want to use the SD for persistence, make a casper-rw or casper-rw + home-rw partitions on the microSD as Sudodus explained.
When making the flash drive, use Startup Disk Creator or UNetbootin to make an install with minimum persistence. 
When complete, delete the casper-rw file.
The flash drive will now use the first persistence file or partition it sees during boot.

Edit:
I gave suspend/unplug a try, with remote persistence partition, as you suggest, seems to work ok.
I think you need to start any programs you intend to use before suspending, once the flash is removed you can't open anything new.
This is cool, I have never thought of removing the boot drive before.

---

### Post by sudodus on 2015-07-14
A casper-rw partition is standard for persistence.  C.S.Cameron suggests casper-rw + home-rw partitions, and it is even better, particularly if you have plenty of space in the microSD card, because the home-rw partition will probably survive even if the casper-rw partition is damaged :-)

Using the boot option **toram** makes it possible to unmount the mounted partition(s) on the boot drive, and it can be removed. **toram** makes the system copy all of the content from the squashfs to RAM, so you need not start the programs before unplugging (but I would recommend unmounting before unplugging the boot drive).

If you haven't got enough RAM, there can be problems, otherwise it works very well. So if there is 1 GB RAM, the performance will improve significantly if you add 1 GB (or more if possible).

---

### Post by TheZeusJuice on 2015-07-14
Actually, I found a way to do this without **toram**:

1) I created a bootable Ubuntu USB stick.
2) I formatted the microSD card with a GPT partition table and 2 partitions: a small fat32 partition and a **casper-rw** partition (hmm, I guess next time I should do 3 and include a **home-rw** partition).
3) I created a new directory in the USB stick (I chose the name "initrd"), and copied into it the initrd.* and vmlinuz files from the "casper" directory.
4) I **moved** the "casper" directory from the USB stick to the fat32 partition of the microSD card (it's important that there no longer be a "casper" directory in the USB stick).
5) I edited "/boot/grub/grub.cfg" on the USB stick so that the Ubuntu entry targeted the new location for initrd.* and vmlinuz, as well as adding the **persistent** flag:

> linux /initrd/vmlinuz boot=casper persistent
initrd /initrd/initrd.img

So, what happens now is that the USB stick is used for booting (and initializes all the hardware, including the microSD card reader), but then the system starts looking for and finds the "/casper/filesystem.*" files and casper-rw partition on the microSD card, and uses them for the rest. So, once the system is booted, you can eject the USB stick despite not having used **toram**, because all the OS and app data is on the microSD (in the large squashfs file), not the USB stick.

---

### Post by sudodus on 2015-07-14
I'm glad you found a system configuration that works well for you. Congratulations :KS

Thanks for sharing your solution :-)

When you feel that your problem in the first post is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

Whenever you run into other problems you are welcome back with a new thread.

---

### Post by C.S.Cameron on 2015-07-16
It might be simpler to use a boot manager, (similar to Plop).
Plop can be installed on any bootable media an works similar to grub.

---

### Post by TheZeusJuice on 2015-07-16
That was my first thought as well. However, in my (admittedly unusual) case, the microSD reader in the Asus T100TA isn't functional until a kernel initializes it/loads the appropriate drivers. I tried to chainloading from grub, syslinux, and refind before I figured that out.

---

