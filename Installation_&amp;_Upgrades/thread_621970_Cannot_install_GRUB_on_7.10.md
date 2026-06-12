---
title: "Cannot install GRUB on 7.10"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by jcgp on 2007-11-24
I installed Fedora 8 on sda1, Mandriva 2008 on sda2, Suse 10.3 on sda3 (primary partitions), Ubuntu 7.10 on sda5  and sa6 is swap (logical partitions). A second SATA disk has one partition only.

Fedora, Manriva and Suse installed their own GRUB stuff, and after some copy and past text editing I managed to have all three booting fine.

Unfortunately I cannot convince Ubuntu 7.10 to install GRUB at all. The _boot directory exists but the _boot_grub directory does not. There is a kernel on the boot directory and a initrdxxx.bak, but when I try to boot from there, the kernel starts I belive (same fonts and general aspect going up as when going down) but then the process dies in the middle. I tried grub-install, the expert mode in the installation (from the 7.10 Live-Install DVD), I tried to install on a primary partition, always to no avail.

What am I doing wrong?
Carlos Pereira

---

### Post by meierfra on 2007-11-24
Are your sure that you do not have a grub folder.? Make sure that you mount your ubuntu partition and look for /boot/grub/ on the ubuntu partition

If you really do not have a grub folder, try this:

 chroot to the ubuntu partition. (Let me know if you need help with that)

 ```
sudo grub-install /dev/sda
```
This creates the grub folder and all the  stage files; and installs grub to the MBR.
Use /dev/sda5 if you want to install grub to the ubuntu partition rather than the MBR

```
sudo update-grub
```
This generates  "menu.lst"

If this did not work, report any error messages and post the output of "sudo fdisk -l"

---

### Post by jcgp on 2007-11-24
Initially there is no /boot/grub directory, so no menu.lst (or defult.grub with a symlink to menu.lst as Fedora does).
Actually there are three menu.lst on partitions sda1 (Fedora) sda2 (Mandriva) and sda3 (Suse, currently the bootable partition, so this is the only active meu.lst). But not on sda5, where Ubuntu is.

Commands:

chroot /
cd /boot
ls
abi-2.6.22-14-generic config... initrd...bak memtest... System... vmlinuz...generic

sudo grub-install /dev/sda5
Probing devices etc...
Searching for GRUB ... found /boot/grub
The file /boot/grub/stage1 not read correctly.

sudo update-grub
Searching for GRUB... found /boot/grub
Cannot determine root device. Assuming /dev/hda1 (???)
This error is probably caused by an invalid /etc/fstab (???)
Searching for default file... found /boot/grub/default
Testing for an existing GRUB menu.lst file...

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst ... for you? Yes!
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel:/boot/mmemtest86+.bin
Updating /boot/grub/menu.lst ... done

Now I have a normal Ubuntu menu.lst on /boot/grub/ I just copied the relevant lines to Suse menu. 

