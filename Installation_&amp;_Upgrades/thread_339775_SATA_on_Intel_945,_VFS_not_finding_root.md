---
title: "SATA on Intel 945, VFS not finding root"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by whistlingtony on 2007-01-16
Hi all!

I got my hands on a Core2Duo to play with. I got a Shuttle SD32G2 to throw mine in. I’m a linux nut, and wanted to run only linux. I had a devil of a time getting the BEEPing thing to boot. I’d install it fine using the Ubuntu 6.10 install disk, and then on the first boot it would hang at “Begin: Waiting for root file system... Alert! Not found.” It was annoying, especially as it managed to boot the LiveCD version just fine. FYI, the SD32G2 uses an Intel 945g chipset. Here’s what I've done so far.

In the BIOS, set the SATA to enhanced mode. This isn’t all that enhanced, it just allows the chip to read PATA drives (which is the fancy term for Parallel ATA, IE: old parallel cable). FYI, I disabled it thinking I was helping, then wondered why it wasn’t booting from my CDROM... Because it couldn’t find it any more. Sigh.

Do an install, you’ll have this problem. This is with Edgy Eft, I wonder how the next version would do?

I'm guessing it's just a driver problem, so I just grabbed the latest kernel source and ....

Boot from the LiveCD again.

Download the latest kernel from Kernel.org and stick it somewhere. I always make a spare partition on drives for moving or storing files in case of Voodoo. I put mine there.

make a temp directory (mkdir blah), move into it (cd blah), and then chroot into it (sudo chroot .). You are now inside your installed system. I mounted my spare partition, then copied the linux source to the /usr/src directory. I understand that is bad form these days. Tough. I then created a symlink to it (ln -s linux-2.6.19.2 linux).

Now, my newly installed system does not have GCC, MAKE, or Libncurses5-dev, all of which I need to configure and compile my new kernel. Sigh.... Gettum. (apt-get install gcc make libncurses5-dev)

Configure a new kernel:

    *
      (make mrproper)
    *
      (make menuconfig)
          o
            I selected the Pentium M as my chip. It seemed to work. There was no option for C2D.
          o
            compile the drivers for file systems and SATA/IDE, etc directly into the kernel. It’s just easier
          o
            Put in all the other good stuff too. Automatic kernel loading, network packet filtering, 802.11 options, your network cards, etc, etc, etc...
          o
            They choose the oddest defaults sometimes, don’t they?
    *
      (make bzImage)
    *
      (make modules && make modules_install)

Copy your new kernel to /boot (cp arch/i386/boot/bzImage /boot/whatevername-2.6.whateverrelease).

Now edit your Grub file and add in your new kernel as a bootable choice. (nano /boot/grub/menu.lst) Make a backup before you change anything!!!!!!!!!!!

Right... Now, notice I didn’t make an initrd image. As I understand it, we don’t need one because all of our file system and important hardware drivers are compiled right into the kernel.... Gulp. I hope.

Reboot and give her a whirl.

Curses! VFS: Cannot open root device “<NULL>” or unknown-block(8,1) Please append a correct “root=” boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)

Son of a Glitch! So, if I understand that correctly, the bloody thing can’t find my root partition? Hmm..... Lets take a gander at /etc/fstab.

Well... in my /etc/fstab file my / is commented out and there is a UUID=manymanyhexnumbers in it’s place. Err... I’m a bit behind, what is that crud? Right... Lets fiddle with this then.... MAKE BACKUPS!!!!

I deleted all that UUID stuff and made it look like I remember a fstab file looking like. Holy Beep, it worked!

reboot. Naturally, it doesn’t work again. WTH? 

Any help is greatly appreciated!

---

### Post by wackowillem on 2007-02-18
Did you get any further ? I am having fun with the same machine and same issue...

---

### Post by torbjok on 2007-03-04
I had to update the BIOS before I was able to install ubuntu 6.10.

Then I had to boot the install-cd with     acpi=off libata.noacpi=1

---

