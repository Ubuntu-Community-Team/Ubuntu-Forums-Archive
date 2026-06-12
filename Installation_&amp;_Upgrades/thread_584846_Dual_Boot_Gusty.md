---
title: "Dual Boot Gusty"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by petersra on 2007-10-21
Greetings

I have a Dell 8400 with a Nvida GeForce 7300 GT graphics card.  This system runs WINXP SP2.  I booted up the Gusty CD and then went through the install process using free space.  Everything went well till I tried to reboot.  It will only boot to WINXP not a dual boot menu.

I added NOACPI to the boot/grub/menu.lst file but no change in behavior.
I do notice that the pre-WINXP boot is different but nothing displayed for OS choice.

Advice?

Rob

---

### Post by Sef on 2007-10-21
Use the Live CD and open the terminal (Applications > Accessories > Terminal)

then type in this command:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by petersra on 2007-10-21
Disk /dev/hde: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69499212

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        2831    22739976    7  HPFS/NTFS
/dev/hde2   *        2832        4908    16683502+  83  Linux
/dev/hde3            4909        5005      779152+   5  Extended
/dev/hde5            4909        5005      779121   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf52bcf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19000   152561272+   7  HPFS/NTFS
/dev/sda3           19001       19457     3670852+  db  CP/M / CTOS / ...
ubuntu@ubuntu:~$

---

### Post by logos34 on 2007-10-21
Go into the BIOS at startup and change the hard disk boot order so that Disk /dev/hde: 41.1 GB is first.

anything?

And post your menu.lst

---

### Post by petersra on 2007-10-21
Here is the tail end of grub.lst

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=719af454-3a73-460b-9f60-e06bbfb6e380 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=719af454-3a73-460b-9f60-e06bbfb6e380 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Here is FSTAB
Disk /dev/hde: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69499212

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        2831    22739976    7  HPFS/NTFS
/dev/hde2   *        2832        4908    16683502+  83  Linux
/dev/hde3            4909        5005      779152+   5  Extended
/dev/hde5            4909        5005      779121   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf52bcf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19000   152561272+   7  HPFS/NTFS
/dev/sda3           19001       19457     3670852+  db  CP/M / CTOS / ...

---

### Post by petersra on 2007-10-21
BIOS does not allow anything other than a disk for booting not a partition

---

### Post by logos34 on 2007-10-21
right.  you change the boot disk in the bios and you should (hopefully) get grub, then you select ubuntu (on hde2) or windows (on sda2)

---

### Post by petersra on 2007-10-21
Thanks for the help.  I changed the boot order (was CDROM first and then HD) to HD first.  However, there was no change.  

There is some quick message flashing past during the boot process but I can't read it except for the cap letters ... PBR...

---

### Post by logos34 on 2007-10-21
> **petersra said:**
> Thanks for the help. ** I changed the boot order (was CDROM first and then HD) to HD first.  However, there was no change.  **

There is some quick message flashing past during the boot process but I can't read it except for the cap letters ... PBR...

You merely changed the device boot order.  You need to find the menu for the** hard disk** boot order .

---

### Post by petersra on 2007-10-21
I am sorry but I have looked through every menu in BIOS and there is nothing as you suggest.  The only boot control is the sequence, not anything deeper.

---

### Post by petersra on 2007-10-21
As I indicated earlier, there is a message that flashes by after the POST.  I finally got it "Loading PBR for Descriptor 2 ...Done".  This is a new message since installing Gusty.  So, am I to conclude that somehow the boot record has been trashed by the install and I am loading the backup.  If so, is there any recovery process to repair my boot record?

---

### Post by petersra on 2007-10-21
I found the problem.  I have two disks and somehow, Ubuntu was installed on the D drive, not the C drive.  This is really strange.  However, when I set the D drive to boot I get the boot menu and I can select Ubuntu or WINXP, which is booted off the C drive.

---

### Post by logos34 on 2007-10-22
> **petersra said:**
> I found the problem.  I have two disks and somehow, Ubuntu was installed on the D drive, not the C drive.  This is really strange.  However, when I set the D drive to boot I get the boot menu and I can select Ubuntu or WINXP, which is booted off the C drive.

That's why I suggested changing the hard disk boot order.  During installation Grub will be written by default to the MBR of the boot disk (hd0)--i.e. your sata drive sda--UNLESS there's an IDE disk in the mix, in which case it is detected first and grub is sent there instead.  In this case the IDE drive hde also happened to be where ubuntu installed, because you chose guided install using largest free space.  

Grub chainloads the windows bootloader, it doesn't boot it directly but rather hands off the boot sequence to NTLDR.  You'll notice the[ 'map' lines ]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")in the windows entry in menu.lst--this fools windows into thinking it's the BIOS boot disk and thus allows booting windows on a [non-first hard drive]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Go to 'thread tools' and mark it as' SOLVED.'

---

