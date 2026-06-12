---
title: "Grub does not boot USB disk and says only &quot;GRUB&quot;"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by vatikan on 2008-08-23
Hi everybody,

I had ubuntu installed with wubi. Now I migrated it to an external USB hard drive using lvpm. That worked fine. However, the external hard disk does not boot. 
When I start the computer (Sony vaio fe41z), the Bios finds the external hard disk and the Bios is also set to boot from external devices. After the Bios, the computer seems to try to boot from the usb drive, but all I get on the screen is: 

"GRUB"

Nothing else! No error, no loading nothing. Then nothing happens and only unplugging the device and rebooting helps as then the grub on the internal hard disk is loaded.

I tried to reinstall grub using several methods (grub shell, grub-install etc). However, nothing changed the boot sequence. If I would at least get an error message, I would be happy.
Does anyone have an idea what is wrong here?


One try was to change my device.map to:
(hd0)	/dev/sdg

However I am not sure if /dev/sdg is the right option, but on the current ubuntu installation, the usb drive is connected to this device.
I then installed grub using 
sudo grub-install --root-directory=/media/disk /dev/sdg
It processes the command without error.

When I do:
sudo grub-install --recheck /dev/sdg
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

After hours of googling, it seems that nobody knows what that error really is. 

Does anybody have an idea how I can get grub to talk to me? Or even get ubuntu to boot from the usb disk?

Thank you very much

---

### Post by fcollf on 2008-09-09
Hi,
I've the same problem.... Have you finally find a solution ??

Thanks!

---

### Post by c-yobrog on 2008-12-08
Got the same problem and no solution... Tryed with:

```
grub-install --re-check --root-directory=/mnt/chroot /dev/sdb
```

---

### Post by caljohnsmith on 2008-12-08
So is sdb your USB drive? How about posting the output of:
```
sudo fdisk -lu
sudo xxd -l 2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one.

---

### Post by vatikan on 2008-12-18
The output is:

sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44a01491

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205117919   102558928+  83  Linux
/dev/sda2       205117920   213616304     4249192+  82  Linux swap / Solaris
/dev/sda3       213616640   488394751   137389056    7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
eb48
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
00ff



The disks changed because I did that from the live cd.

---

### Post by logos34 on 2008-12-18
> **vatikan said:**
> The output is:

sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44a01491

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205117919   102558928+  83  Linux
/dev/sda2       205117920   213616304     4249192+  82  Linux swap / Solaris
/dev/sda3       213616640   488394751   137389056    7  HPFS/NTFS


The disks changed because I did that from the live cd.

Where's the other disk, or did you disconnect it?

I think you may need to edit grub:

sudo mkdir /media/sda1

sudo mount -t ext3 /dev/sda1 /media/sda1

gksudo gedit /media/sda1/boot/grub/menu.lst

Post the contents of menu.lst.  I'm guessing LVPM may have gotten the 'root' line wrong during the transfer and installing grub

---

### Post by vatikan on 2008-12-19
No the disk letters are based on my current configuration, that I boot the live CD in virtual box and connect the usb drive to the virtual box. In that way, the usb drive is the only physical drive in virtual box. 
When I boot  the real computer from USB, there is one other disk. 

All uncommented lines in  menu.lst are:


color green/blue black/red
default 0
timeout 5

title Ubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=663bfd56-adc6-4dd9-b3ce-5095f163f4f9
initrd /boot/initrd.img-2.6.24-19-generic

#kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=663bfd56-adc6-4dd9-b3ce-5095f163f4f9  ro quiet splash acpi=off noapic nolapic


The UUID is correct. I checked that.

---

### Post by logos34 on 2008-12-19
> **vatikan said:**
> When I boot  the real computer from USB, there is one other disk. 

Even if there's another hard disk or drive connected, the fact that the USB disk is the Bios boot drive means it's the first one.  So change this

> title Ubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=663bfd56-adc6-4dd9-b3ce-5095f163f4f9
initrd /boot/initrd.img-2.6.24-19-generic

to this

> title Ubuntu
root (hd**[COLOR="Red"]0[/COLOR]**,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=663bfd56-adc6-4dd9-b3ce-5095f163f4f9
initrd /boot/initrd.img-2.6.24-19-generic

---

### Post by vatikan on 2008-12-19
I changed it as you said and reinstalled grub using the shell
root (hd0,0)
setup (hd0)
It installs without errors
however, a reboot of the real computer shows the same result as always
"GRUB" and that was it.

---

### Post by logos34 on 2008-12-19
what does 
> 
sudo grub

grub> find /boot/grub/stage1

show?

---

### Post by vatikan on 2008-12-19
I just followed the same approach as the sample output on one of the links in your signature showed another output than I get.
In fact my output shows only an error:

grub> find /media/disk/boot/grub/stage1

Error 15: File not found

Grub was executed with "sudo grub". However, the file is there:

ubuntu@ubuntu:~$ ls /media/disk/boot/grub
boot           fat_stage1_5       menu.lst-backup    stage2
default        installed-version  menu.lst_original  stage2_eltorito
device.map     jfs_stage1_5       minix_stage1_5     xfs_stage1_5
device.map~    menu.lst           reiserfs_stage1_5
e2fs_stage1_5  menu.lst~          stage1

---

### Post by caljohnsmith on 2008-12-19
How about installing Grub without its stage1.5 file to see if that makes a difference in Grub's behavior for your setup:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
And please post the output of the above commands. The above commands install Grub to the MBR of sda but omit the stage1.5 file so that Grub points directly to the sector location of the stage2 file. In my experience helping others with weird Grub behavior problems, using the above technique sometimes works; how about giving that a shot and let us know the results.

---

### Post by vatikan on 2008-12-19
Well it doesnt install

<ub/stage2 p /media/disk/boot/grub/menu.lst

Error 15: File not found

I am asking myself why the find command and your command say that there is a file missing even though it's there

---

### Post by vatikan on 2008-12-19
Ok my bad
When I set the root to (hd0,0), it uses the disk as root.

grub> find /boot/grub/stage1
 (hd0,0)

grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst

grub> 

No output

---

