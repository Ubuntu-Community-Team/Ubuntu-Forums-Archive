---
title: "Grub not working? Ubuntu doesn't boot."
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by coolVariable on 2006-08-13
Please excuse my limited knowledge but despite being an absolute expert at MS OSs from DOS to Windows this is the first time I am trying out Linux.

Since I am trying to run Ubuntu on my laptop which has only limited harddrive space, I decided to install ubuntu to my external USB harddrive. 

The install went fine and completed correctly but when the computer restarted to boot into ubuntu, it stops after displaying "Grub _".
Nothing happens after that.

It seems to me as if the bootsector / bootprocess is not working properly?

(To clarify when booting the laptop I select boot USB HD to get to the above step. If I disconnect the HD and simply boot the internal HD it boot right away into WinXP - as I want it too.)

---

### Post by Cyhatch on 2006-08-13
(First try having the USB drive connected and "boot from normal HD" (the one with the boot sector?).)

Hm. If with no USB drive it boots into WinXP straight away, then I guess there is no GRUB thing in the bootsector. But since it does display "Grub _" with the USB drive plugged in, then there is.

Could it have happened that the the drive order is misidentified or something? Or GRUB wasn't properly installed?

Also, do you have an Ubuntu Live CD? If so, can you browse the USB drive?

---

### Post by Herman on 2006-08-13
[LEFT][SUCCESS - Breezy loaded on external USB drive !]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=re-install+GRUB")
Perhaps have a read from the link above here and compare that information with what you have and see if there is something more you need to do
         Regards, Herman . [/LEFT]

---

### Post by coolVariable on 2006-08-14
None of the other threads really helped me - but I am a newbie so I do not know.


Maybe it is a problem with the menu.lst file? I do not know.
Sounds to me like it is correct (and I was unable to change the file from the LiveCD boot anyhow).
At the same time, I don't even get to any menu ... it just says "GRUB _" in the upper left hand corner of the screen and doesn't do anything.


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.



title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by coolVariable on 2006-08-14
I just started GParted to get some more information:
I have two harddisks:
dev/hda - this is my internal HD with WinXP and I do not want to touch this. 
dev/sda - this is the external USB HD on which I would like to run Ubuntu:

dev/sda2    ext3        boot (this is where I installed ubuntu)
dev/sda1    extended    lba
  dev/sda6  linux swap  
  dev/sda5  ntfs
 unallocated

---

### Post by jimmygoon on 2006-08-14
Thats something where linux(/ubuntu) is lacking, and that is the ability to boot from a USB device... once it gets easier, I can't wait to try, but I'm not bold enough to try it yet because it requires a lot of work :eek:

---

### Post by raintheory on 2006-08-14
I have this exact same problem trying to boot Ubuntu from an external USB drive on my laptop...

Like you, I have tried every thread I could find but still can't get past the "GRUB _" on boot.

Using a Toshiba Satellite P15 S420 if that makes a difference.

---

### Post by coolVariable on 2006-08-14
I am using a Dell x300.

I absolutely love the way the LiveCD works and how Ubuntu looks and feels (using the LiveCD) BUT ...
... the whole partition thing is totally screwed up! Whoever programs the install routine should take a look at the Windows installation routine and how you can set up partitions/drives with it and take a few clues from that!


Very disappointing.

---

### Post by coolVariable on 2006-08-15
I tried the dual boot suggestion from this thread ([http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)) but it didn't work. 
It created the file (from the GRUB installation on my USB harddrive) and I copied it to C:\ and changed the boot.ini but when I select the option nothing happens blank, black screen.


Here is the full instructions:

How to dual boot Windows and linux without changing the Windows Master Boot Record:

(I'm assuming you've read other FAQs on how to install linux to your partition of choice. I recommend creating a partition on a second hard drive. That's the risk free option if you don't want to destoy Windows on your primary partition. But you should be able to create a partition on your primary hard drive by using software that can non-detructively resize your Windows partition. QTParted is a good program which can be downloaded if you're running the ubunut live CD. Back up though. It doesn't always work. I don't think the partition resizer in the ubuntu installer can do non-destructive.)

When installing ubuntu, install the boot loader (GRUB) to a floppy disk instead of the MBR. ie. when prompted for grub location enter: /dev/fd0

Boot into ubuntu with the floppy.

Open a terminal window.

Copy your bootloader from the floppy to a file called bootsect.lnx with this command:
dd if=/dev/fd0 of=bootsect.lnx bs=512 count=1

Save that file somewhere that you can access from within Windows. ie a FAT partition, a USB drive, a floppy (but not your boot floppy!) Don't try saving it to an NTFS Windows XP partition from within linux. (Bad!)

Reboot into Windows. (hint: take the floppy out of the drive. Keep it somewhere as a rescue boot floppy.)

Copy bootsect.lnx from wherever you had stored it to c:\bootsect.lnx

Open a file called c:\boot.ini
(It's normally a hidden read-only file, so you may have to change the folder and file options.)

After opening boot.ini add the following line to the end of it and save it:
c:\bootsect.lnx=”Linux”

Reboot your system.

You will be prompted to boot either Windows or Linux and your MBR hasn't been changed at all!

It's magic!
I use this setup to boot ubuntu from the third partition of my second hard drive. As ubuntu is on a second drive I haven't made any changes to my Windows partition at all! Risk free.

(If you do screw up your MBR and can't get into Windows try booting your Windows rescue CD and then type 'fdisk /mbr' to restore it. If you already have ubuntu installed I think you can make a boot floppy this way, but I"m not 100% certain: In a console, type grub-intall /dev/fd0.)

I apologize if to anyone who's already read this in the installation forum but someone suggested it would be more useful to post this here.

James.

---

### Post by coolVariable on 2006-08-16
Here is my disk setup:


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    32772599    16386268+   7  HPFS/NTFS
/dev/hda2        32772600    78140159    22683780    f  W95 Ext'd (LBA)
/dev/hda5        32772663    78140159    22683748+   7  HPFS/NTFS

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        10940265    58589054    23824395    f  W95 Ext'd (LBA)
/dev/sda2   *          63    10940264     5470101   83  Linux
/dev/sda5        11486538    58589054    23551258+   7  HPFS/NTFS
/dev/sda6        10940391    11486474      273042   82  Linux swap / Solaris

---