The first entry says:
root (hd0,0) (this is strange! it should say (hd0,4) I suppose?)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
(again /dev/hda1 looks strange because this is sda (SATA disk) and Ubuntu is at /dev/sda5 (moreover the only bootable partition is /dev/sda3 where is Suse, so this is the real GRUB /boot/grub/menu.lst that I really use, after coming from MBR (so is here that I am collecting the entries for the other 3 OSs,  Fedora Mandriva and Ubuntu).

Rebooting... Error 15: File not found
Reboot this time on Suse, to change menu.lst (hd0,0) to (hd0,4) and root=/dev/hda1 to root=/dev/sda5 for Ubuntu,
Rebooting again... Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block (0,0) ;-/

The active menu.lst (on dev/sda3) looks as this:

title Fedora 8
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.23.1-42.fc8 root=LABEL=/ ro rhgb quiet
    initrd /boot/initrd-2.6.23.1-42.fc8.img

title Mandriva 2008
    root (hd0,1)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_WDC_WD740ADFD-0_WD-WMANS1445342-part2 vga=788 BOOT_IMAGE=Mandriva_2008 resume=/dev/sda6 splash=silent
    initrd /boot/initrd.img

title OpenSuse 10.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_WDC_WD740ADFD-0_WD-WMANS1445342-part3 vga=0x314 resume=/dev/sda6 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

title Ubuntu 7.10
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro quiet splash

sudo fdisk -l :
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e866d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2196    17639338+  83  Linux
/dev/sda2            2197        4392    17639370   83  Linux
/dev/sda3   *        4393        6588    17639370   83  Linux
/dev/sda4            6589        9039    19687657+   5  Extended
/dev/sda5            6589        8784    17639338+  83  Linux
/dev/sda6            8785        9039     2048256   82  Linux swap / Solaris
    
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb937
    
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   83  Linux

Carlos

---

### Post by meierfra on 2007-11-24
> chroot /

This chroots to the root of the LiveCD. You need to chroot to the ubuntu partition 

```

sudo mkdir /media/sda5
sudo mount -t ext3  /dev/sda5 /media/sda5
sudo mount -t proc none /media/sda5/proc
sudo mount -o bind /dev /media/sda5/dev
sudo chroot /media/sda5
```

---

### Post by meierfra on 2007-11-24
I fixed one of the commands in the previous post.

---

### Post by meierfra on 2007-11-24
Did some testing and noticed that on my computer I also need to mount "proc" and "dev". I fixed my previous instructions accordingly. (Sorry I took my instruction from a different thread and hadn't tried them out myself)

---

### Post by jcgp on 2007-11-25
After chroot according to your instructions:
sudo grub-install /dev/sda5
error (block device not found or something like that)

Then I tried:
sudo update-grub
This produced the following (seems fine, at least the partition is correct and the vmlinuz kernel file exists):

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bde13d7d-aa5e-4d52-b61a-543f61f3133a ro quiet splash

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bde13d7d-aa5e-4d52-b61a-543f61f3133a ro single

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin

I added these three options to the oficial menu.lst (on /dev/sda3) and rebooted.

Unfortunately the first 2 options do not work. The third option works fine. The error message in both cases is:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I rebooted on Suse and commented the root=UUID=... part and again the same kernel panic message. Rebooted on Suse and commented the whole line. Rebooted on Ubuntu agin: Kernel panic.

I noticed that no initrd is given for Ubuntu, the other three OSs have one. Then I commented the initrd line for Suse and rebooted. Exactly the same message: Kernel panic - not syncing: VFS: Unable to mount root fs on uknown-block(0,0). Rebooting on Fedora to restore Suse. Rebooting fine again from Suse. So the problem could be the initrd line? why update-grub did not add one?

The fight is far from over!

Carlos

---

### Post by meierfra on 2007-11-25
Let's see whether you have the initrd files: Mount the ubuntu partition (sudo mkdir /media/sda5;    sudo mount -t ext3  /dev/sda5 /media/sda5) 

and list the content of the the boot folder on ubuntu:

```
 ls -l /media/sda5/boot 
```

---

### Post by jcgp on 2007-11-25
I prepared by hand an aditional line with the name of the initrd that was in the Ubuntu /boot/ on /dev/sda5, and added it to the oficial menu.lst on /dev/sda3 and this time Ubuntu booted fine!

Congratulations, it really looks great.

So the main problem was my lack of experience with Live-Install CDs.

Some questions:
1) According to linuxcd.org there are no Ubuntu install DVDs, only Live-Install DVDs, is this right?

2) when initially installing Ubuntu, he was unable to create a /boot/grub directory, although the right vmlinuz and initrd were on /boot (I tried this perhaps 15 times with slightly different combinations). Why? because he found 3 other Grubs on the system and got confused?
I was expecting Ubuntu to turn /dev/sda5 a bootable partition after changing MBR, but no... why? because it is a logical partition? I believe Linux can boot from logical partitions (unlinke Windows)...

3) After installing, Ubuntu was not supposed to mount automatically /dev/sda5? perhaps after a reboot?

4) After  mounting by hand and chroot correctly, the grub directory was installed, the menu.lst was created, pointing to the correct kernel file, but the initrd line was still missing. Why?

5) I could not find a way to manage boot managers from the Administration GUI. The same problem in Fedora (but not in Mandriva and Suse). Did i miss it (perhaps the Gnome minimalist default interface)? or is this an area where improvement is needed in future releases?

Thank you for your help!
Carlos

---

### Post by meierfra on 2007-11-25
Question 1)  Don't know.

Questions 2-4:  I'm just as puzzled as you are.

Question 5: Ubuntu does not come with a bootloader GUI. You can install "startupmanger", but it has limited abilities.

---

### Post by jcgp on 2007-11-25
Thanks a lot!
Carlos

---

